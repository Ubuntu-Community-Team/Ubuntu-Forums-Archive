---
title: "Is my ubuntu 16.10 recognized the network card and how could i connect to the wifi"
date: 2017-03-04
forum: Networking &amp; Wireless
---

### Post by delberrrrt on 2017-03-04
[COLOR=#111111][FONT=Ubuntu]when i input the ifconfig it displays:
[/FONT][/COLOR]```
lo:flags=73<uo,loopback,running> mtu 65536
inet 127.0.0.1 netmask 255.0.0.0
inet6 ::1 prefixlen 128 scopeid 0x10<host>
loop txqueuelen 1 (Local Loopback)
RX packets 22284 bytes 1337040 (1.3MB)
RX errors 0 dropped 0 overruns 0 frame 0
TX packets 22284 bytes 1337040 (1.3MB)
TX errors 0 dropped 0 overruns 0 carrier 0
```
How could I solve this problem?

---

### Post by cariboo on 2017-03-04
Could you show us the output of:

```
sudo lshw -C network
```

what you posted is not enough to go on.

---

### Post by grahammechanical on 2017-03-04
ifconfig will show network adapters (ethernet & WiFi) even when disabled by Ubuntu's Network Manager. I do not think that ifconfig will show any network adapter if it is powered off by the hardware. And that could be by a setting in the BIOS/UEFI settings utility or by a keyboard combination if it is a laptop. I do not know if it is still relevant but it used to be that if we had Microsoft Windows installed and then switched off the WiFi adapter it would remain switched off when Ubuntu was loaded

So, if the printout from ifconfig is not showing information about any network adapter then check that the adapter is properly connected and is powered on by the computer.

This is my ifconfig printout

> graham@sdb1-yakkety:~$ ifconfig
enp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.64  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::3ca5:2efc:de42:a1ba  prefixlen 64  scopeid 0x20<link>
        ether 00:1a:92:82:db:59  txqueuelen 1000  (Ethernet)
        RX packets 5729  bytes 4640724 (4.6 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 5365  bytes 620547 (620.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 17  

enp6s4: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 00:1a:92:82:d4:32  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 19  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1  (Local Loopback)
        RX packets 6043  bytes 389419 (389.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6043  bytes 389419 (389.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlx0015af0e9be0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.65  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::1c06:c6b4:395a:48b4  prefixlen 64  scopeid 0x20<link>
        ether 00:15:af:0e:9b:e0  txqueuelen 1000  (Ethernet)
        RX packets 90  bytes 5880 (5.8 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 108  bytes 12007 (12.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0



I have 2 ethernet adapters & 1 WiFi adapter. The WiFi adapter and 1 ethernet adapter are connected. They are the adapters that are listed as UP, BROADCAST, RUNNING, MULTICAST.

UP = powered on. RUNNING = connected to the router.

Regards

---

### Post by norafaithrainbow on 2017-03-05
Try using an Ethernet cord. That should work. It worked for me on the same exact distro.

---

### Post by howefield on 2017-03-05
Thread moved to the "*Networking & Wireless*" forum, probably a better fit to catch the eye of the many experts in this forum.

---

