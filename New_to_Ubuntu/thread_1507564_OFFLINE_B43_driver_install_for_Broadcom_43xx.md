---
title: "OFFLINE B43 driver install for Broadcom 43xx"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by kingaddi on 2010-06-11
I have been following the link listed below on how to do an offline install of the broadcom proprietary drivers 

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

I am at the point where I was able to used the b43-fwcutter to successfullyextract the files from wl_apsta_mimo.o .  The extracted file are in /lib/firmware/b43.   But what do I do now???  The guide doesn't mention what to do next in order to activate the drivers.

---

### Post by sandyd on 2010-06-11
> **kingaddi said:**
> I have been following the link listed below on how to do an offline install of the broadcom proprietary drivers 

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

I am at the point where I was able to used the b43-fwcutter to successfullyextract the files from wl_apsta_mimo.o .  The extracted file are in /lib/firmware/b43.   But what do I do now???  The guide doesn't mention what to do next in order to activate the drivers.
If your using any of these cards -> BCM4311-, BCM4312-, BCM4313-, BCM4321-, and BCM4322-based hardware, just run this


32-bit
```
sudo apt-get install build-essential
mkdir bcmwl
cd bcmwl
wget -c http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_32-v5.60.48.36.tar.gz
tar xvfz *.gz
make
sudo make install
sudo modprobe wl
```restart

64bit
```
 sudo apt-get install build-essential
mkdir bcmwl
cd bcmwl
wget -c http://www.broadcom.com/docs/linux_sta/hybrid-portsrc-x86_64-v5.60.48.36.tar.gz
tar xvfz *.gz
make
sudo make install
sudo modprobe wl
```

---

### Post by kingaddi on 2010-06-11
Update:

I was able to activate the wifi with the command:

ifconfig wlan0 up


But when I check the status of the wireless networks it states:  device not ready

---

### Post by kingaddi on 2010-06-11
PROBLEM SOLVED:

I did a restart and now my wifi is 100% active

> **kingaddi said:**
> Update:

I was able to activate the wifi with the command:

ifconfig wlan0 up


But when I check the status of the wireless networks it states:  device not ready

---

