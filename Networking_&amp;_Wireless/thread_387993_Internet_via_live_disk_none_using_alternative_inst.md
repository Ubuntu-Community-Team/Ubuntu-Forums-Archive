---
title: "Internet via live disk none using alternative install...."
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Grama777 on 2007-03-18
Hullo all first post! i love ubuntu but i would luv it more if i could figure out wut the heck has gone on with my internet connection....

about a week ago i installed ubuntu 6.10 using the desktop i386 cd (i have a p4 without 64-bit) and succesfully installed ubuntu edgy.  Loved It. However, that was on my spare harddrive to test it and so yesterday i decided i was going all out with it and make it a operating system on my current setup.  I thought this would be easy. well i was wrong.

ubuntu isn't the problem.... its my 2 other os's, xp pro (i know....) and osx86 10.4.8.   i have used boot magic for forever to boot my 2 operating systems.  well ofcourse when i tried to install using the desktop cd it didn't like me becuz it automatically installed GRUB to the MBR and GRUB does not recognize osx86.  so i booted into windoze via GRUB and renabled bootmagic and then added the linux partition.... well then i could not boot linux.  so i thought if i use the alternative install disk i can install grub to another partition.... like my ubuntu partition.  great! wellll....

this is wear the problem is.... it could not automatically detect my dhcp server and it did not auto configure my internet.  so now i have no internet and i have tried some suggestions.... u have any?  otherwise as far as i can tell linux runs perfcetly.... i just need my internet otherwise it is totally useless to me! is there a way to get it to work? is there a diference in the way the two disks install? hope u guys can help me!  thanks in advance!

Grama

---

### Post by Mr. C. on 2007-03-18
Please review this thread, and provide the information I have asked from the original poster.

[http://ubuntuforums.org/showthread.php?p=2319937#post2319937](http://ubuntuforums.org/showthread.php?p=2319937#post2319937)

MrC

---

### Post by Grama777 on 2007-03-19
ok well i will do all u said there if not tonight quickly in the morning before company comes over.... thanks tho Mr. C


Grama

---

### Post by Grama777 on 2007-03-19
ok Mr. C I have done everything except the set of commands that begin with cat /etc/... becuz it would not let me complaete them some cat no such file or directory error.

anyways, here is the other terminal out puts (the commands are all bold, italic, and underlined):

***_sudo lshw -class network_***

*-network:0 DISABLED    
       description: Ethernet interface
       product: NC100 Network Everywhere Fast Ethernet 10/100
       vendor: Linksys
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth0
       version: 11
       serial: 00:04:5a:7b:ab:69
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 multicast=yes
       resources: ioport:a000-a0ff iomemory:fc010000-fc0103ff irq:169
  *-network:1 DISABLED
       description: Ethernet interface
       product: NetXtreme BCM5705 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: d
       bus info: pci@02:0d.0
       logical name: eth1
       version: 03
       serial: 00:0c:76:44:6f:6b
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=tg3 driverversion=3.59.1 duplex=half firmware=5705-v3.14.e link=no multicast=yes port=twisted pair
       resources: iomemory:fc000000-fc00ffff irq:209

***_lspci_***

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
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 GS] (rev a1)
02:02.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
02:0d.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705 Gigabit Ethernet (rev 03)

***_lspci -n_***

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
00:1f.2 0101: 8086:24d1 (rev 02)
00:1f.3 0c05: 8086:24d3 (rev 02)
00:1f.5 0401: 8086:24d5 (rev 02)
01:00.0 0300: 10de:0047 (rev a1)
02:02.0 0200: 1317:0985 (rev 11)
02:0d.0 0200: 14e4:1653 (rev 03)

OK also i have attached the dmesg.out.gz for you



hope that helps out

Grama

---

### Post by Mr. C. on 2007-03-19
Ok, both network cards are disabled.  Go to...

System->Administration->Network

and select your Wired connection, and enable the checkbox.

See if this brings up your net.
MrC

---

### Post by Grama777 on 2007-03-19
i already did that tho...... ergh both are enabled! first thing i did to try and bring it up.

any other ideas?

---

### Post by Grama777 on 2007-03-19
oops Mr. C You were right I am posting from the ubuntu partition..... heh i feel kinda dumb now lol.... been wasting my time for a while now i guess.... o well now i know why it wasn't working! thanks a million for the help! any ideas as to why the desktop cd auto sets up the connection and the alternative does not? thanks again!

Grama

---

### Post by Mr. C. on 2007-03-19
Glad you're connected again.

I don't know why the live CD works, and the install doesn't.  I've not had that experience.  Another poster has indicated the same thing, and we're currently trying to figure it out.

MrC

---

