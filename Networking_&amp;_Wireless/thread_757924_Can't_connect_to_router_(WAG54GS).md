---
title: "Can't connect to router (WAG54GS)"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by frustrated chris on 2008-04-17
Hi all,
Installed ubuntu 7.10 yesterday everything went ok apart from runs very slow. I cannot connect to the router through my wired ethernet connection. I hoped it would do it automatically (DHCP is set to automatic). I have another computer running XP connected wirelessly through the same router. I am new to Linux and have spent a few hours trawling the forums to  no avail.

---

### Post by dstew on 2008-04-17
Do you also have a wireless connection on your Ubuntu machine?

---

### Post by frustrated chris on 2008-04-17
No its a pentium with 500 mb ram and ethernet connected through the motherboard.

---

### Post by dstew on 2008-04-17
> everything went ok apart from runs very slowDo you mean the desktop is slow, or that the internet connection is slow? Anyway, on a terminal command line (Applications --> Accessories --> Terminal) enter these commands:```
lspci
ifconfig
```Post the output to the forum.

---

### Post by blackjack21 on 2008-04-17
I have a thread on here today(no intenet)with the exact same problem with my 3 com router, cant get online or access the router so il moniter the replies here very closely, cant some one just post a list of the settings and show us what goes where?

---

### Post by frustrated chris on 2008-04-18
Hi folks,
Sorry for the delay. I have had to get a usb stick to paste in the code.
find below the text. Any help would be appreciated.
The keyboard and mouse also are running very slow. I have tried to speed up the mouse in the settings but this does not seem to have any effect.

Cheers chris

chris@chris-desktop:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Communication controller: Intel Corporation 536EP Data Fax Modem
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
chris@chris-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:E6:6A:44:8C  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:59 overruns:0 frame:0
          TX packets:0 errors:53 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:12 Base address:0xdc00 

eth0:avah Link encap:Ethernet  HWaddr 00:0A:E6:6A:44:8C  
          inet addr:169.254.6.225  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:12 Base address:0xdc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:45692 (44.6 KB)  TX bytes:45692 (44.6 KB)

---

### Post by dstew on 2008-04-18
This might be a bug in the driver + kernel combination. On [this thread]("http://ubuntuforums.org/showthread.php?t=522260"), a fix was to use **acpi=noirq** as a kernel parameter. You can try this kernel parameter by using the edit function on the grub menu. Instead of 'enter' to boot the kernel, press 'e'. This gives you a look at the lines in the grub menu item for that kernel. Highlight the kernel line, and press 'e' again to edit the line. At the end of the kernel line, add **acpi=noirq** and press 'enter'. Then press 'b' to boot. It this works, post back, and we can edit the /boot/grub/menu.lst file to make a permanent change. Note: this parameter might help your slowness too.

---

### Post by frustrated chris on 2008-04-18
Hi,
Unfortunately that didn't work and the keyboard and mouse are still as slow as before

---

