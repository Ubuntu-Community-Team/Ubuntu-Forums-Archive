---
title: "No wifi at boot"
date: 2006-10-05
forum: Networking &amp; Wireless
---

### Post by kal on 2006-10-05
Hello,

I have some troubles with my wireless network. Indeed, everything is ok except at boot. I have to restart manually the networking service to get connected on my router :

```
 /etc/init.d/networking restart
```

This is my configuration :

**/etc/network/interfaces**

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto eth1
iface eth1 inet static
    wpa-driver wext
    wpa-ssid Tonyzio
    wpa-key-mgmt WPA-PSK
    wpa-psk "***"
    address 192.168.1.60
    netmask 255.255.255.0
    broadcast 192.168.1.255
    gateway 192.168.1.1

I don't have any **wpasupplicant.conf** file, because this one doesn't exist with the wpasupplicant version brought by drapper.

Thank you in advance :)

---

### Post by jd65pl on 2006-10-05
Are you using ndiswrapper? I know others have had some similar issues when iplementing ndiswrapper.

---

### Post by kal on 2006-10-06
No, i'm using ipw2200.

No idea ?

---

### Post by jd65pl on 2006-10-06
I don't have any experience with using this driver. But a similar issue has occured using ndiswrapper.
See [this post ]("http://ubuntuforums.org/showthread.php?t=259445")for information i'm not sure it will be relevant though.

---

