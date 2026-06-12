---
title: "[Ubuntu] Network not working on 16.04.2 - RESOLVED"
date: 2017-03-08
forum: Networking &amp; Wireless
---

### Post by grancois on 2017-03-08
Hi,

a few weeks ago, I set-up a virtual Ubuntu server (16.04.2 LTS) running on a physical Windows Server 2008 R2 machine trough [Hyper-V]("https://en.wikipedia.org/wiki/Hyper-V"). I got an Apache2 web server working, and for a few days, everything was fine. Please note that I did never change anything in the server original network's configuration. 

This morning, unexpectedly, I couldn't access the web pages hosted on this Ubuntu server. After a short investigation, I realized that I can not contact the server from any machine, and it can't contact any machine from the server either, even on the local network. I can't apt-get update, upgrade or install anymore, as the server is unable to contact the packages repository.  

As the server IP is dynamic by default, I changed it for a static IP, hoping this would resolve the problem, but that didn't work. I have searched for several hours, trying a lot of solutions, but I can't get the network to work.

Here are all the informations I can think of as relevant. Does anyone as an idea of what the problem might be? Would you need more informations to track the problem?

[B]/etc/network/interfaces
[/B][IMG]http://tof.canardpc.com/view/ae82e8a8-4463-48d9-811d-11abc895e355.jpg[/IMG]

[B]/etc/resolv.conf
[/B][IMG]http://tof.canardpc.com/view/a72426d3-b8ac-4ec5-96b9-f02d559358e8.jpg[/IMG][B]

ifconfig -a
[/B][IMG]http://tof.canardpc.com/view/7facb511-1379-4ad5-8827-ccce7676ceee.jpg[/IMG]

[B]sudo apt-get update
[/B][IMG]http://tof.canardpc.com/view/9f7b777f-2f24-479c-83bb-5667c46cd999.jpg[/IMG]

Thank you for your time and help!

---

### Post by TheFu on 2017-03-08
Can you ping the router by IP?
Can you ping your DNS servers by IP?

Also, I'd remove the "network" line in the interfaces file. That isn't necessary.
BTW, are you certain the ethernet device is eth0?   Systemd usually names devices using a new scheme.
**sudo lshw -C network** will show all the network devices.

---

### Post by grancois on 2017-03-09
Hi TheFu, thank your for your answer!

> **TheFu said:**
> Can you ping the router by IP?
Can you ping your DNS servers by IP?

No, I can't ping neither the router nor the DNS servers. I always get the same answer : **Destination Host Unreachable**

> **TheFu said:**
> Also, I'd remove the "network" line in the interfaces file. That isn't necessary.
Done.

> **TheFu said:**
> 
BTW, are you certain the ethernet device is eth0?   Systemd usually names devices using a new scheme.
**sudo lshw -C network** will show all the network devices.
Here is the result of the command
[IMG]http://tof.canardpc.com/view/ffbbcff5-c6e9-4cae-820b-3464dc70ead2.jpg[/IMG]

---

### Post by TheFu on 2017-03-09
Please copy/paste text, not images. This is kind to bandwidth limited people. Sorta chicken-egg problem when there isn't any networking so ssh isn't possible. Ouch.

For hypervisors, I use virtio network drivers.  The hv-netvsc driver is unfamiliar to me.  I'd start looking into that if you can't change to virtio due to a hyper-v limitation.  Sorry, never seen, touched, hyper-v here.

---

### Post by grancois on 2017-03-09
> **TheFu said:**
> Please copy/paste text, not images. This is kind to bandwidth limited people.
Sure, got it.


> **TheFu said:**
> Sorta chicken-egg problem when there isn't any networking so ssh isn't possible. Ouch.

For hypervisors, I use virtio network drivers.  The hv-netvsc driver is unfamiliar to me.  I'd start looking into that if you can't change to virtio due to a hyper-v limitation.  Sorry, never seen, touched, hyper-v here.
Ok. Thank you for your help.

---

### Post by TheFu on 2017-03-09
So, did a little searching and found some interesting things about hv-netvsc and hyper-v. Nothing useful, just enlightening for me. You probably already know these things.

[https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/best-practices-for-running-linux-on-hyper-v](https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/best-practices-for-running-linux-on-hyper-v) has the best practices for running Ubuntu on Hyper-V.  Nothing specific about the networking, but if there is too much RAM or too many CPUs allocated, that seems to be an issue.

Towards the bottom of this [http://www.serverwatch.com/server-tutorials/installing-and-activating-hyper-v-linux-integration-services.html](http://www.serverwatch.com/server-tutorials/installing-and-activating-hyper-v-linux-integration-services.html) is some settings for the network driver to be added to  /etc/initramfs-tools/modules after the Guest Additions for hyper-v are installed. Microsoft calls these things "Hyper-V Linux Integration Services."  Are those installed into your VM? Run 
```
lsmod | grep hv
``` to see.  I suspect they are.

[https://askubuntu.com/questions/515391/unable-to-connect-to-internet-on-hyper-v-ubuntu-14-04](https://askubuntu.com/questions/515391/unable-to-connect-to-internet-on-hyper-v-ubuntu-14-04) has instructions for setting up a bridge on hyper-v. I expect the issue is in the Windows-side of the config.  On Linux, I'd manually create a bridge and specify that the VM use it in the VM machine settings. Inside the VM, it all appears as normal networking.  If I didn't use a bridge, then I'd have to setup NAT, which would isolate the VM. Sorry I can't help with any better explanation.

---

### Post by grancois on 2017-03-10
> **TheFu said:**
> So, did a little searching and found some interesting things about hv-netvsc and hyper-v. Nothing useful, just enlightening for me. You probably already know these things.
I am probably not aware of this in facts. I am a quite a newcomer in server administration, especially when using virtualization.

> **TheFu said:**
> 
[https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/best-practices-for-running-linux-on-hyper-v](https://technet.microsoft.com/en-us/windows-server-docs/compute/hyper-v/best-practices-for-running-linux-on-hyper-v) has the best practices for running Ubuntu on Hyper-V.  Nothing specific about the networking, but if there is too much RAM or too many CPUs allocated, that seems to be an issue. 

Nothing related to number of processor or RAM amount should be an issue : this virtual machine has 2 processors and 2 GB RAM (the problematic limit being respectively 7 and 30 according to this article).
But I wonder if the network issue could be related to the failover of the MAC address, as the issue appeared for (apparently, at least based on my current knowledge) no specific reason (I mean that it was not caused by a an error when manipulating configuration files or scripts or whatsoever). I think I should investigate this further.

> **TheFu said:**
> 
Towards the bottom of this [http://www.serverwatch.com/server-tutorials/installing-and-activating-hyper-v-linux-integration-services.html](http://www.serverwatch.com/server-tutorials/installing-and-activating-hyper-v-linux-integration-services.html) is some settings for the network driver to be added to  /etc/initramfs-tools/modules after the Guest Additions for hyper-v are installed. Microsoft calls these things "Hyper-V Linux Integration Services."  Are those installed into your VM? Run 
```
lsmod | grep hv
``` to see.  I suspect they are.

Here is the result, they are indeed. 
```

hv_ballon              24576 0 hv_netvsc 40960 0
hv_storvsc             20480 2
hv_utils               28672 0
scsci_transport_fc     61440 1 hv_storvsc
hv_wmbus               90112 7 hv_ballon,hyperv_keyboard,hv_netvsc,hid_hyperv,hv_utils,hyperv_fb,hv_storvsc
```
This article states that Ubuntu embeds the Hyper-V Linux Integration Service, so I suppose this could not be the origin of the issue.


> **TheFu said:**
> 
[https://askubuntu.com/questions/515391/unable-to-connect-to-internet-on-hyper-v-ubuntu-14-04](https://askubuntu.com/questions/515391/unable-to-connect-to-internet-on-hyper-v-ubuntu-14-04) has instructions for setting up a bridge on hyper-v. I expect the issue is in the Windows-side of the config.  On Linux, I'd manually create a bridge and specify that the VM use it in the VM machine settings. Inside the VM, it all appears as normal networking.  If I didn't use a bridge, then I'd have to setup NAT, which would isolate the VM. Sorry I can't help with any better explanation.
I'm going to look at this in details.

---

### Post by TheFu on 2017-03-10
hv_netvsc isn't in the left column of your ls_mod command. Any idea why?  That would mean the driver isn't loaded, but is referenced.

---

### Post by grancois on 2017-03-13
> **TheFu said:**
> hv_netvsc isn't in the left column of your ls_mod command. Any idea why?  That would mean the driver isn't loaded, but is referenced.
This is my fault, I formatted my copy/pasting the wrong way. Here is the correct response from the command :

```

hv_ballon              24576 0 
hv_netvsc              40960 0
hv_storvsc             20480 2
hv_utils               28672 0
scsci_transport_fc     61440 1 
hv_storvsc [COLOR=#000000][FONT=&amp]hv_wmbus    90112 7 hv_ballon,hyperv_keyboard,hv_netvsc,hid_hyperv,hv_utils,hyperv_fb,hv_storvsc[/FONT][/COLOR]
```

---

### Post by grancois on 2017-03-13
I had to restart the physical serveur on which I run my Virtual Ubuntu server a few minutes ago, because of a Hyper-V error.

Since the restart, my Ubuntu virtual server is working correctly anew. So apparently, all this issue had nothing to do with Ubuntu itself.

---

### Post by TheFu on 2017-03-13
Any interest in removing hyper-V?  KVM is extremely stable and clearly designed to work with Linux AND MSFT client machines. The hostOS really needs to be extremely stable for hosting production VMs.

---

### Post by grancois on 2017-03-14
> **TheFu said:**
> Any interest in removing hyper-V?  KVM is extremely stable and clearly designed to work with Linux AND MSFT client machines. The hostOS really needs to be extremely stable for hosting production VMs.
KVM is a Linux hyperviser, but my physical server is running Windows Server 2012 (and I can't change that), so this will not be possible.

---

