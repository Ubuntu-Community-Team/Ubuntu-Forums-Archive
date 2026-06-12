---
title: "Dlink DWL-G122 WPA"
date: 2007-08-19
forum: Networking &amp; Wireless
---

### Post by PeteZA on 2007-08-19
Hi All

I have every post that I could find on this topic (and i admit that there are quite a few of them), and for the life of me i cannot get this usb device to work. I can see my wireless network in the network manager, but it wont let me connect with WPA security. If i try to add the WPA supplicant is still does not work, i have tried serialmonkeys Rutil, but this also does not work. I am stumped, can anyone help???

Tx

---

### Post by ala.frosty on 2008-03-18
Me too. I hate posting "Me too" postings, but I've got nothing to add but frustration with trying to get this working with WPA-PSK.

---

### Post by acad1 on 2008-03-18
I am using this USB stick with Ubuntu 7.04 and WEP and it works OK, but when I loaded 7.10, I cannot get a wireless connection at all. I  am still learning about Linux, but I now think I will wait for 8.04 to see if that will work.

---

### Post by Barton101 on 2008-04-05
I have just loaded 8.04 with a DWL-G122 straight out of the box.  

All worked perfectly first time. :)

---

### Post by kevdog on 2008-04-05
Either upgrade to Hardy or Hardy's kernel since this uses the rt2x00 driver rather than the old ra driver, or see the following:

WPA with Ra Based Chipsets

Ra cards do not require the wpa_supplicant package to use WPA. Here is how to connect from the command line with these cards:
References: [http://ubuntuforums.org/showthread.p...=serial+monkey](http://ubuntuforums.org/showthread.p...=serial+monkey), [http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA](http://rt2x00.serialmonkey.com/wiki/...owto#Using_WPA)

WPA(1)
Code:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <inteface> essid "ESSID_IN_QUOTES"
sudo iwpriv <interface> set AuthMode=WPAPSK
sudo iwpriv <interface> set EncrypType=TKIP
sudo iwpriv <interface> set WPAPSK="YOUR_WPA_PSK_KEY"
sudo dhclient <interface>

For WPA(2), I have no working configuration yet. If someone would like to help me refine these instructions for WPA2 with Ra-based chipsets, I would appreciate your help!

This is borrowed from this thread:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

---

