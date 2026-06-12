---
title: "HELP!!Wireless Not Working in Ubuntu-HPV6000-Broadcom 4324a"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by mijachin on 2010-05-03
ello,

   Windows is **** so im trying out this Ubuntu but i cant get the  wireless to work. The light is orange(should be blue) Ubuntu only  recognizes the wired network.I cant find a wireless device anywhere is  like is not connected... I tried lspci | grep Broadcom\ Corporation and  just lspci with results:
 
      lspci: 

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
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go  6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller  (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio  (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]  HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]  Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]  DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron]  Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro  Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev  0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host  Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev  ff


____________________________________________________
and lspci | grep Broadcom\

nothing to show

I took of the FCC label from the Broadcom card it says 4324a so im  guessing thats the model number.

Any help would really appreciate.!!!

thanks so much

mijachin

---

### Post by WinterRain on 2010-05-03
Go to system-administration-hardware drivers and activate the broadcom driver.

---

### Post by anewguy on 2010-05-03
Also, your wireless is probably connected to internal USB on your laptop, that's why it doesn't show on the PCI lists.  If you do a lsusb you will probably see it.

If you don't see a driver in System/Administration/Hardware Drivers, you'll need to do the following:


Keep the following in mind:

- if you have already attempted to install a driver using ndiswrapper, you need to completely reverse what you did first - this includes removing the entries you may have added to the blacklist.conf file, removing ndiswrapper, and then being sure to reboot.

Connect your laptop temporarily via a hard-wire cable to your router.

Do the following in a terminal window:

sudo apt-get update


When that completes, disconnect the hard-wire cable.

Check in System/Administration/Hardware Drivers and you should see a driver - enable it.

Wait a minute or two, then check to see if your wireless is now available in network manager (be sure to right-click the network manager icon and be sure the "Enable Wireless" box is checked).

Dave ;)

---

### Post by mijachin on 2010-05-04
Hey thanks for the answer,

   Unfortunately there is no such Broadcom driver under System/Administration/Hardware Drivers :( I just see NVDIA drivers for my display, the which one of them is installed. 
   I tried the sudo lsusb and this is what came up:

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


 I also tried doing the update and nothing afterwards still no driver.
i checked with ndiswrapper -l for drivers installed with it and nothing came up....

:(

---

### Post by anewguy on 2010-05-06
Looking at your lspci and lsusb output, I don't see your wireless controller.  So, how did you determine you needed to try use broadcom drivers? 

If we could see the output of:

lshw -C network

it might help us more.

Dave ;)

---

