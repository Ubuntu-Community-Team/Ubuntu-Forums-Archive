---
title: "Help entering IP &amp; WEP"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by npergakis on 2008-10-07
I have a home network with 2 Vista based machines. I just converted one of my XP laptops to Linex It was previously linked to the network and I am trying to figue out how to get it back on line. I do know the Router/Modem IP address and WEP key, but can't figure out how or whehe to enter this info.

I would appreciate any help. Thank You :)

---

### Post by willca on 2008-10-07
Open up a terminal.

Edit this file /etc/network/interfaces

Look for the portion you have your wifi card..Typically...

auto wlan0
iface wlan0 inet dhcp
wireless-essid putithere
wireless-key puturkeyhere

Save file.

sudo /etc/init.d/networking restart

Check if its working.
sudo iwconfig
sudo iwlist wlan0 scan

---

### Post by npergakis on 2008-10-08
Thanks for the reply, but I think I am in WAY over my head.

---

### Post by superprash2003 on 2008-10-08
presuming you are planning to connect via wifi.. firstly ensure ubuntu has recognized it.. post output of iwconfig and lshw -C network from the terminal..

---

