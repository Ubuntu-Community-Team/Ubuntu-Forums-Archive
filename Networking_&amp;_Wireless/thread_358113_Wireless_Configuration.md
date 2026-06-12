---
title: "Wireless Configuration"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by miggols99 on 2007-02-10
I have set up Ubuntu and it's running perfectly! I just want to know how to connect to the internet. I have a Linksys Wireless G PCI Adapter. I looks like it's been detected. Now what? Where do I configure it? I am using WEP security using DHCP.

---

### Post by grendel38 on 2007-02-10
what exactly have you done up to now?

you say your card appeared to be recognized.  what makes you say that?  (this is sort of a repeat of the first question exactly)  tell us exactly what you've tried, and people will be in a better position to help

---

### Post by miggols99 on 2007-02-10
I have looked in the Device Manager and it is there. I went into the Network area and there was a wireless connection. I have tried filling in the configuration in there, but it does nothing.

---

### Post by grendel38 on 2007-02-10
OK, I'm by no means an expert at this but I'll pitch in until someone more experienced comes along.

what happens when you type the following into a terminal window?

> sudo lspci

what is the output it gives for network controller?

---

### Post by miggols99 on 2007-02-11
The output for sudo lspci

```
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 Bridge: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
01:00.0 VGA compatible controller: S3 Inc. ProSavage KM133 (rev 03)
```

---

### Post by grendel38 on 2007-02-11
ok. I have good news and bad news.  Broadcom chipsets seem especially problematic.  (that's the bad news.) Lots of people seem to have problems getting them to work, so it's not just you. (the good news :) )

First, are you able to disable the WEP on the network?  I know that leaves you unsecure, but it's best to take things one step at a time.  First, get the card working on an open network then add security.  If you can't disable the security, that's ok to -- but it would make things simpler (to this not too overly sophisticated ubuntu-ite anyway)

OK, that said, try the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Edgy)

and let me know how it goes.

the instructions are only a few days old and written for the new 2.6.17 kernel, so make sure that's what you are running before you attempt the instructions.

good luck, and let me know how it goes.

---

### Post by miggols99 on 2007-02-11
It's working now! Thanks for the help ;)

---

### Post by grendel38 on 2007-02-11
no problem.  glad to be of help.

enjoy ubuntu

---

