---
title: "Libvirt/KVM/Qemu and networking between host/guest"
date: 2018-08-08
forum: Networking &amp; Wireless
---

### Post by Roasted on 2018-08-08
Hello friends. I was recently looking into virtualizing some of my home items in an effort to compartmentalize some of my services. To test, I fired everything up on my desktop first. With all of my initial testing, things seemed great and I very much liked using KVM with virt-manager. Out of necessity for an unrelated problem, I redid my home server, opting for Ubuntu Mate 18.04 as the base OS and built out a few Ubuntu Server VMs on top of it.

Overall, things work great and I quite like this setup. The only thing is I can't seem to figure out the networking piece in between the the server underneath and the VMs on top. Due to macvtap, it seems like they are unable to connect. Admittedly I even get a notice about this in the VM settings after selecting macvtap bridge as the network type.

The problem with this is in both scenarios (my desktop where I am frequently testing VMs and my home server which will host a few permanent VMs) I need to be able to communicate between host and guest OS. In the case of my desktop I often have the need to transfer files to/from the systems. Likewise, in the case of my server, I would like to back up some configurations (such as tar'ing /etc nightly and rsyncing it to the host OS for safe keeping). All the while I want my guest OS's and host OS to maintain regular LAN IPs from the main scope of my router.

I did my usual digging online, but a lot of the approaches seem to be either questionable due to their age (2006 documentation causes me to raise an eyebrow), or the suggestions come across as rather hacky. Perhaps I'm being a bit forward with my judgment, but given how approachable KVM seems and how easy to use virt-manager is for GUI setups, it created some pause to see an assortment of suggestions involving a massive amount of scripts and startup jobs and whatnot to reconfigure networks on bootup to accept guest-vs-host communication.

Is there a more approachable way to enable host and guest OS's to communicate? Something else I considered was adding a second NIC in a NAT. For example, say my main LAN is 10.52.x.x, and the host OS is 10.52.0.100 and all guest VMs on that host are 10.52.0.101 thru 110. That's perfect for regular use and setup, but perhaps a second NAT NIC in a 192 network (say host is 192.168.1.100 and guests are 192.168.1.101 thru 110) where the guest OS's can communicate over the 192 network back to the host OS, I'd be fine with that too. End goal is for everything to be on a 10.52 network first and foremost. If I have to adjust rsync jobs and whatnot to run over a 192 network, that'd be fine. Catch is I'm not sure if this is the go-to method for this (and likewise, so far in my testing, I haven't been able to make a NAT'd NIC work as I was hoping for with my above description).

Anyway, might anybody here have any ideas or suggestions? Would greatly appreciate any and all insight. Thanks much!

---

### Post by TheFu on 2018-08-08
Setup standard Linux bridges, manually, on the hostOS.  Then when you setup the guestOSes, use that bridge as the device.  If any of the VMs are internet accessible, it is best to NOT use the same NIC on the hostOS that is used inside a VM.  

Ah - you are running 18.04.  Sorry, can't help there.  They changed all the networking from ifupdown to netplan and I think bridges got broken.  I've seen a few threads in these forums about 18.04 bridges.  I don't think any GUI will get you want you want. I've always manually setup bridges in the interfaces file the last 8+ yrs.  The libvirt bridges always seemed to have performance problems. Userland vs kernel-land networking.  Stay with kernel-land for stability and performance.  I've never used macvtap.

If you run 16.04, I can tell you exactly what to do. I like my VM hosts to be extremely stable.  My primary VM host is on 14.04 still.

---

### Post by Roasted on 2018-08-08
Well if we look at this from a xenial standpoint perhaps I can leverage the insight and adapt it to bionic. To confirm you're suggesting I set up multiple bridges within the base os, then assign each bridge (one per) to each guest, correct? 

Perhaps another consideration would be to just get a 4 port network card. If I went that route would it be trivial to assign one port of the card per one virtual machine? I had considered looking into that already but the workload of the guests will be so light I didn't pursue it too heavily. 

If you would be able to share 16.04 insight I believe I can still find that very helpful and move forward with my current setup. Would appreciate any insight. Thanks again!

---

### Post by TheFu on 2018-08-08
Sharing a bridge with the hostOS is a security problem. That's all.  Bridging can allow access to all the traffic on that NIC to any OSes connected.  It would be bad if the hostOS were connected to an internet-facing service running in a VM using the same bridge.

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

---

### Post by Roasted on 2018-08-08
Hmm, makes me wonder if the macvtap bridge approach presents the same security concerns as a traditional bridge does. May have to dig into this more to see. Thanks for your 2c.

---

### Post by Roasted on 2018-08-08
Hm, so something I'm experimenting with at the moment seems to be giving me the behavior I was looking for. Basically I left the main NIC on the guest OS as macvtap bridge. I created a 2nd NIC and set it up to be a NAT instead of a macvtap bridge. Host OS starts at 192.168.122.1 for the IP with a DHCP range of 192.168.122.2-254. This gave me an idea. I just went into the guest OS and set up the ens8 interface (which was added to the guest OS after I added the 2nd NAT'd NIC) to be a static IP at 192.168.122.2. From the guest OS, I can ssh into 192.168.122.1 (host OS).

So this has me wondering. Maybe what I'll do is experiment with setting up a 2nd NIC on each guest OS and set that NIC to be NAT. From there, set it to have a static IP, where the last octet matches the static IP I gave the guest OS for the main VM. i.e. if the macvtap (main) NIC is 10.52.0.5, the NAT (second) NIC is 192.168.122.5. Then I can build out my bash/backup/rsync scripts to target the 192.168.122.1 address of the host OS in an effort to sling over raw configs to the main box**.

** the main box has a 6 TB array running and it's where I like to keep raw backups. I know I can snapshot VMs (and I will) but having something separate to a VM snapshot is another layer I'd like to aim for.

So overall I'm basically tying in two NICs per VM, where each NIC has its own set of "duties". One does everything except one specific task, and the other NIC can accommodate that one specific task.

Of course I'm all ears if there's something not-good about this approach, but from what I'm seeing this may be the most approachable way to handle what I'm after.

---

