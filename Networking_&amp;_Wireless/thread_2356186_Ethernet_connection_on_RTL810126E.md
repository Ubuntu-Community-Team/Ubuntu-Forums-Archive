---
title: "Ethernet connection on RTL8101/2/6E"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by kleganishe on 2017-03-20
Greetings. 
Ubuntu 16.04.2
[https://paste.ubuntu.com/24217407/](https://paste.ubuntu.com/24217407/)
The point is that i can't connect to the lan with ethernet. I used NM as well as temp. terminal way (ip adr/route add). Notify says "Connection Established" just for a sec and then "Disconnected". Trying to get some info from logs (dmesg, syslog) led to nothing. There are no info about errors or fails in connections. I tried to install the official realtek dirver with kernel 8101, but nothing have changed. Help, please.
Thanks in advance.

---

### Post by praseodym on 2017-03-20
If using the NM the /etc/network/interfaces shall only show both "lo" lines:
```

echo -e "auto lo\iface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot

---

### Post by kliganishe on 2017-03-20
> **praseodym said:**
> If using the NM the /etc/network/interfaces shall only show both "lo" lines:
```

echo -e "auto lo\iface lo inet loopback" | sudo tee /etc/network/interfaces
```
Reboot
Done. But didn't help, unfortunately.
```
00:37 main :> ~ $ ip link ls enp3s0f2
2: enp3s0f2: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
    link/ether 40:16:7e:44:e0:23 brd ff:ff:ff:ff:ff:ff
00:38 main :> ~ $ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2015ms

^C00:38 main :> ~ $ tracepath 8.8.4.4
 1?: [LOCALHOST]                                         pmtu 1500
 1:  no reply
 2:  no reply
 3:  no reply
 4:  no reply
 5:  no reply
 6:  no reply
 7:  no reply

^C00:39 main :> ~ $ ping 8.8.4.4
PING 8.8.4.4 (8.8.4.4) 56(84) bytes of data.

--- 8.8.4.4 ping statistics ---
8 packets transmitted, 0 received, 100% packet loss, time 7026ms



```

---

