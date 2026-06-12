---
title: "How To Install Aztech WL230USB wireless dongle"
date: 2007-02-04
forum: Networking &amp; Wireless
---

### Post by voltage on 2007-02-04
Hi,

Currently I just bought a Aztech WL230USB wireless dongle. Fortunedtly, I found that.. this device is support the linux and it's cd has supply the driver. But unfortunedtly i'm fail to install.

So do anybody have install the Aztech WL230USB wireless dongle ? PLease share with me, who are having this experiance .. 

Thanks and Good Day.
Rg,
Frank Ong

---

### Post by dhaneshr on 2007-03-25
hi Frank,

I have similar issues like you. The linux driver that is incuded on the Cd is outdated and may not work with the latest kernels. I had some success using ndiswrapper when i tested the windows driver with feisty herd 4.  It wasn't too stable at that time. 

Today, I tried Feisty Beta. Installation went fine.

# sudo ndiswrapper - i xxx.inf
# sudo depmod -a
# sudo ndiswrapper - m


Issuing ndiswrapper -l says that device is present. modprobe reveals that ndiswrapper is loaded at startup. however, there is no wireless connection present at all. only localhost.

dunno how to solve this need help




dhanesh

---

### Post by sundait on 2007-12-04
Hello..

Looks like my Aztech WL230USB dongle have similar problem too which I plugged into my Gutsy Gibbon running on VMWare. Supplied driver by manufacturer doesn't work. Currently I use zd1211rw driver, it works but it doesn't support monitor mode/rfmon. 

I need to analyze and test my own wireless system with aircrack-ng suite for vulnerability. So, how do I put this dongle in monitor/rfmon mode?  Anyone can help me out? Please.....

Sundait

---

### Post by sundait on 2007-12-08
Just ignore mine, it solved.  For Aztech WL230USB dongle user, just use zd121rw driver since it only one driver known make that dongle works pretty good for Ubuntu so far. You can download it at [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download)

---

### Post by teonghan on 2007-12-16
good day everyone.
i got an aztech wlan230usb as well and i had just install ubuntu 7.10 on my old laptop.
been trying to install the driver for the usb wireless adaptor from the installation cd but failed.
also try ndiswrapper, installation went well but when i try to configure using iwconfig, no wireless adaptor presented.
also try the guide from [http://www.linuxwireless.org/en/users/Download](http://www.linuxwireless.org/en/users/Download), again failed.
any suggestions?

---

### Post by sundait on 2007-12-17
teonghan,

did u install zd1211rw driver?

---

### Post by teonghan on 2007-12-20
well sundait, i downloaded the "compat-wireless-2.6.tar.bz2" from the website, un-tar it, cd into that folder then run make --> make install --> make unload --> make load. i'm not sure whether the zd1211rw is install by default or not? by the way, isn't the zd1211rw is bundled with any linux distribution since kernel version 2.6.18. if i'm not mistaken, kernel version in gusty is 2.6.24.

---

### Post by sundait on 2007-12-25
Teonghan, looks like your zd1211rw driver installed smoothly if you haven't recieved any error message start from running 'make' to 'make load'. The only thing I guess to be your problem is the "firmware". Try type "dmesg" in terminal console and if you get an error message such as "could not load firmware -- error line 71" or similar, then you need to install the firmware first.

For your info, I personally use this zd1211rw driver with Gutsy 2.6.22-14-generic and it works just fine..

---

### Post by teonghan on 2008-03-16
sundait,

it's been a very very long time since i last log in to ubuntuforums. been busy with my stuff. anyway, few days back i re-install my gusty 7.10 and start install those drivers from linuxwireless.org and it works, great! maybe previously i messed up with something. but now i have trouble connecting the wireless network. didn't see any icon over in the top right corner. found a guide to manual config the wireless connection somewhere here, hope it will work. thanks a lot sundait for the info!

---

