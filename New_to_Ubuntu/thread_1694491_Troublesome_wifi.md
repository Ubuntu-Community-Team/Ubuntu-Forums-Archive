---
title: "Troublesome wifi"
date: 2011-02-24
forum: New to Ubuntu
---

### Post by Lloydstedman on 2011-02-24
**My wifi has been fine** since I installed Ubuntu 10.4 on my Asus 1005p two weeks ago. It's connected all over the place and I live in a place in the middle east where wifi can be 'awkward' and restricted somewhat. I've had no issues.

However, for some reason the wifi will not now connect to the internet or even shake hands with a network at all. Neither to local networks I have used before happily, or to my own Mac created network at home that again has worked blamelessly before now.

The wifi works, it sits on the top taskbar and recognises the networks but will not connect. The connection icon will spin away but never take root on a regular network.

(The only way I can get online is via a USB 3g stick, which is fine, and of course very different.)

Is there a diagnostic tool I can use to find out the wifi issue?
Any idea what has changed as things were fine?
And I'm pretty new to Linux and although i use the terminal happily, I'm a cut and paste man at best.

I've updated software since this happened and rebooted, to no avail.

Ideas appreciated.

Regards, Lloyd


    description: Wireless interface 
                product: AR9285 Wireless Network Adapter (PCI-Express) 
                vendor: Atheros Communications Inc. 
                physical id: 0 
                bus info: pci@0000:02:00.0 
                logical name: wlan0 
                version: 01 
                serial: 1c:4b:d6:82:a9:73 
                width: 64 bits 
                clock: 33MHz 
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn 
                resources: irq:17 memory:fbff0000-fbffffff 
        *-pci:2 
             description: PCI bridge 
             product: N10/ICH 7 Family PCI Express Port 4 
             vendor: Intel Corporation 
             physical id: 1c.3 
             bus info: pci@0000:00:1c.3 
             version: 02 
             width: 32 bits 
             clock: 33MHz 
             capabilities: pci pciexpress msi pm bus_master cap_list 
             configuration: driver=pcieport 
             resources: irq:26 ioport:e000(size=4096) memory:f7f00000-f7ffffff memory:80400000-805fffff(prefetchable) 
           *-network

---

### Post by Bodsda on 2011-02-24
> **Lloydstedman said:**
> **My wifi has been fine** since I installed Ubuntu 10.4 on my Asus 1005p two weeks ago. It's connected all over the place and I live in a place in the middle east where wifi can be 'awkward' and restricted somewhat. I've had no issues.
 
However, for some reason the wifi will not now connect to the internet or even shake hands with a network at all. Neither to local networks I have used before happily, or to my own Mac created network at home that again has worked blamelessly before now.
 
The wifi works, it sits on the top taskbar and recognises the networks but will not connect. The connection icon will spin away but never take root on a regular network.
 
(The only way I can get online is via a USB 3g stick, which is fine, and of course very different.)
 
Is there a diagnostic tool I can use to find out the wifi issue?
Any idea what has changed as things were fine?
And I'm pretty new to Linux and although i use the terminal happily, I'm a cut and paste man at best.
 
I've updated software since this happened and rebooted, to no avail.
 
Ideas appreciated.
 
Regards, Lloyd
 
 
description: Wireless interface 
product: AR9285 Wireless Network Adapter (PCI-Express) 
vendor: Atheros Communications Inc. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: wlan0 
version: 01 
serial: 1c:4b:d6:82:a9:73 
width: 64 bits 
clock: 33MHz 
capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn 
resources: irq:17 memory:fbff0000-fbffffff 
*-pci:2 
description: PCI bridge 
product: N10/ICH 7 Family PCI Express Port 4 
vendor: Intel Corporation 
physical id: 1c.3 
bus info: pci@0000:00:1c.3 
version: 02 
width: 32 bits 
clock: 33MHz 
capabilities: pci pciexpress msi pm bus_master cap_list 
configuration: driver=pcieport 
resources: irq:26 ioport:e000(size=4096) memory:f7f00000-f7ffffff memory:80400000-805fffff(prefetchable) 
*-network
 
Hi Lloydstedman,
 
Welcome to the Forums
 
Are you able to connect to these networks if you use an ethernet cable? This would rule out strange stupid things like mac address filtering.
 
The next thing I would look at would be disabling any encryption on the networks. Just to prove whether the Ubuntu device can connect. If it can, then we are looking at a router/encryption issue.
 
One other thing you can try is using WICD as your network manager instead of whatever gnomes default network manager is. Be careful if you go for this option though, as soon as you start installing WICD, the gnome network manager will be uninstalled, so if something goes wrong with the WICD install, your in trouble.
 
Can you also try booting off a 10.4 live cd and attempt to connect to your networks.
 
Hope this helps,
Bodsda

---

### Post by Lloydstedman on 2011-02-27
Thanks. I can't actually try an ethernet as I'm generally in cafes or wifi hotspots.

I _can_ create a network at home off a mac laptop, but can't ethernet into that. It doesn't currently want to connect to that homegrown network, but has in the past. 

But it does connect to some wifi networks and hotspots happily and then frustratingly doesn't to others. I can be in a place where there are 20 people with windows and macs happily online, and I am not. So I'm pretty sure it's a localised issue with my Ubuntu.

I will try booting 10.4 off a USB and seeing how it connects. What will that tell me?

Can you also me how to install WICD and why you think I need to?

Thanks again, much appreciated,

---

### Post by Lloydstedman on 2011-02-27
And is there an issue with the fact that 

system/administration/hardware drivers  tells me that 

'no proprietory drivers are in use on this system'

---

### Post by Habeouscorpus on 2011-02-27
> **Lloydstedman said:**
> And is there an issue with the fact that 

system/administration/hardware drivers  tells me that 

'no proprietory drivers are in use on this system'


Nope, that just means that your hardware plays nice without proprietary drivers. That can be a good thing.

---

