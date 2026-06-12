---
title: "[SOLVED] Internet with IBM ThinkPad A22m via Nokia 5140i"
date: 2008-06-22
forum: Networking &amp; Wireless
---

### Post by 1GENNADIY1 on 2008-06-22
Helo!
Shortly had I  Internet access efficient. I have a ThinkPad A22m and Nokia 5140i, that via Infrared with Laptop effective communicated (keywords "IrDA", "FIR"; in this my thread is described: [http://forum.ubuntuusers.de/topic/157613/?highlight=](http://forum.ubuntuusers.de/topic/157613/?highlight=) (in German)). I use a German Provider ALDI Talk. Currently can I into Internet with my mobile Phone, but not with Laptop (via mobile phone). Hier is bash:
```
$ vi /etc/wvdial.conf
[Dialer Defaults]
Modem =
Phone =
Username =
Password =
New PPPD = yes

[Dialer mm]
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
#Init3 = AT+CGDCONT=1,"IP","internet.eplus.de", "0.0.0.0",
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ircomm0
ISDN = 0
Phone = *99#
Password = "eplus"
Username = "gprs"
DNS Test1 = www.yahoo.de
~ 
```                              
I start wvdial with script (bash):
```
[sudo] password for gennadiyupt:
WvDial<*1>: WvDial: Internet dialer version 1.56
WvDial<Warn>: Warning: section [Dialer n] does not exist in wvdial.conf.
WvDial<*1>: Initializing modem.
WvDial<*1>: Sending: ATZ
WvDial Modem<*1>: ATZ
WvDial Modem<*1>: OK
WvDial<*1>: Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
WvDial Modem<*1>: OK
WvDial<*1>: Modem initialized.
WvDial<*1>: Sending: ATDT*99#
WvDial<*1>: Waiting for carrier.
WvDial Modem<*1>: ATDT*99#
WvDial Modem<*1>: CONNECT
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: Carrier detected.  Waiting for prompt.
WvDial Modem<*1>: ~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
WvDial<*1>: PPP negotiation detected.
WvDial<Notice>: Starting pppd at Sun May 25 05:43:50 2008
WvDial<Notice>: Pid of pppd: 6632
WvDial<*1>: Using interface ppp0
WvDial<*1>: local  IP address 10.128.88.202
WvDial<*1>: remote IP address 10.6.6.6
WvDial<*1>: primary   DNS address 212.23.97.2
WvDial<*1>: secondary DNS address 212.23.97.3
....
(cursor blinks)
```
If I ubunuuser.de ping:
```
:~$ ping -c 4 213.95.41.11
PING 213.95.41.11 (213.95.41.11) 56(84) bytes of data.
	
--- 213.95.41.11 ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3009ms
```
Soever Firefox detects none ;-(

Here another relevant data:
```
:~$ lspci | grep -i net
:~$ lsusb
Bus 001 Device 001: ID 0000:0000
:~$ egrep -v "^$|^#" /etc/network/interfaces
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
iface ppp0 inet ppp
1provider ppp0
:~$ egrep -v "^$|^#" /etc/resolv.conf
nameserver 212.23.97.2
nameserver 212.23.97.3
:~$ egrep -v "^$|^#" /etc/hosts
127.0.0.1 localhost
127.0.1.1 gutsy.meindomain.mein gutsy
192.168.178.20 gena.meindomain.mein gena
192.168.178.21 squid.meindomain.mein squid
192.168.178.24 alla.meindomain.mein alla
192.168.178.25 gutsy.meindomain.mein gutsy
:~$ ifconfig 
irda0     Protokoll:IrLAP  Hardware Adresse fb:83:ec:62  
          UP RUNNING NOARP  MTU:2048  Metric:1
          RX packets:591 errors:0 dropped:0 overruns:0 frame:0
          TX packets:380304 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:8 
          RX bytes:3260 (3.1 KB)  TX bytes:11808685 (11.2 MB)

lo        Protokoll:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6 Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1991 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:90458 (88.3 KB)  TX bytes:90458 (88.3 KB)

ppp0      Protokoll:Punkt-zu-Punkt Verbindung  
          inet Adresse:10.128.218.60  P-z-P:10.6.6.6  Maske:255.255.255.255
          UP PUNKTZUPUNKT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:3 
          RX bytes:64 (64.0 b)  TX bytes:97 (97.0 b)
:~$ route -n
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
10.6.6.6        0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

:~$ /sbin/route
Kernel IP Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
10.6.6.6        *               255.255.255.255 UH    0      0        0 ppp0
default         *               0.0.0.0         U     0      0        0 ppp0
```
I hope, this make be possible to help me.
Thank you!
Gena

---

### Post by 1GENNADIY1 on 2008-06-28
Helo!
I have my problem resolved. It was due to false configuration of wvdial. Efficient configuration is as following:
```
$ vi /etc/wvdial.conf
```
```
[Dialer Defaults]
Modem =
Phone =
Username =
Password =
New PPPD = yes

[Dialer mm]
#Init1 = ATZ
#Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
Init3 = AT+CGDCONT=1,"IP","internet.eplus.de", "0.0.0.0",
Modem Type = USB Modem
Baud = 460800
New PPPD = yes
Modem = /dev/ircomm0
ISDN = 0
Phone = *99#
Password = "eplus"
Username = "gprs"
DNS Test1 = 212.23.97.2
DNS Test2 = 212.23.97.3
```
```
:~$ ping yahoo.de
PING yahoo.de (217.146.186.221) 56(84) bytes of data.
64 bytes from rc1.vip.ird.yahoo.com (217.146.186.221): icmp_seq=1 ttl=48 time=840 ms
64 bytes from rc1.vip.ird.yahoo.com (217.146.186.221): icmp_seq=2 ttl=48 time=729 ms
64 bytes from rc1.vip.ird.yahoo.com (217.146.186.221): icmp_seq=3 ttl=48 time=735 ms
64 bytes from rc1.vip.ird.yahoo.com (217.146.186.221): icmp_seq=4 ttl=48 time=734 ms

--- yahoo.de ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 4890ms
rtt min/avg/max/mdev = 729.815/760.166/840.838/46.628 ms 
```
Anyway Thank you!:)

---

