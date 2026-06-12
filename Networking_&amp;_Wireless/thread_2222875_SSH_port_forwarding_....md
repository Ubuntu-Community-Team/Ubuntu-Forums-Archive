---
title: "SSH port forwarding ..."
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by redrumrogue on 2014-05-08
Hi folks,

I hope this falls under this catagory.

I have three machines - laptop (software license server), PC (openssh server & VM host), VM (running on the PC).

I want to run some software on the VM which will need to get a license from the laptop.  The VM is using a NAT network configuration, and I'd like to try and keep it that way.  The PC is in my home network at address 192.168.1.2 and the VMs NAT address is 192.168.122.10.  The license server is mobile and can ssh to the PC from anywhere.  The VM needs to request a license using port 1515 and the license server replies using port 1516.  I'm pretty sure I've opened all necessary ports on all the machines firewalls.  So I would like to use ssh port forwarding, initiated from the laptop (lic server), to open the lines of comms for the license request to work.  This is what I've tried already with no success ...

On the laptop (using putty)...
equivalent command line would be **ssh -p 1234 **[B]user@PC -R 151501:laptop:1515 -L 1516:192.168.1.2:151601
[/B]Once logged i run **ssh -p 1234 ****user@VM  ****-R 1515:192.168.1.2:151501 -L **[B]151601:192.168.122.10:1516
[/B]
So i'm trying to hop from the laptop to the PC then to the VM and visa versa.  Unfortunately this does not work.  The VM cannot see the license server and the license request times out.  I think I must be going wrong with my ssh tunnels.

Can anybody show me the way?  I don't want to put the VM on a bridge network if I can help it.

Thanks
JB

---

### Post by TheFu on 2014-05-08
Which license software is being used?  Some may have restrictions on the subnet allowed ... and only work over UDP.
BTW, I've written code to leverage commercial SW license tools a few times.

---

### Post by redrumrogue on 2014-05-09
Thanks for your reply.  The license software is IBM LUM 4.6.8.15 (License Use Management).  This is installed on my laptop as a network license server, and it has to be installed on the VM and configured as a network license client.  I've had this installed and working correctly on another VM where I was using bridged networking.  So I'm fairly sure it's just an issue with how to use ssh tunnelling to open the right lines of comms for the LUM client to talk to the LUM server.

---

### Post by TheFu on 2014-05-09
I've only worked with ElanLM and FlexLM - these used a mix of tcp and udp connections. The manuals for the other LM software was fairly explicit about which ports and which protocols had to be available. Is it possible to tunnel udp over ssh?  Looks like the answer is yes.

Ok ... moving on.

All my machines are limited to 64K ports. Does yours support 151,601 ports or am I reading the command incorrectly?
Are you certain that putty supports the mode requested? I haven't used putty in .... er ... 9 yrs.

---

### Post by redrumrogue on 2014-05-09
Blimey ... I did actually try to use port 151601 didn't I ... but I've also tried using ports under 64k with no success.  No i'm not certain of what Putty supports really.  Is Putty even still considered a good solution these days, or is there somthing much better out there?  I've been using Putty for about 2 years now but only to connect my laptop (windows 7) to my machine at home (ubuntu 14.04)  and port forward between the two.  This multi-hop business involving VMs is hurting my head!

---

### Post by TheFu on 2014-05-09
> **redrumrogue said:**
> Blimey ... I did actually try to use port 151601 didn't I ... but I've also tried using port under 64k with no success.  No i'm certain of what Putty supports really.  Is Putty even still considered a good solution these days, or is there somthing much better out there?  I've been using Putty for about 2 years now but only to connect my laptop to my machine at home and port forward between the two.  This multi-hop business involving VMs is hurting my head!

If bridge mode works, I'd just use that.
Haven't used putty 'cause I stopped using Windows. Yes, there is a better solution, Linux.  Also, you may want to read up on the ~/.ssh/config file. It can simplify your life across all ssh connections. Don't know if putty supports that or not.

If you like pain, ... then perhaps using bridge mode with a verbose firewall with only ssh open will help to determine exactly which ports/protocols are required? Sometimes LMs use subnet broadcasts - which will not be forwarded through an ssh tunnel.  

Anyway, hope that provides a way to troubleshoot this further.

---

### Post by redrumrogue on 2014-05-09
Thank you very much for your time.  Sadly the software I'm running on the laptop and on the VM (CATIA V5) only runs on Windows.  I love linux and would use it for eveything if I could!  The reason I'm avoiding bridge mode for the VM networking is because I'm trying to run the VM with KVM/QEMU on my ubuntu box.  I've been using VMWare and VirtualBox for a while now and know those well, but I'm new to KVM and I've not learned how to create the bridge network with that yet.  I thought I'd see if I could just use SSH tunnels as I'm more familair with SSH (but obviously not familiar enough!).

---

### Post by TheFu on 2014-05-09
Ah ... bridging on Linux.
a) KVM is a much better solution for server-on-server VMs and VMware-whatever (they make 6 different products) or virtualbox. Excellent choice.
b) KVM built-in networking ... er ... sucks. 
c) Setting up Linux bridging happens outside the libvirt/KVM environment - at least for the most stable bridges.  You will need to manually modify the bridge to be used inside each VM machine.

So ... you are in luck. I gave a presentation on simple KVM installation and configuration last month at 2 LUGs.  Here's the preso: [http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html](http://blog.jdpfu.com/ALE/ALE-NW/2014_04-virtualization.html)   Pgs 13 - 15 are what you want.

---

### Post by redrumrogue on 2014-05-09
Excellent stuff, thank you.  I'll read through that when I have a mo and let you know how I get on.  I'm going to be running some finite element analysis jobs on the VM, which is going to be very intensive for the CPU so I'm interested in seeing how KVM will perform vs Virtualbox on the same host machine.  I' hoping to get better performance from KVM.  I'm still keen to see if I can get the lic server / client conversation going through SSH tunnelling but I'll persue bridging the VM as well as I'm sure it'll all be easier once that's setup properly.  Again, thanks for your time.

---

### Post by TheFu on 2014-05-09
From what I've read, heavy CPU tasks are poor choices for  any VM environment. VMs need to share resources, not eat 100% of anything. OTOH, if you have a 12-core server .... Be certain to leave 1 core for the hostOS, otherwise, things get slow.  I've lost my presentation on "Performance Tuning VMs" - sorry.  However, this: [http://blog.jdpfu.com/slowVbox](http://blog.jdpfu.com/slowVbox) might help from a high level.

Linux bridging is really easy. 5 minutes to setup and it kinda "just works".
I've even setup bridges that the hostOS doesn't use at all, on different networks for 1 client OS - a firewall/gateway VM. Using it for testing, I'd never run a production firewall on a VM.

---

### Post by redrumrogue on 2014-05-09
The reason I started looking into this is that I have the FEA software on my laptop and could run the computation there but I have a much more powerful desktop PC at home running ubuntu and I'd like to put it to work crunching numbers.  It has an AMD FX 8350 8 core 4GHz processor, which beats my laptop. I've already proven that running the FEA job on a Virtualbox VM on the ubuntu machine is quite a bit faster than running it on the laptop, but I'm hoping to squeeze more performance out using KVM.  Do you think I'd see much difference?  Is KVM much more efficient with CPU usage than Virtualbox?  Sorry - this thread is moving into virtualization territory ...

---

### Post by TheFu on 2014-05-09
I don't know. Every workload is unique.
Virtualbox is NOT optimized for server workloads.
KVM is.
KVM is NOT primarily designed to be used for desktop VMs, but that it improving.
So, if you turn down the "GUI cheese", KVM should perform better than Virtualbox.

This is just my gut feeling. I have no data to back it up.

Might be worth asking this specific question in the virtualization sub-forum. There are some smart folks there.

---

### Post by redrumrogue on 2014-05-12
Sorted ... I believe the license server software on the VM won't work over SSH tunnel.  I've used a different license server instead and it works. Also managed to setup bridge networking for the VM ... setting that up wasn't how I expected it to work but it's doing what I expect it to do.

---

