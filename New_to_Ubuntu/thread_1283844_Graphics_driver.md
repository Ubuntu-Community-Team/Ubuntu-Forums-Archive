---
title: "Graphics driver?"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by 2roombas on 2009-10-06
Typing in lspci in terminal I get the below output.  Is it possible to uprade my graphics driber?  Or is this old Dimension 2350 too old?

[INDENT]00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:06.0 Communication controller: Conexant Systems, Inc. Device 2702 (rev 01)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)[/INDENT]

---

### Post by inobe on 2009-10-06
you cannot, i would be glad just as i am to even have desktop affects regardless on how slow our gpu's are.

i have the 915 chipset on a laptop, i found that if it works let it be.

---

### Post by wdzieczny on 2009-10-06
I agree with inobe my 915 Chipset has been working great (for a 915 chipset) just let it be man.

---

### Post by Patrikf on 2009-10-07
Just wondering, do you guys with 915 chipsets have direct rendering capabilities?

---

### Post by 2roombas on 2009-10-07
> **Patrikf said:**
> Just wondering, do you guys with 915 chipsets have direct rendering capabilities?

What is that?
[U]
Update[/U]:  Just googled ie.  [http://www.gentoo.org/doc/en/dri-howto.xml](http://www.gentoo.org/doc/en/dri-howto.xml)

---

### Post by Patrikf on 2009-10-07
Thanks 2roombas, makes more sense now.

---

### Post by noobie1 on 2009-10-07
Ah!! someone with a 845 chipset.
I've been trying to get my Samsung V25 laptop working properly with linux.
Maybe searching the web for a dell 2350 would be more successful. 

What version are you running?
What configuration did you do?
Is everything working ok?

Ubuntu seems to work best "out the box" but it still has graphics/standby issues.
eg the virtual consoles have the wrong resolution (right edge of screen is repeat of left - maybe a memory issue?)

---

### Post by 2roombas on 2009-10-09
Were you asking me those questions, noobie1?

I upgraded to Karmic (9.10) now on both this Dell Dimension 2350 desktop and my Inspirion 1500-something laptop.  It's doing just fine on the laptop, I even get the cool 3d effects on that one, but I'm thinking of re-loading 9.04 (Jaunty) on this desktop. 

It seems that everyday I'm cold booting multiple times because the screen will just freeze, lock-up, stop everything. Nothing will work, no mouse curser movwment, nothing at all, so I'll have to shut down, wait a few minutes then restart.  I never had that problem with 9.04 on this computer. 

Anyone know why that is occurring?  Do you think this computer is just too old for 9.10, or will whatever theat bug is will get wotked out eventually?

---

### Post by rickh57 on 2009-10-11
I'm having similar symptoms on my Compaq EVO D510 system with an 82845G graphics controller. The system is alive; it serves up web pages and I can ssh to it, it is just the display that stops functioning.

---

### Post by 2roombas on 2009-10-11
I ended up just reloading 9.04 on that computer... No more lock-ups on there now...yay!:)  I sure wish someone could tell me why that was happening, and if it'll be fixed or not wit the release?!

---

