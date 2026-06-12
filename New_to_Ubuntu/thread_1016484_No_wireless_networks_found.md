---
title: "No wireless networks found"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by theair on 2008-12-19
Hi! I just installed Ubuntu as a duel-boot on my laptop with Vista, and it is working beautifully, except no wireless networks are showing up in my network management tool. I was reading through the troubleshooting (I'm a complete Linux newb), and from what I can gather, I think it's a driver problem. I greatly appreciate any help in getting the driver working.

My computer: 
Toshiba Satellite A215
AMD Turion 64 X2 1.8ghz
2gb ram

Wireless device:
Atheros AR5007EG Wireless Network Adapter

---

### Post by wwusnobrdr on 2008-12-20
You can check out this wiki post but it may or may not help

[https://help.ubuntu.com/community/WifiDocs/Driver/Atheros](https://help.ubuntu.com/community/WifiDocs/Driver/Atheros)

There are various ways to get this to work and it seems with each kernel upgrade or ubuntu update it can change.  First thing I would try is disabling the built in restricted drivers ubuntu loads then reboot, sometimes it will work then.  If not...

What I found that worked for this chipset is download the compat-wireless package from here 

[http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

They have instructions but basically you have to download the file, unzip it to a directory, enter the directory and run IIRC
1. sudo make
2. sudo make install
3. sudo make unload
4. sudo make load
5. reboot

May have to blacklist ath_hal and ath_pci by adding these to the bottom of the /etc/modprobe.d/blacklist file.  But that should get you started and good luck.

---

