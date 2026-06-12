---
title: "Fail to suspend"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by neher on 2008-12-25
Happy Gift Day.  I just installed Ubuntu 8.04 a couple days ago on a Dell Dimension 2400.  I am having a problem going into Suspend, or rather, when I do suspend, I have all kinds of glitch things happening on the display when coming out of suspend, as in, the display flicks all over when I do anything upon returning from suspend. Any ideas?

---

### Post by labrat37 on 2008-12-25
Have you installed the drivers for your video card?

---

### Post by igknighted on 2008-12-25
What type of laptop do you have?  And could you post the output of 'lspci' so we know what the hardware is?

---

### Post by neher on 2008-12-26
lspci:

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

As far as I can tell, I didn't need to install any drivers for the graphics card on this machine.

---

### Post by neher on 2008-12-27
I'm still having this problem.  I am not using any restricted drivers.

---

### Post by whiteshiel on 2009-01-19
*BUMP* having the same issue with a Dell Latitude D620

---

### Post by HeWhoE on 2009-09-08
I'm having this problem too.  This happens on my Dell Dimension 4500s desktop system when operated by Hardy, even with the latest updates from the official repository as of September 8, 2009.

---

