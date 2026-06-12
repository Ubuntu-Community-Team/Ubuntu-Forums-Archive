---
title: "My wireless is messed up!"
date: 2006-12-11
forum: Networking &amp; Wireless
---

### Post by ominolore on 2006-12-11
Hi everybody,
playing with ndiswrapper and network manager ('cause the system was able to detect the wireless network but wasn't able to connect to it) and particularly with /etc/network/interfaces I've completely messed up Network Manager and now the system is not detecting my wireless card any longer

I'll try to better explain: going to system > admin > network the wireless device is not present and the "enable wireless" disappeared from the network manager applet.

Here's the output of "iwconfig"
```



lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

```

Nonetheless I don't think ndiswrapper is responsible for this: the output of "ndiswrapper -l" shows things are working (driver installed, hardware present). So what's wrong?

Can anybody help me to solve this thing?
Thank you. I really don't know what to do.. ](*,) 

Here's my /etc/network/interfaces:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by FrodoB on 2006-12-11
Removing the ndiswrapper that comes with Ubuntu using apt-get remove and installing from source to the latest version usually helps a lot.

See the instructions in this post:

[http://ubuntuforums.org/showthread.php?t=315745](http://ubuntuforums.org/showthread.php?t=315745)

---

