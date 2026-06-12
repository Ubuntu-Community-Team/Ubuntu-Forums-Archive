---
title: "Networking on LAN is working but no WAN connection (not a DNS problem)"
date: 2014-09-27
forum: Networking &amp; Wireless
---

### Post by gaston1982 on 2014-09-27
Hi, I have the following network:
- Router at 192.168.2.1
- Notebook at 192.168.2.52 running Ubuntu 14.04
- Desktop at 192.168.2.37 running Ubuntu 14.04

The desktop cannot access the internet (I'm trying to ping 8.8.8.8 and I'm actually connected to the desktop from my notebook by ssh). I tried this from the desktop:
```
[B]desktop:~$ ping 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
--- 8.8.8.8 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 1006ms[/B]
**desktop:~$ ping -c 1 192.168.2.1**
PING 192.168.2.1 (192.168.2.1) 56(84) bytes of data.
64 bytes from 192.168.2.1: icmp_seq=1 ttl=64 time=2.49 ms
--- 192.168.2.1 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 2.497/2.497/2.497/0.000 ms
**desktop:~$ ping -c 1 192.168.2.52**
PING 192.168.2.52 (192.168.2.52) 56(84) bytes of data.
64 bytes from 192.168.2.52: icmp_seq=1 ttl=64 time=1.52 ms
--- 192.168.2.52 ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 1.523/1.523/1.523/0.000 ms
```

Reading other posts I've also checked:
```
**desktop:~$ ifconfig**
eth0      Link encap:Ethernet  direcciónHW 00:24:8c:77:05:42  
          Direc. inet:192.168.2.37  Difus.:192.168.2.255  Másc:255.255.255.0
          Dirección inet6: fe80::224:8cff:fe77:542/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:671 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:1435 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:68984 (68.9 KB)  TX bytes:210863 (210.8 KB)

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:65536  Métrica:1
          Paquetes RX:3837 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:3837 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:1411694 (1.4 MB)  TX bytes:1411694 (1.4 MB)
**desktop:~$ route -nv**
Tabla de rutas IP del núcleo
Destino         Pasarela        Genmask         Indic Métric Ref    Uso Interfaz
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
**desktop:~$ cat /etc/network/interfaces**
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
address 192.168.2.37
netmask 255.255.255.0
network 192.168.2.1
broadcast 192.168.2.255
gateway 192.168.2.1
dns-nameservers 192.168.2.1
[B]desktop:~$ sudo iptables -L | grep -E 'dpt:((ssh)|(http))'
desktop:~$ sudo ufw status numbered[/B]
Estado: inactivo

```

I've restarted several times /etc/init.d/networking but it doesn't seem to work. It's also strange that DHCP isn't working:
```
**desktop:~$ sudo dhclient eth0 -v**
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

So I've disabled it.
Listening on LPF/eth0/00:24:8c:77:05:42
Sending on   LPF/eth0/00:24:8c:77:05:42
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 (xid=0x51fecae)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6 (xid=0x51fecae)
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 (xid=0x51fecae)
(and keeps going)
```

While in the notebook:
```
**notebook:~$ sudo dhclient -v wlan0 **
Internet Systems Consortium DHCP Client 4.2.4
Copyright 2004-2012 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/c4:85:08:da:37:43
Sending on   LPF/wlan0/c4:85:08:da:37:43
Sending on   Socket/fallback
DHCPREQUEST of 192.168.2.52 on wlan0 to 255.255.255.255 port 67 (xid=0x17d2867)
DHCPACK of 192.168.2.52 from 192.168.2.1
RTNETLINK answers: File exists
bound to 192.168.2.52 -- renewal in 2716 seconds. to make internet work

```

So I've disabled it on the desktop. But I'm still not able to reach the WAN. Any help or suggestion?

---

