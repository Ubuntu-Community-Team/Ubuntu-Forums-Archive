---
title: "Disastrous attempt at setting up wireless for ubuntu!"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by Bartikky on 2007-06-11
Hi, I'm in search for help for setting up my wireless connection on Ubuntu, my attempt with some help was disastrous, I seemed to get somewhere, then later realise I'm getting no where at all, I'm about to format ubuntu's partition and reinstall it (this is Ubuntu 7.04 by the way), but first want to find out if there is anyone out there willing to help me before I reinstall for no reason at all... My problem is posted in more detail in this thread [http://ubuntuforums.org/showthread.php?t=470600](http://ubuntuforums.org/showthread.php?t=470600), I'm not certain I went about configuring the connection properly and can't recall all the things I've done/changed/editted/installed. So this is why I'm wanting a format and reinstall.

Thanks, Bartikky

PS, I'll need a step-by-step help, since I'm very new to Linux Ubuntu.

---

### Post by spd106 on 2007-06-11
I haven't got one of these so I can't do much to you help with the installation setup process. This page might be useful for specific information [http://www.qbik.ch/usb/devices/showdev.php?id=1218](http://www.qbik.ch/usb/devices/showdev.php?id=1218)

---

### Post by kevdog on 2007-06-11
Ok maybe we can figure this out.

What type of wireless interface are you using -- PCI or USB?
What is the name of the card or USB dongle you are using?
What is the output of lspci and lspci -n?
How did you install the drivers for your network device in the first place?

---

### Post by Bartikky on 2007-06-11
USB interface...
What's USB dongle? (excuse my inexperience)...
as for the lspci and lspci -n output, I'll get back to you on that when I arrive back home tomorrow, shall I also send lsusb and lsusb -n output aswell?...
I installed all drivers through the terminal...

---

### Post by Bartikky on 2007-06-12
brandon@brandon-ubuntu:~$ lspci

00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)
02:00.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev f0)
02:02.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
02:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

brandon@brandon-ubuntu:~$ lspci -n

00:00.0 0600: 8086:2570 (rev 02)
00:01.0 0604: 8086:2571 (rev 02)
00:1d.0 0c03: 8086:24d2 (rev 02)
00:1d.1 0c03: 8086:24d4 (rev 02)
00:1d.2 0c03: 8086:24d7 (rev 02)
00:1d.3 0c03: 8086:24de (rev 02)
00:1d.7 0c03: 8086:24dd (rev 02)
00:1e.0 0604: 8086:244e (rev c2)
00:1f.0 0601: 8086:24d0 (rev 02)
00:1f.1 0101: 8086:24db (rev 02)
00:1f.3 0c05: 8086:24d3 (rev 02)
00:1f.5 0401: 8086:24d5 (rev 02)
01:00.0 0300: 1002:5964 (rev 01)
01:00.1 0380: 1002:5d44 (rev 01)
02:00.0 0480: 1131:7133 (rev f0)
02:02.0 0703: 10b9:5459
02:0a.0 0c00: 104c:8023
02:0b.0 0200: 10ec:8139 (rev 10)

lsusb

Bus 005 Device 003: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 005 Device 002: ID 05e3:0710 Genesys Logic, Inc. USB 2.0 33-in-1 Card Reader
Bus 005 Device 005: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 046d:c001 Logitech, Inc. N48/M-BB48 [FirstMouse Plus]
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 077b:2219 Linksys WUSB11 V2.6 802.11b Adapter
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0ed1:6680 WinMaxGroup USB Flash Disk 64M-B
Bus 002 Device 001: ID 0000:0000

---

### Post by happynix on 2007-06-12
Fiesty
Averatec 2100 series laptop

I too seem to have a non functioning ethernet driver / wireless problem. 
I have a bcm4306 wireless card and a VIA VT6102 (rhine--II) ethernet controller.  Before I downloaded the BCM firmware (using the bcm43xx-fwcutter package) the wireless obviously didn't work, but more disturbing neither did my ethernet adapter.  However when I boot to the maintaince kernel (No X) the ethernet works just fine.

So I installed the bcm 4306 firmware.  Now the system locks up hard whenever I boot into X.

In command line the ethernet and the bcm430g wifi work.  

My guess is the vt6102 (ethernet) the bcm4306 (wifi) and the vt8378 (S3 UniChrome VGA) are all sharing the same IRQ.

I don't have the fix yet (Bios has no advanced options).  But I do hope to find something.

---

### Post by happynix on 2007-06-12
Good News.

I added 'Option  "DisableIRQ"' to the device section of xorg.conf

Voila!
Everything works.

---

### Post by spd106 on 2007-06-13
[QUOTE=happynix]
Voila!
Everything works.
[/QUOTE]
That's great news!

If you can spare the time, could you create a page in the wiki as part of the [Laptop Testing Team]("https://wiki.ubuntu.com/LaptopTestingTeam") and fill in the steps you took. That would be a big help for other Averatec 2100 owners.

It might even be a good idea to create a bug report on launchpad too.

Thanks

---

### Post by spd106 on 2007-06-13
@Bartikky

Are you able to scan for networks? Try this command
```
sudo iwlist wlan0 scan
```

The output of this command may be useful in diagnosing driver configuration problems.
```
sudo lshw -class network
```

---

