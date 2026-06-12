---
title: "wpa_supplicant: ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported"
date: 2007-08-23
forum: Networking &amp; Wireless
---

### Post by blueberries on 2007-08-23
hey,

i tried to follow [this]("https://help.ubuntu.com/community/WifiDocs/WPAHowTo") howto, and got stuck at "testing the configurations" under wpa_supplicant.

lea@lea-laptop:~$  sudo wpa_supplicant -iwifi0 -c/etc/wpa_supplicant.conf -Dhostap -w
Password:
ioctl[PRISM2_IOCTL_PRISM2_PARAM]: Operation not supported

what does it means? what can i do?

thanks!

---

### Post by watkipet on 2008-03-30
I'm having the same problem. As far as I can tell, wpa_supplicant doesn't work with hostap in Ubuntu.

---

### Post by kevdog on 2008-03-30
Check the syntax
lea@lea-laptop:~$ sudo wpa_supplicant -iwifi0 -c/etc/wpa_supplicant.conf -Dhostap -w

It is my bet the the wifi0 is an incorrect parameter -- likely another interface should be used.  Confirm the interface name with ifconfig

---

### Post by watkipet on 2008-03-30
Ah. Could be. In my case however, the device in my wpa_supplicant command matches the device shown by lshw:

```

*-network
   description: Wireless interface
   physical id: 2
   logical name: wlan0_rename
   serial: 00:06:25:16:b2:c4
   capabilities: ethernet physical wireless
   configuration: broadcast=yes driver=hostap driverversion=0.4.4-kernel firmware=1.4.2 multicast=yes wireless=IEEE 802.11b

```

```

wpa_supplicant -w -Dhostap -iwlan0_rename -c/etc/wpa_supplicant.conf

```


Like some other people, Ubuntu freezes if I leave my wireless card in at startup so I have to insert it after I start up. This morning when I left it in I found this error:

```
Unknown interrupt or fault at EIP 00000283 00000060 c0201658
```

---

