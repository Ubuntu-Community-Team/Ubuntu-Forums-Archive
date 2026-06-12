---
title: "Wi-Fi doesn't work on Ubuntu 16.04"
date: 2018-01-03
forum: Networking &amp; Wireless
---

### Post by fsacado on 2018-01-03
Hey guys, having some troubles here. I just installed Ubuntu alongside my Windows 10, but it doesn't find any Wi-fi networks. I have been to Settings and Additional pilots but nothing shows up and there's an issue window. I'm kinda new to Ubuntu so I don't want to risk doing stuff on my own.
Can you please help me ?

Thank you a lot.

---

### Post by chili555 on 2018-01-03
Please start here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by fsacado on 2018-01-04
Thing is a wired connection doesn't work either ! It does recognize the ethernet cable and tries to connect to the internet, and after a minute or two it says that I'm disconnected. I've tried a few times, without any success.

---

### Post by chili555 on 2018-01-04
I suggest that you download the script on some other computer; transfer it on a USB key or similar; run it on your Ubuntu computer to gather the results; transfer it back and post it here: [http://paste.ubuntu.com](http://paste.ubuntu.com) and then give us the link.

In order to diagnose and fix your two problems, we need details.

---

### Post by chili555 on 2018-01-04
I suggest that you download the script on some other computer; transfer it on a USB key or similar; run it on your Ubuntu computer to gather the results; transfer it back and post it here: [http://paste.ubuntu.com](http://paste.ubuntu.com) and then give us the link.

In order to diagnose and fix your two problems, we need details.

---

### Post by fsacado on 2018-01-04
Thanks for your help !

There is my link : [https://paste.ubuntu.com/26321518/](https://paste.ubuntu.com/26321518/)

---

### Post by chili555 on 2018-01-04
The correct driver for your wireless is called bcmwl-kernel-source. It and its dependency dkms are found on the DVD or USB that you used to install Ubuntu. Here is how you can find and install it: [https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619](https://askubuntu.com/questions/553615/cant-enable-the-proprietary-drivers-for-broadcom-bcm43142-wireless-after-instal/553619#553619)

Very nicely done with the wireless script, by the way!

Once we have the wireless going, we'll address the ethernet.

---

### Post by fsacado on 2018-01-06
Awesome, wi-fi's working now ! Thanks. I've tried to do an sudo apt update but it's not working. Is it because everything is not set yet ?

---

### Post by chili555 on 2018-01-06
>  I've tried to do an sudo apt update but it's not working. Details! We need details. You typed in:```
sudo apt[COLOR="#FF0000"]-get[/COLOR] update
```Then you pressed Enter and then what happened? Did the terminal have any useful clues? There can be many reasons it didn't work and, in order to propose a solution, we need to know more.

Are you actually connected?```
iwconfig
```Can you ping?```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
```

---

### Post by fsacado on 2018-01-08
I'm sorry for my lack of details. Yep now it works perfectly, I didn't write the 'get', I thought it was useless nowadays. And the upgrade worked perfectly too !

---

### Post by fsacado on 2018-01-08
My Ethernet still does'nt work though, it keeps telling me that I'm disconnected.

---

### Post by chili555 on 2018-01-08
> **fsacado said:**
> My Ethernet still does'nt work though, it keeps telling me that I'm disconnected.Your ethernet device is this:> 
Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
	Subsystem: ASUSTeK Computer Inc. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [1043:200f]
	Kernel driver in use: r8169
Let's try a well-known little trick and see if it helps; if it does, we'll make it persistent. Disconnect from the wireless and hook up the ethernet cable and then:```
sudo ethtool enp2s0 speed 100 duplex full autoneg off 
```Does it connect? Are there any clues in the log?```
dmesg | grep enp
```

---

### Post by fsacado on 2018-01-08
I'll try this tomorrow when I have a cable, will let you know ;)

---

### Post by fsacado on 2018-01-09
Hello Chili555, this is not working.
When I run sudo ethtool enp2s0 speed 100 duplex full autoneg off it tells me :
```
ethtool: bad command line argument(s)
```

When running dmesg | grep enp this is what it tells me :

```

[    1.145811] r8169 0000:02:00.0 enp2s0: renamed from eth0
[   20.479788] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   20.696573] r8169 0000:02:00.0 enp2s0: link down
[   20.696627] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  162.566207] r8169 0000:02:00.0 enp2s0: link up
[  162.566222] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready


```

---

