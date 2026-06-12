---
title: "wireless not working after upgrade"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by shakejuhn on 2008-05-06
i just install 8.04 from 7.10 and now my wireless is not working. the network shows up and tries to connect but fails. the system i have is a ibm thinkpad t60

---

### Post by RequinB4 on 2008-05-06
Please open a terminal and paste the output of
```

lspci

```

This will list all of your pci hardware devices that ubuntu sees so we can tell you what specifically to do for your setup.

---

### Post by shakejuhn on 2008-05-06
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller

---

### Post by fnielsen on 2008-05-06
I am also having the problem of "wireless not working after upgrade".

The network-admin shows greyed out controls (somewhat related to this: [http://ubuntuforums.org/showthread.php?t=737816](http://ubuntuforums.org/showthread.php?t=737816) ). The "Unlock" button is not greyed. When I press an error message says: "Could not authenticate. An unexpected error has occurred".

$ sudo ifup eth1
ifup: interface eth1 already configured
$ iwlist eth1 scanning
eth1      No scan results

---

### Post by koma77 on 2008-05-06
I have a slightly different version of this problem.

After the upgrade network applet asks for the WPA password for my wirless over and over and over again. In rare cases 1 out of 100 it will accept the password and connect to the Internet.

I also get the "Could not authenticate" when I try to unlock the network-admin!

I've seen other people having these problems as well, so I guess it's not that uncommon.

---

### Post by shakejuhn on 2008-05-06
is there an easy fix to this problem??

---

### Post by Ayuthia on 2008-05-06
I thought that I read somewhere that you might need to install linux-backports-hardy-generic.  I have not seen any verifications on whether it fixed it or not though.  I do know that the package does contain things for your wireless card.

---

### Post by koma77 on 2008-05-06
I wonder what makes this problem appear for some but not for all. On my laptop everything works fine, WiFi and wired networks are ok.

But not on my desktop machine.

Both machines are upgraded from 7.10 and the troublesome laptop is a real vanilla installation.

One difference is that my laptop was upgraded using the wireless on eth1 and my desktop computer was upgraded via eth0 wired network. Maybe that confuses network-manager at upgrade time? Or some other part of the system.

You other guys with this problem, how did you upgrade?

---

### Post by NE Key on 2008-05-06
> **koma77 said:**
> 

You other guys with this problem, how did you upgrade?

Wireless upgrade. At "re-boot" I lost wireless. Followed these instructions;

[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+4306)

And running in no time at all - did not even have to re-enter key.

---

### Post by ene_dene on 2008-05-06
I had the same problem with Intel(R) PRO/Wireless 3945 Network Connection. The problem is that 7.10 uses restricted drivers that work and 8.04 doesn't use these drivers and it doesn't work. I've downgraded laptop to 7.10 since I couldn't find a solution, and as I've seen LOOT of people has the same problem.

---

### Post by fnielsen on 2008-05-07
Min network card is this:
$ lspci | grep less
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I am now in the situation in that my wireless is "working" (since I can write this) and ifconfig looks alright, but iwlist eth1 scanning reports nothing, my knetload shows nothing, the wireless LED on the computer is off, network-admin is still greyed, and kwifimanager shows connected...

---

### Post by Ayuthia on 2008-05-07
> **fnielsen said:**
> Min network card is this:
$ lspci | grep less
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

I am now in the situation in that my wireless is "working" (since I can write this) and ifconfig looks alright, but iwlist eth1 scanning reports nothing, my knetload shows nothing, the wireless LED on the computer is off, network-admin is still greyed, and kwifimanager shows connected...
Did you install linux-backports-hardy-generic?

---

### Post by fnielsen on 2008-05-07
> **Ayuthia said:**
> Did you install linux-backports-hardy-generic?

I have now installed 

 sudo aptitude install linux-backports-modules-hardy

as described on [https://bugs.launchpad.net/linux/+bug/176090](https://bugs.launchpad.net/linux/+bug/176090)

My wireless seems to work slightly better after this. Still no LED, knetload now works, network-admin still greyed, wlassistant works, iwlist eth1 scanning reports ok. Thanks

---

### Post by shakejuhn on 2008-05-15
Is there a fix for this yet??

---

### Post by koma77 on 2008-05-15
Not that I am aware of...

I want a fix too.

---

