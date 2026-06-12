---
title: "Missing: wired connection"
date: 2016-07-22
forum: Networking &amp; Wireless
---

### Post by mune on 2016-07-22
I run Ubuntu 16.04 65 bit.

Yesterday I did some packages upgrade, after rebooting my box (without wifi) the wired connection has gone.

ifconfig says that a device named enp3s0 appeared:
```
mune@lello:~$ ifconfig 
enp3s0    Link encap:Ethernet  IndirizzoHW c0:3f:d5:96:0c:7b  
          indirizzo inet:192.168.1.2  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::c23f:d5ff:fe96:c7b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:186 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:540 (540.0 B)  Byte TX:18777 (18.7 KB)

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1224 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1 
          Byte RX:94992 (94.9 KB)  Byte TX:94992 (94.9 KB)
```


I modified the file  /etc/network/interfaces and the network manager:
```
mune@lello:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)

auto lo
iface lo inet loopback

auto enp3s0
iface enp3s0 inet static
	address 192.168.1.2
	netmask 255.255.255.0
	gateway 192.168.1.1

auto eth0
iface eth0 inet static
        address 192.168.1.2
        netmask 255.255.255.0
        gateway 192.168.1.1

dns-nameservers 192.168.1.1, 8.8.8.8, 8.8.4.4
```

[code[mune@lello:~$ nmcli con 
NOME                    UUID                                  TIPO            DEVICE 
Connessione via cavo 1  ce61c593-6c52-4d51-86ae-1562f8da7e9d  802-3-ethernet  --     
Connessione via cavo 2  0fecd2c8-cf1c-4880-bb49-fa9fee15722a  802-3-ethernet  -- [/code]

and pinging the modem isn't working (where 192.168.1.1 is my modem/router/gateway)

```
mune@lello:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.2 icmp_seq=1 Destination Host Unreachable
From 192.168.1.2 icmp_seq=2 Destination Host Unreachable
From 192.168.1.2 icmp_seq=3 Destination Host Unreachable
^C
```

I think that getting the list of the recent upgraded packages it would be possible to identify the responsable and after downgrading it revert back to wired connection.

The router and cables are ok because some other device works.

Moreover the wifi part of the router works (now I'm connected with a wifi dongle).

Googling I've found oyer got the sane problem but no 3D offered a solution.
.

---

### Post by smelheim85 on 2016-07-23
By default the name convention of network interfaces have changed in many *nix systems.  enp3s0 is now eth0 and you can change it back but that's more hassle then it's worth. Would it be possible to run a;

route -n

your interface is setup correctly so I can't see a problem.  Under thing to try is set the enp3s0 to DHCP and the restart the network service with;

sudo systemctl restart network or sudo systemctl restart network.service

---

