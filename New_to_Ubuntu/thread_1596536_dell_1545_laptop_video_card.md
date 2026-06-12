---
title: "dell 1545 laptop video card"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by ibdonna on 2010-10-14
First post newbie seems the laptop does not recognize my video card  was told to post lspci can anyone help me please


donna@donna-Inspiron-1545:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 13)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
donna@donna-Inspiron-1545:~$ 

Thank you Donna

---

### Post by ibizatunes on 2010-10-14
Hello
Which version of ubuntu are you using? And what is the display not doing?
[http://webapps.ubuntu.com/certification/hardware/200911-4633/](http://webapps.ubuntu.com/certification/hardware/200911-4633/)
your hardware look to be well supported, and have been certified for ubuntu 10.04

---

### Post by ibdonna on 2010-10-14
sorry should have told you oops ubuntu 10.10 it supports 1360 x768 (16:9) full screen

when  I try and use 1024 x 768 (4:3) page will only fill 3/4 of screen

 I should have been more precise  sorry

Donna

---

### Post by ibizatunes on 2010-10-14
Ok
you have gone to system > preference > monitor
and tried up'in the resolution there?

---

### Post by ibdonna on 2010-10-14
Yes I have I ave one resolution higher that also gives me a full screen

2 resolutions lower than the 1024 x 768 that still give me 3/4 screen have rebooted and checked still 3/4 screen 

my friend that installed ubuntu 10.10 for me ibbill told me to reboot with no luck. Then advised me to check here thanks again for your help. I can live with the 1360 x768 but makes a few games i play little stretched looking.

Donna

---

### Post by ibizatunes on 2010-10-14
you may have been better off with 10.04 as it has been certified 
try downloading that on a live CD, and see what resolution it pop up with
I had a google around and not found any issue, it could be a bug with 10.10 thought!

---

### Post by ibdonna on 2010-10-14
Thank you ever so much for your help.

Will try what you suggested with a little help from ibbill who has a 10.04 disk will post what I find out. Again thans ever so much.

Donna

---

