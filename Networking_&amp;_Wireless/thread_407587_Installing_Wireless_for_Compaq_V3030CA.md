---
title: "Installing Wireless for Compaq V3030CA"
date: 2007-04-12
forum: Networking &amp; Wireless
---

### Post by adam988 on 2007-04-12
I am having trouble getting wireless to connect...the blue light is not on very often and even when it is i do not seem to be getting any signals....any help would be greatly appreciated!


00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
03:09.1 Class 0805: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by chili555 on 2007-04-12
Here is the clue: ```
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```Here is the most likely looking solution: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

---

### Post by adam988 on 2007-04-13
it says the link does not exist....

---

### Post by chili555 on 2007-04-13
Try again. I had a little problem with the URL, which I fixed. Sorry.

---

### Post by adam988 on 2007-04-13
thanks for the quick reply...the guide seemed to be working well until i got to a certain point am now am stuck,...

Once we've got the archive file from a manufacturer, the "cabextract" tool will be required to extract the archive:

Edit the /etc/apt/sources.list and uncomment the line for the universe repository and then run apt-get update and install:

user@ubuntu:~/ndiswrapper-1.28$ gksudo gedit /etc/apt/sources.list

Find and uncomment these lines:

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

- i am new at this and so i dont know if i was just supposed to type that first line in the terminal or not but when i did i got this error...'

adam@adam-laptop:~/ndiswrapper-1.28$ gksudo gedit /etc/apt/sources.list

(gedit:7826): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
adam@adam-laptop:~/ndiswrapper-1.28$ 
adam@adam-laptop:~/ndiswrapper-1.28$ gksudo gedit /etc/apt/sources.list

(gedit:7881): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

the screen loads to change the file however it is black and i am unable to edit anything...any tips??

Thanks

---

### Post by chili555 on 2007-04-13
Please try just *sudo gedit /etc/apt/sources.list* Be sure to save before you close gedit. 'Uncomment' means, if it's not correctly explained, to remove the leading #. Later, when you become a jaded, scarred linux zombie, you will read 'comment the following' and you will know to *add* a leading #.

Post back and tell us how its going.

---

### Post by bdogg64 on 2007-04-13
> **chili555 said:**
> Here is the clue: ```
01:00.0 Network controller: Broadcom Corporation Unknown device 4311 (rev 01)
```Here is the most likely looking solution: [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper))

Here is a guide for the Broadcom 4311 using ndiswrapper

[http://www.ubuntuforums.org/showthread.php?t=346083](http://www.ubuntuforums.org/showthread.php?t=346083)

---

