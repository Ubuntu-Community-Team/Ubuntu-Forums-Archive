---
title: "I Need Help With Connection"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by boboyo on 2007-12-27
ok.....

on my laptop, i paritionned my hard drive for vista and 64-bit ubuntu.

i also got wireless internet so i can go on the internet with my laptop. I got a WPA personnal thing and the connection is DHCP(no idea what it is....) when i set up my connetcion on vista, it works normally. But on ubuntu, it doesnt work. In order to be connected to the net, i have to unplug the connection cable from my pc and i have to plug iy in my laptop. When i do that, i can go on internet!

is there a way that i can go on the internet with linux without the cable?

---

### Post by csat on 2007-12-27
Yes, there is...  First of all you should find out which wireless board your computer is using and then looking for it here.  If you don't know how to find just go to a terminal console and type lspci -v followed by enter.

---

### Post by boboyo on 2007-12-27
here i pasted everything what was written when i wrote the thing in terminal

what do i do now?

00:00.0 RAM memory: nVidia Corporation Unknown device 0547 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 ISA bridge: nVidia Corporation Unknown device 0548 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0

00:01.1 SMBus: nVidia Corporation Unknown device 0542 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 3080 [size=64]
        I/O ports at 3040 [size=64]
        I/O ports at 3000 [size=64]
        Capabilities: <access denied>

00:01.2 RAM memory: nVidia Corporation Unknown device 0541 (rev a2)
        Flags: 66MHz, fast devsel

00:01.3 Co-processor: nVidia Corporation Unknown device 0543 (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 11
        Memory at f6200000 (32-bit, non-prefetchable) [size=512K]

00:02.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f6486000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:02.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at f6489000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:04.0 USB Controller: nVidia Corporation Unknown device 055e (rev a2) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 18
        Memory at f6487000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

00:04.1 USB Controller: nVidia Corporation Unknown device 055f (rev a2) (prog-if 20 [EHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
        Memory at f6489400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

00:06.0 IDE interface: nVidia Corporation Unknown device 0560 (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0
        [virtual] Memory at 000001f0 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 000003f0 (type 3, non-prefetchable) [disabled] [size=1]
        [virtual] Memory at 00000170 (32-bit, non-prefetchable) [disabled] [size=8]
        [virtual] Memory at 00000370 (type 3, non-prefetchable) [disabled] [size=1]
        I/O ports at 30c0 [size=16]
        Capabilities: <access denied>

00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
        Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:08.0 PCI bridge: nVidia Corporation Unknown device 0561 (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
        Memory behind bridge: f6100000-f61fffff
        Capabilities: <access denied>

00:09.0 IDE interface: nVidia Corporation Unknown device 0550 (rev a2) (prog-if 85 [Master SecO PriO])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
        I/O ports at 30f0 [size=8]
        I/O ports at 30e4 [size=4]
        I/O ports at 30e8 [size=8]
        I/O ports at 30e0 [size=4]
        I/O ports at 30d0 [size=16]
        Memory at f6484000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>

00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
        Memory at f6488000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 30f8 [size=8]
        Memory at f6489c00 (32-bit, non-prefetchable) [size=256]
        Memory at f6489800 (32-bit, non-prefetchable) [size=16]
        Capabilities: <access denied>

00:0c.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=05, sec-latency=0
        I/O behind bridge: 00004000-00004fff
        Memory behind bridge: f2000000-f3ffffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
        Capabilities: <access denied>

00:0d.0 PCI bridge: nVidia Corporation Unknown device 0563 (rev a2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Memory behind bridge: f6000000-f60fffff
        Capabilities: <access denied>

00:12.0 VGA compatible controller: nVidia Corporation Unknown device 0531 (rev a2) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 16
        Memory at f5000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Memory at f4000000 (64-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at 88000000 [disabled] [size=128K]
        Capabilities: <access denied>

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: <access denied>

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: <access denied>

02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10 [OHCI])
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 5
        Memory at f6100000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

02:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 7
        Memory at f6100800 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f6100c00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f6101000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
        Subsystem: Hewlett-Packard Company Unknown device 30cf
        Flags: bus master, medium devsel, latency 64, IRQ 11
        Memory at f6101400 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1360
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f6000000 (32-bit, no

---

### Post by csat on 2007-12-27
> **boboyo said:**
> here i pasted everything what was written when i wrote the thing in terminal

what do i do now?

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
        Subsystem: Hewlett-Packard Company Unknown device 1360
        Flags: bus master, fast devsel, latency 0, IRQ 19
        Memory at f6000000 (32-bit, no

Sorry, I should instruct you to type sudo lspci -v so that it would prevent you of getting "access denied".

Ok.  Your board is a Broadcom BCM4312.  Here you will find a nice written tutorial for this board:

[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

Meanwhile you don't have wireless connection you should put your computer to work with ethernet cable in order to download something from the above tutorial.

Good luck.

---

### Post by dalex on 2007-12-27
hi everyone:
I'm also new to ubuntu and have a similar problem with my computer. Is there a thread that talks about setting up a realtek rtl-8110sc/8169sc?
I've been working on this since the day before Christmas and can only get internet when I plug in .....

Thanks
Dalex

---

### Post by boboyo on 2007-12-28
the tuorial didnt help me alot....i still cant have wireless networking

---

### Post by csat on 2007-12-28
> **boboyo said:**
> the tuorial didnt help me alot....i still cant have wireless networking

Sorry, but did the notebook wifi light turned on or not?  If it turned on is a great advantage.  Confirming it is working now you should try a different network manager like wicd.  See it from  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/) and observe Ubuntu directions when download.

Hope this can help you out.

---

### Post by boboyo on 2007-12-28
on ubuntu, the wlan light is always orange. but on vista, its blue when its on and orange when its off.... I cant change it when im on ubuntu.

---

### Post by boboyo on 2007-12-28
csat

on the tutorial, i couldnt do it with gnome (the first option) because when i click on "run on terminal" nothing happens. I had to do it with KDE and maybe thats why it doesnt work

---

### Post by csat on 2007-12-28
> **boboyo said:**
> csat

on the tutorial, i couldnt do it with gnome (the first option) because when i click on "run on terminal" nothing happens. I had to do it with KDE and maybe thats why it doesnt work

How about the second try?  It is to download it and save it somewhere  onto your computer hard disc folder.  Have you tried?

There are several tutorials and below is another one.

[http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys](http://ubuntuforums.org/showthread.php?t=202834&highlight=linksys)

---

### Post by boboyo on 2007-12-28
it still doesnt work.

this is what i wrote and tell me whats wrong

auto lo 
iface lo inet loopback 

auto iface eth22 inet dhcp 
iface eth22 inet dhcp 
wpa-driver wext 
wpa-ssid inksys
wpa-ap scan 1 
wpa-proto wpa 
wpa-pairwise tkip 
wpa-group tkip 
wpa-key-mgmt WPA-PSK 
wpa-psk 01c9d25465ea626904f38d331c27a91617f62458e813e18bb27f2637977eefe6


i got a wpa personnal key
brodcasted ssid
and DHCP

---

### Post by boboyo on 2007-12-28
this is what is written when i get to the restart part

 * Reconfiguring network interfaces...                                          Ignoring unknown interface iface=iface.
eth22: ERROR while getting interface flags: No such device
ioctl[SIOCSIWPMKSA]: No such device
ioctl[SIOCSIWMODE]: No such device
Could not configure driver to use managed mode
ioctl[SIOCGIFFLAGS]: No such device
Could not set interface 'eth22' UP
ioctl[SIOCGIWRANGE]: No such device
ioctl[SIOCGIFINDEX]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWENCODEEXT]: No such device
ioctl[SIOCSIWENCODE]: No such device
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 7 value 0x0 - Failed to disable WPA in the driver.
ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 5 value 0x0 - ioctl[SIOCSIWAUTH]: No such device
WEXT auth param 4 value 0x0 - ioctl[SIOCSIWAP]: No such device
ioctl[SIOCGIFFLAGS]: No such device
wpa_supplicant: /sbin/wpa_supplicant daemon failed to start
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.eth22.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth22: ERROR while getting interface flags: No such device
eth22: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth22.

---

### Post by boboyo on 2007-12-28
its ok now....i replaced eth22 by eth1 and the restart part worked. but i still cant go on the internet without the cable from my router. I still cant go wireless.

---

### Post by boboyo on 2007-12-28
but now, i got another big problem

the wireless setting in network settings is not shown!

and when i try lookin for wireless networks, it doesnt work.

man ubuntu is complicated and it has alot of problems with wireless connections.

---

### Post by boboyo on 2007-12-29
anyone can help me fix this prob?

---

### Post by csat on 2007-12-29
> **boboyo said:**
> 
man ubuntu is complicated and it has alot of problems with wireless connections.

I agree... but don't give up.  Alternatively you can give a try also with linux Mint which is also based on Ubuntu.  Sometimes trying out different Linux flavors help you out to choose one distribution.

Hope you can find a way to sort it out.

Happy 2008.

---

### Post by boboyo on 2007-12-29
i dont know why but the wireless setting icon came back!:)

now theres only one thing left to do....find out how to connect to a wireless network with ubuntu

---

### Post by csat on 2007-12-29
Wireless connection is tricky and has only few things to worry about:

a) make wifi board to work;  (seems you have done);
b) configure ESSID that should match with ESSID that comes from your router;
c) configure your pass phrase that is going to authenticate you to the wifi, unless you want to run the risk of being invaded;
d) configure the network to run DHCP or static IP (in this case informing gateway address, IP number, netmask).

For all this, as I sent you before, you cant count with WICD.

You're getting there, man!!!

---

### Post by boboyo on 2007-12-29
first, what is a wifi-board?

and second, i configured the network (properly) millions of times and it just wont work with wireless. it only works when i plug the cable from my wireless router.

---

### Post by kevdog on 2007-12-29
Lets start at the beginning

Your wireless chipset is broadcom:
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
Subsystem: Hewlett-Packard Company Unknown device 1360
Flags: bus master, fast devsel, latency 0, IRQ 19
Memory at f6000000 (32-bit, no

Lets see what driver you are trying to use with this chipset. Can you post lshw -C network

For now turn off WPA on your router and lets go with no encryption.  Once we get a wireless connection, then lets turn WPA back on and work with it from there.  Lets just not skip over the basics.  Ive seen a lot of people do this, and if they are not extremely lucky, it always leads to problems.

---

### Post by cdtech on 2007-12-29
> **boboyo said:**
> ok.....

on my laptop, i paritionned my hard drive for vista and 64-bit ubuntu.

i also got wireless internet so i can go on the internet with my laptop. I got a WPA personnal thing and the connection is DHCP(no idea what it is....) when i set up my connetcion on vista, it works normally. But on ubuntu, it doesnt work. In order to be connected to the net, i have to unplug the connection cable from my pc and i have to plug iy in my laptop. When i do that, i can go on internet!

is there a way that i can go on the internet with linux without the cable?

I had the same problems with my setup and so many different recommendations on the setup procedures. I'm running an HP Pavilion DV9608 with a Turion 64x2 AMD.

This is the information that I get, running lspci at the command line:

**03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)**

and this is the tutorial that I followed to get my wireless working:

[[COLOR="DarkRed"].:: using  ndiswrapper ::.[/COLOR]]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_%28ndiswrapper%29")

I hope this helps, I know how frustrating this can be trust me, lol.

---

### Post by boboyo on 2007-12-30
thank you

ill try it

---

### Post by cdtech on 2008-01-02
Cool, let me know if that works out for you.

---

### Post by boboyo on 2008-01-03
it doestn work.

when i get to the part of cabextract, theres a thing that says E could not find package

---

### Post by boboyo on 2008-01-04
this morning, i ried to connect on my wireless thing and IT WORKED!!!!


i want to thank everyone for helping me.  

thanks alot!!

---

### Post by cdtech on 2008-01-07
Glad to hear you got it working.

---

