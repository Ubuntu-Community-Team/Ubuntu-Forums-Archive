---
title: "Dell Latitude D620 DELL 1490 Wireless"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by davidvasta on 2007-03-21
So let me get you all as much info as possible. I have a DELL Latitude D620. It's for work and I refuse to keep running windows. I want to get Ubuntu 6.10 on it and have followed everything I can find to get the Wireless working.

From what I can tell from DELL it has a DELL TrueMobile 1400 (BCM4309 - 802.11a+b+g) and in my case a 1490.

I have tried using NDSWrapper and can get the diver installed, but I can't get the wireless to turn on. Yes I know this should be simple but it's not. DELL used to make it the FN+F2 key and it would turn on the card, but now there is a switch on the left hand side that is supposed to do it and it does not. Even if you tell the BIOS to just leave it on it won't. Moving the switch does not help either?

So my question is how to I get the switch to turn the card on or how to I get the card on period. Ubuntu sees the card and knows what it is, but I can't connect if I can't get it turned on?

Cart before the horse kind of thing.

Here is what I know about the card:

Broadcom Corporation Unknown device 4311 (rev 01)

I think that is the Wireless card?

Please help ASAP and If I think of more I will add it....

Thanks,
David

---

### Post by renzokuken on 2007-03-21
have a look at [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx) then click on the appropriate link at the bottom

---

### Post by CrypticBlade on 2007-03-21
davidvasta,

I think this will work wonders for your D620, I know it did mine: **[http://sourceforge.net/projects/lc4ul/]("http://sourceforge.net/projects/lc4ul/")**

In fact I am writing this post from my fully functional D620 laptop.

I built the Laptop Configuration for Ubuntu Linux script specifically for my Latitude D620 and hope to expand it to support other Dell models in the future with the help of the community.

It's still a work in progress so please submit any feedback for improvements.

Regards,
CB

---

### Post by WinNot on 2007-04-23
Whin I run the pearl script foud in this site on my Dell D620 with Ubuntu edgy, it starts up and then hangs at Updating graphics .... any ideas ?

---

### Post by CrypticBlade on 2007-04-23
Please ensure you are connected to the Internet via a wired connection and have the Edgy CD/DVD in the CD/DVD drive when you run the script.

Also, could you post the output from the following command:
```
lspci
```

Thanks

---

### Post by WinNot on 2007-04-27
I did indeed verify that my ubuntu live CD Ver 6.10 was in the CDROM drive and I was connected to the internet via ethernet cable.. once I figured out how to start up perl again, I re-ran the script and it still gets stuck at "... installing graphics driver ... and will just sit there.

As you requested, here is the output of lcsi - and btw way many thanks for taking the time to help out.

/ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 01d7 (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$

---

### Post by pike2k on 2007-05-03
I had already fixed most annoyances before I tried your script, all that remained was the darned wireless.
first I thought it hanged on the graphics part, but it was just a huge delay until it started downloading the stuff.

I restarted in the hope that the wifi led would go on, still no wifi led though. the only thin the switch on the left side toggles is the bluetooth. worth mentioning is that before I run your script, I tried the ndiswrapper_setup method

here's my complete lspci output:
```

pike@dell-linux:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
03:01.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller (rev 40)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

```

edit: forgot to mention that I use Feisty Fawn
edit2: forgot to mention that before I started "fixing" the wireless, it atleast showed up in Network Settings app, it doesn't anymore :(
edit3: I haven't done any changes... but today after a fresh restart the wifi LED is enabled, but I still can't see any wireless card in Network Settings
edit4: the wifi LED may be ON, but the wireless toggle on left has no effect at all on it, still just affects bluetooth

---

