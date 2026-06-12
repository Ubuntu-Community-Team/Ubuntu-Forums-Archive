---
title: "New user having problem with screen resolution"
date: 2009-12-30
forum: New to Ubuntu
---

### Post by cavalete on 2009-12-30
I installed UBUNTU 9.10 today from a magazine cover disk (Computer Shopper - "Linux .. The complete manual)

Initial installation appeared OK and UBUNTU recognized my Fujitsu 19 inch monitor and set the resolution correctly to 1440 x 900.

I then followed the recommendation to download and install all updates since the CD had been released.

Following the restart the resolution is stuck at 800 x 600 and I can't change this to 1440 x 900.

Are there any instructions available which may show me how to configure the video correctly?

Thanks for any help you can provide.

-----------------------------


As suggested by Danastasio I entered "lspci" which gave the following output:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
01:0a.0 USB Controller: NEC Corporation USB (rev 41)
01:0a.1 USB Controller: NEC Corporation USB (rev 41)
01:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---------------------------------

Also in response to HappyFeet
Going to system>administration>hardware drivers 

the following information was returned:

 "No proprietary drivers are in use on this system"

---

### Post by QIII on 2009-12-30
Working the same problem with the updates right now for Lucid (10.04).  May be a similar issue for Karmic, but I haven't run into it.

I haven't had a chance to do much research on launchpad, but I'm willing to bet a bug and possibly even a work-around for Karmic have been posted.  I plan to do some searching with regard to Lucid.

I have noticed the problem both with and without the proprietary driver (ATI Catalyst) installed.

I suggest searching launchpad (upper right, see the link "launchpad.net") and doing a search, which is what I plan to do this evening.

---

### Post by HappyFeet on 2009-12-30
Go to system>administration>hardware drivers and see if the video driver is available. If so, install and reboot.

---

### Post by danastasio on 2009-12-30
what is the output of
```
lspci
```

That will tell us exactly what hardware that your system is recognizing, and what drivers that you need.

---

### Post by cavalete on 2009-12-30
As suggested by Danastasio I entered "lspci" which gave the following output:

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 02)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 02)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)
01:0a.0 USB Controller: NEC Corporation USB (rev 41)
01:0a.1 USB Controller: NEC Corporation USB (rev 41)
01:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

---------------------------------

---

### Post by cavalete on 2009-12-30
Also in response to HappyFeet
Going to system>administration>hardware drivers 

the following information was returned:

"No proprietary drivers are in use on this system"

---

### Post by cavalete on 2009-12-30
QIII

Thanks for the suggestion.

I will try to search launchpad to see if there is any information there.

---

### Post by cavalete on 2009-12-30
SOLVED

Thanks to Giblet5 in the General Help section of the forum for the following information:

                [http://ubuntuforums.org/showthread.php?t=1324239](http://ubuntuforums.org/showthread.php?t=1324239)

At first this looks a little scary to newbies like me.

But the instructions are clear and now my machine boots up OK in the 1440 x 900 resolution mode.

I should probably carry out a full power cycle rather than just a reboot before I get too excited but so far so good.

Thanks to Giblet5 and all forum members who made suggestions

---

