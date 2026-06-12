---
title: "Enabling wireless with Atheros chipset"
date: 2008-02-08
forum: Networking &amp; Wireless
---

### Post by slarrabe on 2008-02-08
I've been digging through the forums and found some topics similar to this, but none seem to work.  I'm trying to get my wireless card (Atheros 5007EG) to work properly.  I've tried using ndiswrapper (didn't work) and madwifi is not supported for my processor type (AMD Turion 64).

I've managed to download Windows drivers and enable them using Windows Wireless Drivers, but wireless is still disabled.  Restricted Drivers Manager indicates the card is in use and enabled.  Other things I've checked:

lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 4c:cb:ed:24:1b:00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.60 ip=137.28.55.39 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR5006EG 802.11 b/g Wireless PCI Express Adapter
       vendor: Atheros Communications, Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
```

lspci
```
00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2)
00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2)
00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2)
00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0533 (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
```

How do I get this accursed wireless network enabled?!  It isn't showing up under Network.  All I have is Wired connection (currently using) and Modem connection.

---

### Post by bwhite82 on 2008-02-08
What shows when you issue the command: ifconfig -a? If you see your wireless card listed, try the command: sudo ifconfig deviceShortTitle up (example sudo ifconfig wlan0 up). Also, make sure you try pressing the chassis switch for your wireless card (if you have one.)

---

### Post by slarrabe on 2008-02-11
Here's what I get when I type ifconfig -a in the terminal.  Yes, I made sure the chassis switch was turned on.

```
eth0      Link encap:Ethernet  HWaddr 4C:CB:ED:24:1B:00  
          inet addr:137.28.55.39  Bcast:137.28.55.255  Mask:255.255.255.0
          inet6 addr: fe80::4ecb:edff:fe24:1b00/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3584 errors:813 dropped:0 overruns:0 frame:809
          TX packets:3169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4623821 (4.4 MB)  TX bytes:261015 (254.8 KB)
          Interrupt:20 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

It doesn't seem to recognize the card being present.:confused:

---

### Post by Hightide on 2008-02-11
Hi slarrabe

I can see by the output from lshw c -network '  *-network UNCLAIMED' that there is a driver problem

see can this site help [http://madwifi.org/wiki/Compatibility/Atheros](http://madwifi.org/wiki/Compatibility/Atheros)

and have a look at Kevdog's wireless [tutorial]("http://ubuntuforums.org/showthread.php?t=571194")

hope this helps

regards

:)

---

### Post by slarrabe on 2008-02-11
Hightide,

I tried installing the madwifi drivers but no luck.  I suspected they wouldn't since they aren't compatible with 64-bit systems (what I've got, see signature).  Are there ANY 64-bit drivers out there?

---

### Post by slarrabe on 2008-02-12
I did it!:shock:  I followed the advice from the site below and everything worked!

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

No more ](*,) for me.  :guitar:
=D> =D> =D> =D> =D>

---

### Post by dca on 2008-02-12
Kudos!!!  You should create a directory called 'download' or something in your /home and keep the Win32 drivers whatever else you use for sys config there in case you need them in the future.  Every system I've created for family/friends that run Ubuntu and have funny hardware I always save the tar files there...

---

### Post by Caraibes on 2008-02-12
Just a word to say that I successfully configured the Atheros AR5007EG, in an Acer laptop.
It was running Linux Mint 4.0, which is basically Ubuntu 7.10.

I simply followed this guide:
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#more-394](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#more-394)

And it "just worked" !!!

Good luck to you !

---

### Post by braveerudite on 2008-05-19
> **slarrabe said:**
> I did it!:shock:  I followed the advice from the site below and everything worked!

[http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/](http://quilombo.wordpress.com/2008/01/09/atheros-ar5006eg-in-ubuntu-710-gutsy-gibbon/)

No more ](*,) for me.  :guitar:
=D> =D> =D> =D> =D>

I have same laptop as you and I haven't been able to do it following the link you gave.

I need "net5416.inf"  but is not on nowhere to be found. 


Did you did this with 32 or 64 bit Ubuntu


Thank you for your time.

---

