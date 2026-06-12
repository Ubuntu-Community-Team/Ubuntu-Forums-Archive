---
title: "Wireless issues with ndiswrapper and zd1211rw in feisty fawn"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by UrbenLegend on 2007-05-01
I have a Dell Inspiron 5100 laptop with a Belkin 54g USB network card. It currently works using the zd1211rw driver. However, the speed is stuck at 11 Mbps because the driver doesn't support automatic speed adjustments yet. How do I change the speed to 54 Mbps if I am using the Network Manager?

I also have a desktop with a Belkin BCM4306 network card. I've installed ndiswrapper and the windows driver, disabled bcm43xx, rmmod bcm43xx, and modprobed ndiswrapper, but I am unable to get it to connect to anything using the Network Manager. I was able to do this in openSUSE 10.2. Has anyone successfully gotten ndiswrapper to work with Network Manager?

Any suggestions?

---

### Post by Candace on 2007-05-05
Hi,
I am not sure what the Network Manager is (sorry I'm a newbie to Linux, and Ubuntu specifically), but I got Ndiswrapper to work with my laptop (HP, wireless card Broadcom 1390) using these links.
1. [http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505](http://ubuntuforums.org/showthread.php?t=297092&highlight=Dell+Inspiron+E1505)
2. [http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

Hope that helps.

---

### Post by bandan on 2007-05-05
> **UrbenLegend said:**
> I have a Dell Inspiron 5100 laptop with a Belkin 54g USB network card. It currently works using the zd1211rw driver. However, the speed is stuck at 11 Mbps because the driver doesn't support automatic speed adjustments yet. How do I change the speed to 54 Mbps if I am using the Network Manager?

Any suggestions?

You should have read the Documentation over at [http://www.linuxwireless.org/en/users/Drivers/zd1211rw]("http://www.linuxwireless.org/en/users/Drivers/zd1211rw"), then you would know, Automatic rate selection/management is not yet supported.

But you can set the rate manually by typing```
sudo iwconfig eth1 rate 54M
```
the 'eth1' should match your zd1211 device, and instead of 54M you can set other rates depending on your signal strength.

bandan

---

### Post by UrbenLegend on 2007-05-05
I did read the documentation and that's why I said "the driver doesn't support automatic speed adjustments yet" in my first post. :P

Does the command work even for Network Manager?

---

### Post by UrbenLegend on 2007-05-10
I've switched to ndiswrapper for my Dell inspiron 5100 with a USB network adapter. I've blacklisted zd1211rw, rmmoded it, and put ndiswrapper into my /etc/modules. However, the adapter does not work upon boot. It only works if I put the adapter in after my computer finishes booting. How do I fix this?

---

