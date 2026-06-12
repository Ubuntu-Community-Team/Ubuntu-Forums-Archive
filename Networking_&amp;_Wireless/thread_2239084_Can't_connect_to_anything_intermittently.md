---
title: "Can't connect to anything intermittently"
date: 2014-08-11
forum: Networking &amp; Wireless
---

### Post by michaeljs19902 on 2014-08-11
I have had an ubuntu server running for a little over a year. Recently it it will seemingly randomly be able to connect to the rest of the network/internet. This included pinging [www.google.com](www.google.com) or 8.8.8.8 or any local IP that i know is up since I can ping it from other computers. A little background to how it's set up.

I have a dd-wrt router running as a repeater which the LAN port is hooked up to.
The computer is set as dhcp but the router is set to always hand out a static ip to it since many devices connect to it.
I can ALWAYS connect to this device from anywhere else on the network but can't ping even the gateway from the server.

Here is my conf files.

/etc/resolv.conf
```
nameserver 8.8.8.8 8.8.4.4
```

/etc/network/interfaces
```
#The loopback network interfaceauto lo
iface lo inet loopback


#The primary network interface
auto eth0
iface eth0 inet dhcp
```

I have tried setting it as static with no luck.

sudo route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         homeportal      0.0.0.0         UG    100    0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
```

sudo ip addr dev show eth0
```
eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
    link/ether d0:27:88:xx:xx:xx brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.94/24 brd 192.168.1.255 scope global eth0
    inet6 fe80::d227:88ff:fedf:672c/64 scope link 
       valid_lft forever preferred_lft forever

```

sudo ifconfig eth0
```
eth0      Link encap:Ethernet  HWaddr d0:27:88:xx:xx:xx  
          inet addr:192.168.1.94  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::d227:88ff:fedf:672c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27354 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2882256 (2.8 MB)  TX bytes:37593526 (37.5 MB)
          Interrupt:41 Base address:0xc000 

```

As i am tying this is started randomly working again.

One thing i did notice is that although i can now ping anything it is supper slow. It takes about 2 seconds in-between pings although its not showing any as dropped.

Thanks for any help. This is starting to drive me a little mad to the point of rebuilding the entire server which with all that i have set up between raid configuration and special config on the software would take 4-8 hours so not looking forward to that.

ubuntu 12.04 
3.2.0-67-generic-pae

EDIT:

I had set nameserver in resolv.conf to 192.168.1.254 to test something which is the nameserver all my other computer are using and work fine with. However after changing it to 8.8.8.8 ping is now pinging at it's normal rate.

---

### Post by michaeljs19902 on 2014-08-12
So i believe I have figured out what is wrong. I was testing some stuff when i got home today and if I assign another ip and run sudo dhclient I have internet access again. So something is going on between the repeater and the router or the router is having an issue. I am not great with networking so I will have to learn a little more before I can figure out why this is happening but I will leave this open in case someone else knows what may be causing this issue.

---

