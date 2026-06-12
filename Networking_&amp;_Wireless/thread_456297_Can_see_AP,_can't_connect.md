---
title: "Can see AP, can't connect"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by AndyCampbell on 2007-05-27
I am using Metro Free Wi-Fi in Portland and of course it works fine on the Windows side of the box but can't connect w/Ubuntu.  I'm using a Hawking Technology Wireless-G USB Adapter (HWUG1) and in Network settings Metro Free shows up in both WLAN0 and WLANMASTER.  Configured as DHCP but still can"t connect to the internet.  The Metro Free page shows *Type: 802.11b/g Wi-Fi SSID: MetroFi-Free Security: Open*  

Not sure if the problem is Ubuntu's or Metro's.  Anyone have any experience setting up a Metro Free connection in Ubuntu 7.04?

---

### Post by handaxe on 2007-05-27
You may be falling foul of a bug (relating to the driver of your usb device viz rt73). Refer to:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/108264)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/89665)
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86980](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86980)

The solution seems to be to install serialmonkey drivers, tho' they do not support SMP (latest CVS offers SMP support!)  and PREEMPT:  [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236) also:  [http://wiki.ubuntu-it.org/RalinkRT73](http://wiki.ubuntu-it.org/RalinkRT73)  in Italian. And the following offers config method   [http://ubuntuforums.org/showthread.php?t=434952](http://ubuntuforums.org/showthread.php?t=434952)

HA

---

