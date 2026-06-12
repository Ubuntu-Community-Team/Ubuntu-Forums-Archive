---
title: "Automagically connecting wirelessly"
date: 2008-09-09
forum: Networking &amp; Wireless
---

### Post by cov on 2008-09-09
Hi,

My Wireless USB key works fine with the 'wext' driver.

The problem is that I have to run 'sudo /etc/init.d/network start' after I log into gdm.

This is not a problem for me, but it is really freaking my girlfriend out. ("Why can't it just work like Windows?")

my /etc/network/interfaces
```
auto lo
iface lo inet loopback


iface eth0 inet dhcp
wpa-psk ea00c29fa40d5d9610253a62e1aecff3d49e7079b8d50858aeeabca59c7fc156
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid whatever

auto eth0
```

Any suggestions?

---

### Post by mikewhatever on 2008-09-09
Simply add the command to startup scripts. Check out post #2 of the thread below:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by cov on 2008-09-15
> **mikewhatever said:**
> Simply add the command to startup scripts. Check out post #2 of the thread below:
[http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

Thanks.

That worked.

---

