---
title: "linksys wireless usb help (v3)"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by yanq on 2009-07-01
i am a complete newbie & am just looking to use ubuntu for one specific reason at the moment, though i'd like to gradually get it working properly. i don't specfically need internet right now but it would make the process a lot easier.  i'm only just reading about software installation & it sounds pretty vital.  i'm trying to get my wireless connection working & it won't detect my usb.  i've read some instructions here but they're gobbledeegook to me & seem to presuppose i have some other way of connecting.

---

### Post by Michael.Godawski on 2009-07-01
hey,

can you please post some more info. Open up the Terminal
Applications > Accessories > Terminal
run these commands, and post the outputs here.

```
lspci
lsusb
sudo lshw -C network
```

The last commands requires your login password, which won't be displayed while you type it in.

---

### Post by yanq on 2009-07-01
thanks michael, but... (i did stress that i'm a newbie & slightly retarded right?)

i pasted the output to the text editor & saved it under both formats to my windows folder but of course windows can't read the files.  i don't know if ubuntu comes w/ a compliant software or not.  i'll reboot into ubuntu again & check around...i'm basically just trying to get wine & this wireless working right now, baby steps etc. 

i'm sort of cycling back & forth b/w ubuntu & windows so i'll post this now then update

---

### Post by Michael.Godawski on 2009-07-01
Sure. No sweat! ;) A trivial txt file should do it. 
I know exactly how you feel. It reminds me of my dual-booting times...

---

### Post by yanq on 2009-07-01
ok, here it is--

john@john-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)
02:00.0 Audio device: Creative Labs [X-Fi Titanium series] EMU20k2 (rev 03)
04:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4850]
04:00.1 Audio device: ATI Technologies Inc HD48x0 audio
john@john-desktop:~$ lsusb
Bus 002 Device 003: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 058f:9410 Alcor Micro Corp. Keyboard
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1737:0077 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@john-desktop:~$ sudo lshw -C network
[sudo] password for john: 
  *-network               
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:4b:26:82
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=0.9-2 latency=0 link=no module=e1000e multicast=yes port=twisted pair
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 8a:bc:ec:bf:8a:d8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
john@john-desktop:~$

---

### Post by Michael.Godawski on 2009-07-01
OK. What I want to find out is the chipset of the USB thingy. The output was not that informative concerning this question. 

Might be obvious but have you tried to click on the network icon in the right upper corner and choose your network? (You surely have..)

We might end up using a special application called ndiswrapper which uses the Windows drivers to make the usb thing run.

---

### Post by yanq on 2009-07-01
i did try choose network, but none were displayed. i'll dink around a little more.

---

