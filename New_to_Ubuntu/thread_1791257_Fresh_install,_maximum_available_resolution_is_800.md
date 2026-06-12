---
title: "Fresh install, maximum available resolution is 800x600"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by 9antreas9 on 2011-06-26
I am a windows user and installed ubuntu 11.04 about an hour ago, so please your responses as noob friendly as possible.
 
I googled a bit but I didn't find anything to help me.
 
I the exact distribution i installed is:
 
```
root@ubuntu:~# cat /etc/*-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
```my lspci command outputs the following:
 
```
root@ubuntu:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
[COLOR=red]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)[/COLOR]
[COLOR=red]00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)[/COLOR]
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
02:0c.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
```Please help me get my monitor in decent resolution.

---

### Post by jtarin on 2011-06-26
[Let's see what this does.]("http://www.upubuntu.com/2011/04/how-to-know-your-current-screen.html")

---

### Post by 9antreas9 on 2011-06-26
Thank you for you response.

I did:

xrandr -s 1024x768

That changed the resolution as expected, but created a 2 inch thick black strip on the top of the screen and one on the right.

The launcher seems intact, but the top menu bar disappeared. After i clicked where it was supposed to be, it appeared again, over the 2 inch black strip. So I thought restarting the computer would solve the black strip thing and it would be done.

I restarted the computer normally, but the resolution was reverted to 800x600 when ubuntu was loaded again.

---

### Post by jtarin on 2011-06-26
Ah! your using 11.04.....sorry...out of my area of expertise.Might edit your first post to reflect this. It's not too obvious.

---

