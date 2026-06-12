---
title: "[SOLVED] belkin"
date: 2007-08-12
forum: Networking &amp; Wireless
---

### Post by touchq on 2007-08-12
Dear all, I am new to Linux and ubuntu. I have got a Belkin  Wireless G **USB** Network Adapter. I think the product model is: **F5D7050** 

I am using ubuntu 7.04. I tried to play with the network settings through: System>Administration>Network. After trying many things randomly, still no wireless connection. I am using Belkin router, the wired connection works! I have disabled the WEP security in the router.

I only have driver for Windows XP.  I have looked at this link ([https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)) and plug in the usb adaptor and type:** lsusb -v | less**
Got following in terminal:
Bus 003 Device 006: ID 050d:705a Belkin Components 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x050d Belkin Components
  idProduct          0x705a 
  bcdDevice            0.01
  iManufacturer           1 
  iProduct                2 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           32
    bNumInterfaces          1
    bConfigurationValue     1

Can Anybody help me to setup the wireless connection? Does my belkin Wireless G USB Network Adapter supported in Ubuntu 7.04? Thank you very much!

By the way the belkin web site ([www.belkin.com](www.belkin.com)) doesn't work! Since I tried to see if I can find any driver for linux.

---

### Post by AndyCooll on 2007-08-12
First of all you need to find out what chipset your USB dongle uses.

I have some of these though I haven't used them for awhile (I think I last used them in Breezy). IIRC at the time it required installing the Ralink RT2570 driver and I used this howto:[ HOWTO: Ralink RT2570 usb wireless driver]("http://ubuntuforums.org/showthread.php?t=106846")

You probably won't need all that since the RT2570 driver has now been incorporated into the kernel. In which case you'll only need the section which shows you how to manually setup the network interfaces file.

I also have a couple of Belkin PCMCIA cards which also use the RT2570 driver and these work fine. However I bought a third PCMCIA card and even though it has the same name it uses a different chipset (RT61) and this has proved more tricky to setup. So as I mentioned at the beginning, check the chipset your USB dongle uses first.

:cool:

---

### Post by touchq on 2007-08-12
Thanks for reply. After post the question, I searched the forum and found one:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
(Thank you)

I follow the advices there and lucky i am, it works after a few hours trying! The driver was installed flawlessly. And i think the adapter was detected. But there is one strange thing when I tried to make the connection by:

sudo ifconfig wlan1
sudo iwconfig wlan1 essid belkin54g
sudo iwconfig wlan1 key "off"

sudo dhclient wlan1

The first three lines works fine, but there is always problem with last line, UNLESS I unplug the adapter and plug in again. 


> **AndyCooll said:**
> First of all you need to find out what chipset your USB dongle uses.

I have some of these though I haven't used them for awhile (I think I last used them in Breezy). IIRC at the time it required installing the Ralink RT2570 driver and I used this howto:[ HOWTO: Ralink RT2570 usb wireless driver]("http://ubuntuforums.org/showthread.php?t=106846")

You probably won't need all that since the RT2570 driver has now been incorporated into the kernel. In which case you'll only need the section which shows you how to manually setup the network interfaces file.

I also have a couple of Belkin PCMCIA cards which also use the RT2570 driver and these work fine. However I bought a third PCMCIA card and even though it has the same name it uses a different chipset (RT61) and this has proved more tricky to setup. So as I mentioned at the beginning, check the chipset your USB dongle uses first.

:cool:

---

### Post by Austin_KW on 2007-08-12
> **touchq said:**
> Thanks for reply. After post the question, I searched the forum and found one:
[http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)
(Thank you)

I follow the advices there and lucky i am, it works after a few hours trying! The driver was installed flawlessly. And i think the adapter was detected. But there is one strange thing when I tried to make the connection by:

sudo ifconfig wlan1
sudo iwconfig wlan1 essid belkin54g
sudo iwconfig wlan1 key "off"

sudo dhclient wlan1

The first three lines works fine, but there is always problem with last line, UNLESS I unplug the adapter and plug in again.

I have the same adapter (belkin 7050 v3000 rt73) and also see problems sometimes. Removing and reinserting usually fixes it. Check the output from "dmesg", I usually see problems with the usb probe function or the firmware load so it is probably some race condition on boot and usb init but I have not found a reliable way of fixing it.

---

### Post by touchq on 2008-05-27
My same USB wireless adapter works perfectly well in 8.04 (hardy) now, without any tweaks. Only thing needs to do is setting the hex encryption in network manager.

---

