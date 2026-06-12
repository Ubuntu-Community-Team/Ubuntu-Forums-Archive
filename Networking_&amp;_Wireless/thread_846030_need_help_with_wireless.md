---
title: "need help with wireless"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by Caveageman on 2008-07-01
hello i have got a REALTEK RTL8187b Wireless LAN Driver usb and i cant get it to register or work cuz i would love to operate in linux but i need the internet. can any one help me?

i have got the kubuntu 8.04 amd distro
althon 64 3000+ 
1.5 GB of ram

---

### Post by chili555 on 2008-07-01
Please check here: [http://ubuntuforums.org/showthread.php?t=792092](http://ubuntuforums.org/showthread.php?t=792092)

---

### Post by Caveageman on 2008-07-03
Hello but my wireless usb is the 8187. i am really confused :/

---

### Post by chili555 on 2008-07-03
I guess I'm confused, too. I thought the USB was 8187**L**, but let's ask the computer, then we'll both know:```
sudo lshw -C network
```Thanks.

---

### Post by Caveageman on 2008-07-03
what am i looking for? what do you need to see?

---

### Post by chili555 on 2008-07-03
If you can't post the whole thing, I'd love to see product, vendor, logical name and driver. Some of them may or may not be listed, in which case, it's fine to say, for example: 'driver:none shown.'

If you do this command:```
sudo lshw -C network > network.txt
```a text document will be created in your /home/username directory. You could transfer this on a thumbdrive to a computer with a working internet connection so you can post it here.

---

### Post by Caveageman on 2008-07-06
sorry for the late reply. it says loads about the ethernet interface.

then it says this 

*-network 
description: wireless interface
physical id: 1
logical name: wlan0
serial: 00:0e:2e:dc:4b:9a
capabilities: ethernet physical wireless
configuration: broadcast=yes nulticast=yes wireless=IEEE 802.11g

but as for those other things you listed nothing/not shown

---

### Post by chili555 on 2008-07-06
What does:```
sudo lsusb -v
```tell us? You can ignore the empty buses and anything not related to your wireless device.

---

### Post by Caveageman on 2008-07-08
here you go i put it into a txt file cuz it was dead long : )

---

