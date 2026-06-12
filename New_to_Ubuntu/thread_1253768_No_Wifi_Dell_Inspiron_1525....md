---
title: "No Wifi Dell Inspiron 1525..."
date: 2009-08-30
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-08-30
I'm usingKubuntu 9.04 32bit (well mint 7 really:)) and it doesn't appear to know about my wireless :cry:  this is all totally new for me as most of my previous laptops wireless was recognized out of the box...

Please help

lspci reveals this:

```
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```I've tried installing b43-fwcutter like a post somewhere on Google suggested which didn't seem to do much if anything

---

### Post by kamitsukai on 2009-08-30
Please help this is driving me barmy!!!!!!!

I've got b43-fwcutter installed but still no luck after restart, how do I check that it's loaded and if it's not how do I load the module manually????

---

### Post by kamitsukai on 2009-08-30
Ok bit more info after some hair pulling and screaming at Google I have found out that I have a special version of the BCM4312 chipset as someone on a launchpad bug report put it...it appears I have the 14e4:4315 which isn't supported by the b43 driver 

so my onlyh options are using the windows drivers or the Broadcom  [SIZE=1]Linux STA driver[/SIZE]

---

### Post by kamitsukai on 2009-08-30
> **kamitsukai said:**
> Ok bit more info after some hair pulling and screaming at Google I have found out that I have a special version of the BCM4312 chipset as someone on a launchpad bug report put it...it appears I have the 14e4:4315 which isn't supported by the b43 driver 

so my onlyh options are using the windows drivers or the Broadcom  [SIZE=1]Linux STA driver[/SIZE]

Just a little not to say that I've managed to get the wireless to work natively by compiling the Broadcom Linux STA Driver from source

and good luck to anyone else with this wireless card:lolflag:

---

### Post by pdc on 2009-09-03
LW Finger, a wireless guru on the OpenSuse forums, 

Update on using b43 with Broadcome BCM4312 PCI ID 14e4:4315

[http://forums.opensuse.org/network-internet/wireless/420760-update-using-b43-pci-id-14e4-4315-a.html](http://forums.opensuse.org/network-internet/wireless/420760-update-using-b43-pci-id-14e4-4315-a.html)

reports that > Until today, it was not possible to use the BCM4312 802.11b/g devices with b43. That is no longer the case. The code that I'm using will be in the wireless-testing git tree within a few days, and will be in compat-wireless shortly thereafter.It should be in the 2.6.32 kernel.

So thanks and recognition to the tremendous work that the linux community does on behalf of all its members to help

---

### Post by kamitsukai on 2009-09-03
> **pdc said:**
> LW Finger, a wireless guru on the OpenSuse forums, 

Update on using b43 with Broadcome BCM4312 PCI ID 14e4:4315

[http://forums.opensuse.org/network-internet/wireless/420760-update-using-b43-pci-id-14e4-4315-a.html](http://forums.opensuse.org/network-internet/wireless/420760-update-using-b43-pci-id-14e4-4315-a.html)

reports that 

So thanks and recognition to the tremendous work that the linux community does on behalf of all its members to help

Excellent thanks for letting me know :D

---

