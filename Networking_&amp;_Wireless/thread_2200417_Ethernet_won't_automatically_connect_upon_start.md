---
title: "Ethernet won't automatically connect upon start"
date: 2014-01-19
forum: Networking &amp; Wireless
---

### Post by gabp on 2014-01-19
Hi,
I have apparently a simple issue but I've been so far unable to solve it. My system won't connect to the Ethernet connection automatically on start up, I have to manually click on [I]Wired Connection 1
[/I]
It is the only connection available under *Networks* and *Connect automatically *and *Available to all users* options are both checked. I've tried deleting the connection and letting it be created again, but still the same.

This started happening after I unplugged my router and connected it to another system. Before that the connection worked fine and started automatically, but after moving the router to another system and back this issue began.

My /etc/network/interfaces file reads:

auto lo
iface lo inet loopback

Disclaimer: I made a [question ]("http://askubuntu.com/questions/400929/ethernet-not-connecting-on-boot")over at askubuntu some days ago but the answer given did not help me.

---

### Post by chili555 on 2014-01-19
Sorry; I didn't respond as I wish I would have. Please see an edit back at askubuntu.

---

### Post by gabp on 2014-01-19
Hey there chili, nice to see you here too :) (and thanks for responding also here)

I just read your addendum to the solution proposed, I'll apply it and let you know here how it went (and over there too if it works)

---

### Post by gabp on 2014-01-20
Sadly it didn't work chili. The fact that it used to work fine up until I moved the router to another system and then back to mine makes me believe this is not a driver issue but a router configuration issue. Should I go back to the previous driver now? If so, how would I do this? Any other ideas for me to try?

---

### Post by Iowan on 2014-01-20
On power-up, does **ifconfig** show eth0 with an IP address?

---

### Post by gabp on 2014-01-20
This is what ifconfig shows after power-up:

```
eth0      Link encap:Ethernet  direcciónHW c8:60:00:58:07:61  
          Direc. inet:192.168.1.101  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::ca60:ff:fe58:761/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:17 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:119 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:3245 (3.2 KB)  TX bytes:15569 (15.5 KB)
          Interrupción:53 Dirección base: 0x2000 


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:275 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:275 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:21156 (21.1 KB)  TX bytes:21156 (21.1 KB)
```

and after I manually click on *Automatic wired* (I don't know what it says in english so I'll paste an image of what I have to click in order to manually connect below):

```
eth0      Link encap:Ethernet  direcciónHW c8:60:00:58:07:61  
          Direc. inet:192.168.1.101  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::ca60:ff:fe58:761/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:598 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:836 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:300343 (300.3 KB)  TX bytes:96452 (96.4 KB)
          Interrupción:53 Dirección base: 0x2000 


lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:529 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:529 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:44581 (44.5 KB)  TX bytes:44581 (44.5 KB)
```

[IMG]http://imagebin.org/index.php?mode=image&id=287787[/IMG]

---

### Post by Iowan on 2014-01-20
Well, eth0 seems to be getting an IP (from the router?).
Can you **ping** the router?
Can you **ping** internet by IP address? (try **ping 8.8.8.8**)

---

### Post by gabp on 2014-01-20
I just tried **ping 8.8.8.8** while connected and this is the output:

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=40 time=157 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=40 time=158 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=40 time=161 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=40 time=158 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=40 time=178 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=40 time=174 ms
64 bytes from 8.8.8.8: icmp_req=7 ttl=40 time=174 ms
64 bytes from 8.8.8.8: icmp_req=8 ttl=40 time=157 ms
^C
--- 8.8.8.8 ping statistics ---
8 packets transmitted, 8 received, 0% packet loss, time 7009ms
rtt min/avg/max/mdev = 157.236/164.983/178.689/8.458 ms

Should I do this right after power-up before the connection is established?

---

### Post by Iowan on 2014-01-20
Yes, sorry, I shoulda mentioned that...
(also, try **ping -c4 8.8.8.8** - it'll stop after 4 tries)

---

### Post by gabp on 2014-01-21
Pinging before the connection is established shows pretty much the same results:

PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=40 time=158 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=40 time=158 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=40 time=159 ms
64 bytes from 8.8.8.8: icmp_req=4 ttl=40 time=157 ms
64 bytes from 8.8.8.8: icmp_req=5 ttl=40 time=158 ms
64 bytes from 8.8.8.8: icmp_req=6 ttl=40 time=157 ms
^C
--- 8.8.8.8 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5008ms
rtt min/avg/max/mdev = 157.274/158.296/159.373/0.723 ms

---

