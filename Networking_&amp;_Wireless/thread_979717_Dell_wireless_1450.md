---
title: "Dell wireless 1450"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by nine tails on 2008-11-12
Hi all,
I use **Ubuntu 8.10** and I can't connect internet by **dell wireless 1450**

Please help me :(
Thanks

---

### Post by Ayuthia on 2008-11-12
If you have a wired internet connection, you can go into System->Administration->Hardware Drivers and select the Broadcom (b43) driver.  If it is not there, you can install b43-fwcutter from Synaptic.

However, if you do not have a working connection, you can try this post:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

It contains the information on what to download into Ubuntu to help make it work.  Hope that helps.

---

### Post by nine tails on 2008-11-14
> **Ayuthia said:**
> **Downloading Firmware**
Both 32-bit and 64-bit:
You will still need to find someplace with a working internet connection and download the following files:
```
http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o
http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2
```
Copy those files to your home directory.  In the Terminal/Konsole/xterm window do the following:
```
cd
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
```

For those of you who are configuring your /etc/network/interfaces, you might need to do:
```
sudo /etc/init.d/networking restart
```That will restarting your network and will read through the /etc/networking/interfaces to connect.

```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```
After that, it said cannot open this file. What should I do? :(

---

### Post by Ayuthia on 2008-11-14
> **nine tails said:**
> ```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
```
After that, it said cannot open this file. What should I do? :(

It sounds like you are either not in your home directory or else the wl_apsta-3.130.20.0.o file is not in your home directory.  Does the system show the file when you do the following:
```
cd
ls wl_apsta-3.130.20.0.o
```

---

### Post by nine tails on 2008-11-15
I did it, thank you so much :D

---

