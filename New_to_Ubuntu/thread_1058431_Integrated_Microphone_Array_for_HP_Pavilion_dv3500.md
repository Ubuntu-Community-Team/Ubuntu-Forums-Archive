---
title: "Integrated Microphone Array for HP Pavilion dv3500"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by Timzor on 2009-02-02
Hello.  I am new to Ubuntu, and linux in general.
Ubuntu has been working well for me, but I cannot figure out how to use the built-in microphone in my HP Pavilion dv3500 Notebook PC.

I am using Ubuntu 8.10- the Intrepid Ibex.

Can anyone help?

---

### Post by Timzor on 2009-02-02
bump

---

### Post by Crafty Kisses on 2009-02-02
What are the results of this command?
```
lspci
```

---

### Post by schwascore on 2009-02-02
have you tried this in a terminal window?

[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

---

### Post by Timzor on 2009-02-02
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9300M GS (rev a1)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

> **schwascore said:**
> have you tried this in a terminal window?

[http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/](http://ubuntu.wordpress.com/2005/12/05/fixing-the-errant-microphone/)

Actually, yes.  It didn't work.

---

### Post by Timzor on 2009-02-02
bump

---

### Post by Timzor on 2009-02-02
bump

---

### Post by fresneda on 2009-02-08
According to this user
[http://ubuntuforums.org/showthread.php?t=1028640](http://ubuntuforums.org/showthread.php?t=1028640)
it still doesn't work with alsa 1.0.19
I also have the same problem, and will report back in case I succeed
in making the capture device work.

---

### Post by fresneda on 2009-02-10
Take a look at the thread 
[http://ubuntuforums.org/showthread.php?t=1028640](http://ubuntuforums.org/showthread.php?t=1028640)
I have posted a possible solution.

---

