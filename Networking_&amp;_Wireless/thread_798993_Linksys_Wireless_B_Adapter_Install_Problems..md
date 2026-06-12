---
title: "Linksys Wireless B Adapter Install Problems."
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by CC440 on 2008-05-18
Hey I am new to Xubuntu and I am using it to revive an old computer for my family to use as a basic internet machine. In order to do that it needs internet. I bought and used an old Linksys WUSB11v4 adapter which worked great with windows. I have followed the very helpful guide given here, [https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Device/Linksys_WUSB11v4_(ndiswrapper)), to help me do this. 

My problem comes at step 6, I have proved that the driver works after running iwconfig but when it some to using gedit the directions lose me. It asks me to run this command and "create a record". I run the command but nothing changes, it just goes back to the driver terminal and I have no idea how to create a record or what a record really is. When I enter the record they give me to copy and paste my terminal says that the commansds wireless-key1 and auto are not found, leading me to believe I am supposed to enter this record somewhere else 

I'm sure if I can complete this step and save the file they ask me my device will work as this guide has worked perfectly so far. Can anyone help me with this terminal issue and get my adapter running?

---

### Post by chili555 on 2008-05-18
Open a terminal and do:```
sudo gedit /etc/network/interfaces
```The text editing application *gedit* will pop up with the file in it ready for you to edit to look like the HOWTO suggests. I think the HOWTO is slightly wrong. Make the file look like this:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
wireless-essid your_essid
wireless-key your_key
```Then click save and close gedit.

You are running WEP encryption, I assume? If WPA, there is a whole different process involved. Check here: [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Congratulations! You have created a record.

---

### Post by garyedwardjohnston on 2008-05-18
Firstly, my wireless cards, just worked.

Secondly, I RUN from any set of instructions like this but if you want to continue...

In terminal type:

~/wusb11/WUSB11v4_08272004/Drivers$ gksudo gedit /etc/network/interfaces

Then in the blank file copy and paste this code into it (replace the XXXX's with your WEP Key):

iface wlan0 inet dhcp
wireless-essid My_Essid
wireless-key1 XXXXXXXXXXXXXXXXXXXXXXXXXX
auto wlan0

Then save and continue with the instructions.

---

### Post by chili555 on 2008-05-18
I don't believe the 1 after wireless key is valid. If you are signifying Key #1 of four created in the router's admin pages, that's the default, so why specify what's the default. Second, according to *man iwconfig* the way to specify a key is [2], that is in brackets. That's why I said I thought the HOWTO is a bit in error.

---

