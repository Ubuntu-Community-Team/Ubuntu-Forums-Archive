---
title: "[SOLVED] Wireless no longer working"
date: 2008-03-02
forum: Networking &amp; Wireless
---

### Post by nikRbokR on 2008-03-02
Well, I just installed 7.10 Ubuntu this weekend.  Today, I downloaded all of the software updates that it told me to.  Up until then, wireless was working.  However, after the update, I lost wireless capability. I went to the network connection icon (@ top) and it doesn't find any wireless networks.

I have no idea why it would do this.  i'm new to Linux and am not sure how to fix it.

This is the output for lspci:

> 00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 CardBus bridge: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)


---

### Post by suibhne on 2008-03-02
not too sure if this is appropriate for your problem or not, but have you looked at

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

?

---

### Post by Hightide on 2008-03-02
Hi

Really surprised as the intel 2915abg is supported.

have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=642357")

regards
:)

---

### Post by nikRbokR on 2008-03-02
checked my /etc/network/interfaces and this is what was in the file
```
auto lo
iface lo inet loopback

```

not sure what to do with it.

---

### Post by nikRbokR on 2008-03-02
bump

---

### Post by nikRbokR on 2008-03-05
bump

---

### Post by beefsack on 2008-03-06
Doesn't help the problem, but I would like to point out after a recent update a few days ago my wireless stopped working too... Booted into Ubuntu, did an update without touching anything (included kernel update), rebooted and wireless hasn't worked since :(

---

### Post by nikRbokR on 2008-03-07
> **beefsack said:**
> Doesn't help the problem, but I would like to point out after a recent update a few days ago my wireless stopped working too... Booted into Ubuntu, did an update without touching anything (included kernel update), rebooted and wireless hasn't worked since :(

Ah.  Well, same for me.  Except... I didn't have Ubuntu before that :(

---

### Post by nikRbokR on 2008-03-23
Okay.  Nevermind.  I got it to work.

I really didn't do anything.  I just reinstalled Ubuntu to my HD.  I had to repartition my HD anyway, so when I reinstalled last night, and updated this morning, it is working well.

Thanks to all who helped!

---

