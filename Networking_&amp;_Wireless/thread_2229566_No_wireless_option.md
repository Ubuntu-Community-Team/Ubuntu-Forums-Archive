---
title: "No wireless option"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by Mikael_Gafi on 2014-06-13
Greetings everybody, 
 I am fairly new to Ubuntu. I recently got an HP Pavilion dv2700 from a friend. The laptop works perfectly with Ethernet but there is no option for wireless anywhere. I know the problem is from the laptop because I can connect my other devices to my wireless router. My wireless card reader for this laptop is an intel wm3945abg driver. I would really appreciate some assitstance as soon as possible because I want to discover more about this laptop. Thank you to all who do

---

### Post by JeQhdMD on 2014-06-14
Well, if you installed the standard Ubuntu with Unity desktop, you should have a network icon (either fan-shaped or bars) in the panel at the screen upper right corner area (mine is just left of language selector widget).      Just click on that and you should see what wireless networks were detected (if laptop has wireless radio switch - be sure it's turned on).

Also, if you open "System Settings" (see Gear/Wrench icon in launcher).   You should then see "network" in the Hardware row.   Running the network program will then allow you to "add" a new network (SSID & Wireless Pass.) - - let the standard defaults apply unless you know otherwise.

---

### Post by squakie on 2014-06-14
You may want to see [this]("http://ubuntuforums.org/showthread.php?t=2173990") link.  The problem is the driver, a driver that steps on it, etc..   If you follow the link it may work for you.  If you have questions about the info in the link please post any such questions here and we'll try to work it out.

---

### Post by chili555 on 2014-06-19
There is a problem with the particular flavor of Ubuntu using the LXDE desktop environment, commonly called lubuntu. Please check here: [http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing](http://askubuntu.com/questions/451593/lubuntu-nm-applet-wifi-icon-missing)

In addition, we'd love to see, from the terminal:```
lspci -nn
```Thanks.

---

### Post by Mikael_Gafi on 2014-06-19
Here is the result:

negacy@apex:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14)
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

---

### Post by Mikael_Gafi on 2014-06-19
I also checked the link that you gave me, but it only added a second network manager which contained only an option for wired (ethernet) networking.

---

### Post by chili555 on 2014-06-19
I see no wireless device there at all. > My wireless card reader for this laptop is an intel wm3945abg driver.Where does this information come from?

Is it possible that the wireless device is defective or not connected properly? Many laptops have a door on the bottom where you can check for the card: [http://moderncomputerskillsandtraining.com/wp-content/uploads/2011/12/HP-dv2700-WLAN-Module.jpg](http://moderncomputerskillsandtraining.com/wp-content/uploads/2011/12/HP-dv2700-WLAN-Module.jpg)

---

### Post by slickymaster on 2014-06-19
Moved to the **Networking & Wireless** sub-forum.

---

### Post by Mikael_Gafi on 2014-06-19
Hi checked at the bottom center of my laptop and opened it up it saws wm3945abg with about 2 antennas connected to it.

---

### Post by chili555 on 2014-06-19
Is there any option in the BIOS to enable or disable the wireless?

---

### Post by Mikael_Gafi on 2014-06-19
no there is not  and I also found out that it is running GNU GRUB version 2.02~beta2-9ubuntu1.....not really sure what that means

---

### Post by chili555 on 2014-06-19
I really have no further suggestions. Unless the card appears to the operating system, the driver won't claim it and load the firmware and begin to connect and pass traffic. In this instance, as you can see from *lspci,* it doesn't appear. Here is the result from my machine:```
 03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)  
```

The driver and required firmware are installed by default in all recent Ubuntu versions.

---

### Post by Mikael_Gafi on 2014-06-19
Hello, I am having issues with Ubuntu. Wired works on my laptop but no WiFi. I am running 14.04. Thanks to all those that help. I have asked this previously with no help.

---

### Post by steeldriver on 2014-06-19
***I have merged your threads - please don't start multiple threads on the same topic***

---

### Post by Jack_Ryan on 2014-06-19
Is it a laptop pre-loaded with Ubuntu, or have you recently switched and if so was your wifi connection fine on your previous OS?

There is no icon in the top right of your desktop with arrows up/down for wireless connections?

---

### Post by Mikael_Gafi on 2014-06-20
The laptop previously ran on vista and when I got it, it was running a dual boot with Ubuntu and vista. There is an icon at the top right with arrows up/down but it only has the wired connection via Ethernet.

---

### Post by squakie on 2014-06-21
Just in case - as some old laptops used to actually internally connect the wireless to USB:

lsusb

Sorry to jump in Chili - I just wanted to add that just in case.  I'll leave well enough alone now and leave this back in your expert hands!

---

### Post by chili555 on 2014-06-21
> **squakie said:**
> Just in case - as some old laptops used to actually internally connect the wireless to USB:

lsusb

Sorry to jump in Chili - I just wanted to add that just in case.  I'll leave well enough alone now and leave this back in your expert hands!No problem. I already expressed my opinion that the device is defective.

---

### Post by wildmanne39 on 2014-06-21
I received your pm about your issue but you already have the best person helping you and if he can not fix it you need to go out a buy a new adaptor.

---

### Post by Mikael_Gafi on 2014-06-22
here is lsusb


negacy@apex:~$ lsusb
Bus 002 Device 002: ID 04f2:b016 Chicony Electronics Co., Ltd VGA 30fps UVC Webcam
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 003: ID 03f0:171d Hewlett-Packard Bluetooth 2.0 Interface [Broadcom BCM2045]
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Vladlenin5000 on 2014-06-22
> **Mikael_Gafi said:**
> Hi checked at the bottom center of my laptop and opened it up it saws wm3945abg with about 2 antennas connected to it.

Considering you can access it why not try removing and installing again? Considering the OS is unable to see your device it's either defective or loosely connected. It happened more often than not with that particular card around the time it was popular in many different laptops and re-inserting it tightly usually solved it.

If the symptom persists then other (hardware) troubleshooting is in order but for that we can't help.

---

### Post by Mikael_Gafi on 2014-06-23
Thanks I will try that

---

