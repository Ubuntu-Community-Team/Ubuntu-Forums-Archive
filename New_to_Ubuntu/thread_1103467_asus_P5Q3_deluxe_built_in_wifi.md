---
title: "asus P5Q3 deluxe built in wifi"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by PhilMax on 2009-03-22
I have the above motherboard and am having trouble getting wifi to work. I have attempted to use ndiswrapper but failed. I have been able to get ndis wrapper to work on other computers so am wondering if this is an inherent problem with said motherboard and whether or not it is even possible to get the wifi to function as it does in windows? 
any help much appreciated.

Thanks

i have the linux driver but the readme has too much tech talk for me to effectivly carry out the instructions.

Thanks again.

---

### Post by halitech on 2009-03-22
could you open a terminal and post the output of
```
lspci
``` so we can see what chipset the wifi is using

---

### Post by PhilMax on 2009-03-22
phil@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 02)
00:06.0 PCI bridge: Intel Corporation 4 Series Chipset PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Device 944c
01:00.1 Audio device: ATI Technologies Inc HD48x0 audio
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
04:02.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 14)
04:03.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 70)

---

### Post by PhilMax on 2009-03-22
The driver can be found here: [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html) , it’s the RT2870USB(RT2870/RT2770). im not sure how it works though, i followed the intructions to no avail.

Thanks

---

### Post by halitech on 2009-03-22
I don't see any wireless controllers listed. Are you sure its enabled in the BIOS?

---

### Post by PhilMax on 2009-03-22
yeah it is. i use in in vista. its plugged in on usb somehow rarther than pci.
phil@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 04d9:1135 Holtek Semiconductor, Inc. 
Bus 006 Device 003: ID 046d:c312 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Cheers

---

### Post by halitech on 2009-03-22
ok, not sure why they would hook it in with usb but whatever

I found this thread which looks hopeful

[http://ubuntuforums.org/archive/index.php/t-916845.html](http://ubuntuforums.org/archive/index.php/t-916845.html)

---

### Post by PhilMax on 2009-03-22
thanks, when it says edit config.mk. what does that mean? how to i edit the file?

---

### Post by PhilMax on 2009-03-22
oh right, does it mean open in a word processor and literaly change the value?

---

### Post by halitech on 2009-03-22
thats the way I'm reading it
```
gedit /config.mk
```should do it

---

### Post by anewguy on 2009-03-22
> **PhilMax said:**
> yeah it is. i use in in vista. its plugged in on usb somehow rarther than pci.
phil@ubuntu:~$ lsusb
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0b05:1742 ASUSTek Computer, Inc. 802.11n Network Adapter
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 004: ID 04d9:1135 Holtek Semiconductor, Inc. 
Bus 006 Device 003: ID 046d:c312 Logitech, Inc. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Cheers


The wireless being connected to the USB is also showing up in some laptops.  That's why I've changed my approach to helping these type of problems to say include the output of lspci and lsusb both - it saves a post exchange if you have all of it up front.

Yes, it wants you to use an editor and manually edit the file.  you can try just using gedit - if it won't let you save then chances are it's owned by a different user - in that case just do gksudo gedit <filename>

Dave :)

---

