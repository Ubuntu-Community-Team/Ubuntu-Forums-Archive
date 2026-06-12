---
title: "Accessing web server / Setting up wireless"
date: 2010-04-05
forum: New to Ubuntu
---

### Post by Nascentes on 2010-04-05
So... Hi, I'm Nascentes and this is my first post on the Ubuntu forums :)


_Boring but necessary introduction_

I have been refraining from posting on this forum because I like to figure things out myself but I am just stumped

Right now I am running two 9.10 Ubuntu servers. One on an old dedicated desktop in my basement, and the other on a separate partition on my laptop. I set both of them up over the weekend and this was my first time working with Ubuntu Server ed. 
I have only worked with Ubuntu one other time and it was a desktop ed.

That last paragraph wrapped up: I am very new to linux overall. lol

So, I have two problems and they are as follows. Any help is much, much appreciated.

_Problem #1_

On my desktop Ubuntu server, all is going fine and well, except that I cannot ssh into the server from outside my network.
I can access it just fine using it's LAN ip, however I am unable to access it through it's domain or WAN ip...

_Problem #2_

On my laptop Ubuntu server, I am unable to establish a wireless connection to my router, any help would be great. 
Also, for the record, I did not figure out how to setup a wireless connection on my desktop Ubuntu server either. I hooked it directly into the router.

Once again, any help would be fantastic

Thanks :)

-Nascentes

---

### Post by halitech on 2010-04-05
Problem 1: did you configure your router to allow SSH connections to go through to the server?

Problem 2: is it an internal wireless card? a USB wireless device? what is the output of lspci and lsusb

---

### Post by Nascentes on 2010-04-06
Problem 1: Solved. Thank you

Problem 2:

Yes, it is an internal wireless card.


lspci

```

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00.02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.4 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:03.0 Network controller: Broadcom Corporation BCM4311 [AirForce 54g] 802.11a/b/g PCI Express Tranceiver (rev02)

```lsusb

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.0 root hub

```Also, just out of curiosity, is there an easier way to post these rather than type them out? xD

Sorry it took so long to respond. Busy day yesterday lol

Edit:

Also, I forgot to mention that when I type iwconfig, it recognizes wlan0
So, I set the essid and it worked. Then I when to set the key using "iwconfig enc" and it appeared to work, but it did not.

I think it may be because I have WPA security

Edit 2:

Sorry, more info lol

Alright, so, I think I've narrowed it down to this firmware that I need. "bf3-fwcutter"
Only problem is, I can't access the internet to download it, and I can't install it manually because it will not mount my flash drive.
On my other server, I wouldn't mount either, I had to install some automount packages. Don't remember what they were called, but they don't help me seeing as how I don't have access to the internet.

This is what I get when I attempt to mount using "sudo mount -t vfat /dev/sdb /mnt/flash" : /
```

[     360.421750] FAT: invalid media value (0x06)
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
           missing codepage or helper program, or other error
           In some cases useful info is found in syslog - try
           dmesg | tail or so

```
Also for the record, my flash drive is formated in FAT32 and in fdisk, it is listed as /dev/sdb

So, in a nutshell, I need wireless to fix the wireless :S ... I think


Edit 3:

Not sure if this helps but, when I star the server, I get this

```

[     9.378646] render error detected, EIR: 0x00000010
[     9.378649] page table error
[     9.378651]     PGTBL_ER: 0x00000100
[     9.378654] [drm:i915_handle_error] *ERROR* EIR stuck: 0x00000010, masking
[     9.378662] render error detected, EIR: 0x00000010
[     9.378664] page table error
[     9.378666]     PGTBL_ER: 0x00000100

```Sorry again for all the info. I am still very new to Linux in general and still have a lot to learn.

---

### Post by anewguy on 2010-04-06
The firmware cutter is available on the LiveCD (assuming you installed from that) for regular Ubuntu - don't know if it'd be on the server version or not.

Located on the CD in pool/main/b/b43-fwcutter


Dave ;)

EDIT:  Also, a while ago I set up a server just to try it out, and it also was wireless.  I remember making the IP address on the server static instead of dynamic.  I have no idea if this a requirement or just something I did.

---

### Post by sandyd on 2010-04-06
> **anewguy said:**
> The firmware cutter is available on the LiveCD (assuming you installed from that) for regular Ubuntu - don't know if it'd be on the server version or not.

Located on the CD in pool/main/b/b43-fwcutter


Dave ;)

EDIT:  Also, a while ago I set up a server just to try it out, and it also was wireless.  I remember making the IP address on the server static instead of dynamic.  I have no idea if this a requirement or just something I did.
Its not really a requirement. I got a server with a dynamic IP too + wireless (broadcom STA), the router and load balancing system just locks onto the mac address...

---

### Post by v1ad on 2010-04-06
oops already solved

---

### Post by Nascentes on 2010-04-07
> **anewguy said:**
> The firmware cutter is available on the LiveCD (assuming you installed from that) for regular Ubuntu - don't know if it'd be on the server version or not.

Located on the CD in pool/main/b/b43-fwcutter


Dave ;)

EDIT:  Also, a while ago I set up a server just to try it out, and it also was wireless.  I remember making the IP address on the server static instead of dynamic.  I have no idea if this a requirement or just something I did.

Hm, my ip is dynamic and the cutter wasn't on the cd :S


> **v1ad said:**
> oops already solved

Not solved yet... lol

---

