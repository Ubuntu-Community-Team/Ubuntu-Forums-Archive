---
title: "BUFFALO Wireless-G USB 2.0 Keychain Adapter with Auto Installation"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by tyw45 on 2008-11-24
Adapter Name: WLI-U2-KG54-AL
Security: WEP64
For some reason my BUFFALO Wireless-G USB 2.0 Keychain Adapter with Auto Installation will not connect to the internet. I can also not find out the password/key thing needed to connect to the wireless network. I have software for the wireless but its for Windows. Anyone have a Linux version? It's Client Manager 3 from BUFFALO. Any help would be appreciated.

---

### Post by Ayuthia on 2008-11-24
From this [link]("http://www.linuxquestions.org/hcl/showproduct.php?product=3053&cat=all"), it looks like it might work in Ubuntu.  It should be a ralink driver so it might be rt2500usb or rt2x00usb (I am guessing because I don't have this card).  You might try to see if the module is loaded:
```
lsmod|grep rt2
```and see if one (or both) of those drivers show up in the list.  If it does not, you might try to load the rt2500usb module first:
```
sudo modprobe rt2500usb
sudo /etc/init.d/networking restart
sudo iwlist scan
```
If it returns wireless sites, then the device is working.  If not, you might try the other module:
```
sudo modprobe -r rt2500usb
sudo modprobe rt2x000usb
sudo /etc/init.d/networking restart
sudo iwlist scan
```
Hope that helps.  The commands that I have provided will only work in this session.  So don't worry if it does not work.  You can reboot and you will be back where you started.

---

