---
title: "Ethernet connection stopped working in Ubuntu 20.04"
date: 2020-08-23
forum: Networking &amp; Wireless
---

### Post by nico16 on 2020-08-23
Hi, 

I installed Ubuntu 20.04 on a brand new Dell Latitude 5500 about 10 days ago. My ethernet conection has been working fine for one week but then it has not been working at all for the last 3 days. Network settings just say "Cable unplugged". 

ifconfig command shows this: [https://paste.ubuntu.com/p/STB2GZS8Vm/](https://paste.ubuntu.com/p/STB2GZS8Vm/)
```
eno2: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500        ether c0:3e:ba:47:32:4a  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0x91300000-91320000
```

sudo lshw -C network command shows this: [https://paste.ubuntu.com/p/fXmW2VcKMF/](https://paste.ubuntu.com/p/fXmW2VcKMF/)
```
*-network:1
       description: Ethernet interface
       product: Ethernet Connection (6) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno2
       version: 30
       serial: c0:3e:ba:47:32:4a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.2.6-k firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:127 memory:91300000-9131ffff
```

Is anything wrong in these outputs ? My understanding of these is limited so any help would be appreciated.

When I start Ubuntu live from a USB stick, same I cannot connect via the ethernet cable, although it worked fine when I installed Ubuntu on the machine. 

Nothing wrong with the cable as it works on another laptop running with Windows.

Could it be a hardware problem ? A driver issue ? Network manager ??

Thanks a lot for your help, this is frustrating...

---

### Post by TheFu on 2020-08-23
The I219-V is a 2.5Gbps adapter that Intel has started pushing.  The driver used above appears to be making an autonegotiated 1 Gbps connection with the switch, so that's a good sign.

A few other people here have struggled with this adapter on their new B550 and X570 Ryzen systems.  Both decided to buy a $25 Intel PRO/1000 NIC after fighting for a few weeks and failing to resolve the problem.  Perhaps in a few more months, support from Intel will work?
[https://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop](https://unix.stackexchange.com/questions/294753/intel-ethernet-connection-i219-v-not-working-under-linux-on-an-asuspro-b-laptop) has a few answers.  The 2 prior people here weren't able to get it working following those instructions.

I am an Intel NIC lover.  Go out of my way to get Intel NICs for a number of reasons. It is just in this situation, whatever is happening between Ubuntu and Intel ain't working.

I don't use network-manager for anything. Early versions of it had some major issues, so I've never trusted it.  The ifconfig output shows your NIC doesn't have any network configuration parameters - like - IP, netmask, gateway, or DNS specified. Those are all required for a working system.  DHCP often provides it, but on a server it is common to set them manually.

I think the issue is a driver issue. [https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-?product=71307](https://downloadcenter.intel.com/download/15817/Intel-Network-Adapter-Driver-for-PCI-E-Gigabit-Network-Connections-under-Linux-?product=71307)  has v3.8.4. You have v3.2.6 of the driver.  I'd try using the newest driver, if I were in your place.

---

### Post by nico16 on 2020-08-23
Hi, 

Thanks a lot for your reply and advice. I updated the driver to the latest version but sadly it didn't make a difference, ethernet connection is still not detected.

  ```
*-network:1
       description: Ethernet interface
       product: Ethernet Connection (6) I219-V
       vendor: Intel Corporation
       physical id: 1f.6
       bus info: pci@0000:00:1f.6
       logical name: eno2
       version: 30
       serial: c0:3e:ba:47:32:4a
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=3.8.4-NAPI firmware=0.5-4 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:126 memory:91300000-9131ffff

```
Why would it work for one week then stop working ? I could understand if it did not work straight from the box but here I don't know. 

I'm not sure if the output of dmesg | grep e1000e would help but here it is in case:
[https://paste.ubuntu.com/p/gff9s6Y7Xj/](https://paste.ubuntu.com/p/gff9s6Y7Xj/)

I am not quite sure what my options are now ? 

Thanks for the help.

---

### Post by TheFu on 2020-08-23
Have you tried forcing gbps connections and disabling autonegotiation?
What about manually setting the network configs - IP, netmask, gateway and dns?

This assumes your already swapped the port to the switch and cable.

---

### Post by nico16 on 2020-08-24
Thanks a lot for your reply. 

I should be able to try manually setting the network configs.

But I don't know how to disable autonegotiate or force gbps connections.

Also don't know how to swap the port to switch and cable sorry.

Any help on these would be much appreciated. Could you also explain why these would help ? 

I'm happy to try these but just for the record I find it frustrating that I seem to be having a hardware compatibility issue as this laptop is supposed to be ubuntu certified: [https://certification.ubuntu.com/hardware/201902-26858](https://certification.ubuntu.com/hardware/201902-26858)
 
Thanks a lot.

---

### Post by TheFu on 2020-08-24
I haven't needed to disable autonegotiation in about 15 yrs. It is part of the Gbps ethernet standard.

The tool we used to control those settings was **ethtool**, assuming the options for the driver can't be used with **modprobe**. You'd need to look up how to pass options to that specific driver. Sometimes a driver will read a specific config file located in a specific directory with a specific name.  
Why?  You have a NIC that is capable of 2.5Gbps, but it is highly unlikely you have a switch with that capability. Perhaps something in the autonegotiation for the connection speed isn't working quite right.  Before we all had 1 Gbps NICs, autonegotiation was a problem and if we had a Gbps NIC, but only 10/100 base-tx switch, autonegotiation often failed. We'd have to force the NIC to use 100 base-tx. Doing that made the connection very stable. Perhaps that will work the same way now?

Swapping the switch port used is a physical connection thing.  Unplug the CAT5e/CAT6 ethernet cable from the switch port and move it to a different port. 
Why?  The port may have gone bad on the switch. Ports fail seldom, but it isn't THAT odd.  I've had complete switches fail after 5 yrs of use.  I've had motherboard NICs not completely fail, but just send lots and lots of corrupted packets.  The solution for the first was to get a new switch. The solution for the 2nd was to disable the onboard NIC and install a very cheap PCIe GigE NIC I had laying around. I really should replace that $10 Marvell in 2006 NIC (less than 300 Mbps throughput) for a $25 Intel PRO/1000 NIC (920 Mbps throughput). Actually, I have a 4-port Intel PRO/1000 here somewhere.

Manually setting the network parameters removes the DHCP server (where ever that is) from this problem. In solving any problem, simplify and test until you get down to the 1 thing that is causing the problem. Then fix that 1 thing.  In a complex system like an ethernet connection using dhcp, autonegotiation, and a switch or router, there are some things which don't cost any money that can be checked. Manual network connection setup is free to try and for a server or a desktop that doesn't move, it is how I setup those systems. No DHCP used.

Also, please realize that nobody here works for Canonical. Everyone, even the moderators, are volunteers.  I bet if you read the fine print for the certification, it says at the time of the testing, everything worked with the OS they tested, nothing more.  But we don't have the equipment you have. I've just noticed that other posters here have issues with the Intel i219-V NICs and that they were unable to solve those problems.  I have a slight personal interest because I'm in the market for a new Ryzen motherboard and the next generation happens to have this same 2.5Gbps NIC on the board (B550). Because of these issues, if I can't wait for a 100% reliable fix to be available, I'll probably buy a B450 with an i211 NIC instead.  Life it too short to deal with stupid driver problems, IMHO.

Feel free to let Dell know about your frustration. Often, if the laptop was shipped with Ubuntu and the correct driver, then they will have an updated driver on their support site.  Perhaps the system came with a Dell PPA configured to ensure driver updates were automatic.  Of course, if you've upgraded from 18.04 --> 20.04, then it isn't the same, supported, computer, anymore.

I like Dell laptops. I would never touch/buy/own a Dell desktop for personal use. 3 Dell laptops are in arms length of me right now. I think, on average, they make the most compatible laptops with Linux today that aren't System76 (way overpriced to me, but a value for many others).  One of those Dell laptops has been running almost non-stop since 2011.

Anyways, hope those explanations are helpful.

Simplify and test. Keep doing that until the only thing left cannot be simplified any more and you've proven through elimination that is where the problem lies.

---

### Post by nico16 on 2020-08-30
Thanks a lot for your advice and apologies for the slow reply. Thanks also for explaining what each of your suggestions meant and why they were good options to try. That was very helpful. For people like me who aren't that savvy it's good to understand what is the intention behind a specific procedure. 

I was about to change some of the connections settings with ethtool when I decided to double check cables and switch ports. That's when I realised it was after all... a cable issue ! That same cable works fine on another computer (running Windows although it probably doesn't matter) so I assumed it couldn't be the problem but there you go. Thanks for suggesting to check the basics again...

I'm relieved and happy that my Dell laptop seems to have really good compatibility with Ubuntu after all. I wasn't having a go at anyone, especially not on here, when I pointed out earlier about possible compatibility issues. I was just venting my frustration about the fact it's difficult to find affordable laptops that are Ubuntu-compatible (agree that the System76 seem overpriced, especially if you try to get them from the UK), so if the ones that are meant to be compatible are not it would make things really difficult. But I take your point about fine prints and the fact that there are no guarantees in the long run. 

In any case, problem solved, ethernet connection works fine with a new cable. Compatibility seems fine for now. Thanks a lot for your help, much appreciated.

---

### Post by TheFu on 2020-08-30
We've all been where you are. An outside person sees what's right in front of my face almost daily. Can't say how many times I've been writing up an issue to get help here over and realized I hadn't do my basic testing.  The act of proving what I believed by running commands to include in the post usually shows the flaw in my process.  So I don't post the question.

Cable issue.  Good to know.  Probably about 1 in 10 times for issues like this, it is the cable or switch.

Please mark this thread as "SOLVED" using the thread tools button near the top. This helps both people wanting to help others and especially people seeking answers.

I'm happy to learn the i219-v NIC isn't the issue, at least for you, on this Dell laptop. For the next person:```

       product: Ethernet Connection (6) **I219-V**
       vendor: Intel Corporation
       capacity: **1Gbit/s**
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=**e1000e** driverversion=**3.2.6-k** firmware=0.5-4 latency 
```

---

