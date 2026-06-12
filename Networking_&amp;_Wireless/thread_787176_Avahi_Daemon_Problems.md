---
title: "Avahi Daemon Problems"
date: 2008-05-08
forum: Networking &amp; Wireless
---

### Post by lesergi on 2008-05-08
Hi all,

I need connect to PCs in my LAN by theirs names. I know avahi helps in that function.

I have in LAN three computers but I can't connect to anyone. Three computers are running avahi-daemon.

I try this:
```
ping pc1.local
ping: unknown host pc1.local

```

The same with pc2 and pc3.

Thanks!

---

### Post by spd106 on 2008-05-08
First see if the avahi-daemon process is running.

```
:~$ ps ax | grep avahi
5300 ?        Ss     0:00 avahi-daemon: running [pc1.local]
 5301 ?        Ss     0:00 avahi-daemon: chroot helper
 7619 pts/0    R+     0:00 grep avahi

```

If that works then move on to checking that you have multicast enabled on the interface.

```
:~$ ip a
4: wlan0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:xx:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 192.168.x.x/24 brd 192.168.x.255 scope global wlan0
    inet6 fe80::211:xxff:fexx:xxxx/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by lesergi on 2008-05-08
```

sjovani@pcsjovani:~$ ps ax | grep avahi
 5446 ?        Ss     0:00 avahi-daemon: running [pcsjovani.local]
 5447 ?        Ss     0:00 avahi-daemon: chroot helper
11431 pts/2    S+     0:00 grep avahi


sjovani@pcsjovani:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:a0:d1:8d:2e:1b brd ff:ff:ff:ff:ff:ff
3: wifi0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast qlen 199
    link/ieee802.11 00:1b:9e:7b:49:98 brd ff:ff:ff:ff:ff:ff
4: ath0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue
    link/ether 00:1b:9e:7b:49:98 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.35/24 brd 192.168.1.255 scope global ath0
    inet6 fe80::21b:9eff:fe7b:4998/64 scope link
       valid_lft forever preferred_lft forever

```

The same with others PCs.

Thank you very much!!

---

### Post by lesergi on 2008-05-08
Oh!

I tried ping to Wired Lan PCs from Wifi Laptop and I didn't get ping, but I've tried from wired to wired, and I got ping!!

Why avahi from Wifi Connection does not work??

---

### Post by jringoot on 2010-07-26
Hi Iesergi,

This sounds like a configuration setting on your WiFi access-point/router.
On mine (I have a Linksys), I know that there is a setting, that means something like (I am not sure because I am not at home): WiFi client isolation.
When this set, every WiFi client is isolated from the wired LAN and has just Internet access.

You might need to go through the settings of your WiFi access-point and/or router to resolve this issue.

Best regards,

Joost

---

