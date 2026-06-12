---
title: "Cannot Recognize Dell Bluetooth Dongle on Ubuntu Gutsy?"
date: 2008-05-28
forum: Networking &amp; Wireless
---

### Post by DilfATX on 2008-05-28
I just received a bluetooth dongle for my mouse and keyboard.  As I understand it this dell bluetooth dongle is also supposed to do more than just connect my mouse and keyboard.  For one it has not issues connecting the keyboard and mouse to my computer running Gutsy which im using now.

I went online and have installed and tried all these

Bluez Utils
Blueman
KDE Bluetooth
Gnome Bluetooth 

and they all have the same issue.. that they don't recognize the bluetooth dongle is on.  

I tried this [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup) and after I run the terminal command to install bluez utility it says its successfuly installed and when I go to run the second command I get this

rey@rey-desktop ~ $ sudo apt-get install bluez-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez-utils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rey@rey-desktop ~ $ sudo /etc/init.d/bluez-utils restart
sudo: /etc/init.d/bluez-utils: command not found
rey@rey-desktop ~ $ 

There must be something Im doing wrong.  Can somebody please help me.  I need to get Ubuntu to recognize it has a bluetooth dongle so I can use it as such.  

Thanks guys for a great and helpful forum!

---

