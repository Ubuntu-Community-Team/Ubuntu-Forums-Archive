---
title: "My RTL8188EU wireless USB is not working. Want to use it as backup to wired."
date: 2016-02-17
forum: Networking &amp; Wireless
---

### Post by _sluimers_ on 2016-02-17
Like the title says, I have a wired powerline network that drops from time to time and would like to use a wireless device to failsafe those moments, so I wouldn't have to deal with not having internet.

But for some reason, after working once, the thing now stays down no matter what. I don't know what's going on and would like some advice.

Below is my connection info:

```

$ ip addr
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether d0:50:99:4b:96:e1 brd ff:ff:ff:ff:ff:ff
    inet 192.168.178.53/24 brd 192.168.178.255 scope global dynamic enp2s0
       valid_lft 863603sec preferred_lft 863603sec
    inet6 fe80::d250:99ff:fe4b:96e1/64 scope link 
       valid_lft forever preferred_lft forever
3: wlx00c3e2331524: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 00:c3:e2:33:15:24 brd ff:ff:ff:ff:ff:ff
```

```

$ lsmod | grep 8188
[   28.543635] 8188eu: module verification failed: signature and/or required key missing - tainting kernel
[   28.546110] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_A_CUT_1T1R_RomVer(0)
[   28.616927] usbcore: registered new interface driver r8188eu
[   28.620360] r8188eu 1-1:1.0 wlx00c3e2331524: renamed from wlan0
[  197.446562] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
```

---

### Post by Bucky Ball on 2016-02-17
Please run the wirelessinfo script in my signature and post back the output, thanks. 

If your ethernet cable keeps dropping out, is it the cable or the router that is the problem? If it is the router, then your wireless will probably continue to drop out, even if the wireless card was working ok.

---

### Post by _sluimers_ on 2016-02-17
[http://paste.ubuntu.com/15100776/](http://paste.ubuntu.com/15100776/)

It's the powerline that's the problem.

And I would like to add that I installed docker a couple of hours ago.

---

### Post by _sluimers_ on 2016-02-21
removed from '/etc/modprobe.d/50-8188eu.conf' blacklist.

---

