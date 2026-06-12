---
title: "ethernet cable attached but not online"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by mjp29 on 2009-10-31
For some reason, this Dell laptop I just put Ubuntu on doesn't want to go online when I open Firefox.

The other computers I have put Ubuntu on just go online when connected to the dsl router via ethernet cable.

How do I tell the computer to connect to the router?

---

### Post by uberg on 2009-10-31
If you are using Gnome on the top task bar on the right had side should be a set of bars (like as in the commercial "more bars in more places" to control your network connections.  At least some basic functionality.  Hover your mouse over it.  Try right clicking it.  Try left clicking it to see it's various tools.  This is the NetworkManager Applet.

---

### Post by prshah on 2009-10-31
> **mjp29 said:**
> laptop I just put Ubuntu on doesn't want to go online when I open Firefox.

The other computers just go online when connected to the dsl router via ethernet cable.

Can you check the connectivity? Open a terminal (Applications-Accessories-Terminal) and give the command```
sudo mii-tool eth0
``` If it reports either a 10,100 or auto-negotiated connection, that is fine.

In that case, it may probably be that the new machine is not getting an IP address from the router; try this command```
sudo dhclient eth0
```.

If it still doesn't work, please post back the output from both previous commands as well as ```
cat /etc/network/interfaces
ifconfig
```

---

### Post by djotto on 2009-11-01
Not to hijack this thread, but I have the exact same problem (but I'm using an HP m7463w).  I followed the previous posters suggestions and here's what I got.

djotto00@djotto00-desktop:~$ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok
djotto00@djotto00-desktop:~$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 1947
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:17:31:35:27:88
Sending on   LPF/eth0/00:17:31:35:27:88
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
djotto00@djotto00-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

djotto00@djotto00-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:35:27:88  
          inet6 addr: fe80::217:31ff:fe35:2788/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:601 dropped:0 overruns:0 frame:601
          TX packets:111 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6840 (6.8 KB)  TX bytes:22773 (22.7 KB)

eth0:avahi Link encap:Ethernet  HWaddr 00:17:31:35:27:88  
          inet addr:169.254.5.93  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:c0:a8:b2:63:a3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:c0:a8:b2:63:a3  
          inet addr:169.254.9.226  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-C0-A8-B2-63-A3-00-00-00-00-00-00-00-00-00-00  
          UP RUNNING  MTU:0  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

- Maybe this can help get the answer for both of us?

---

### Post by mjp29 on 2009-11-01
the command Sudo mii-tool eth0 gives me this reply: eth0 no link


Your other command, I couldn't figure out how to type in because it appears you had a line break in it, but i typed "cat/etc/network/interfaces" and then typed "cat/etc/network/interfacesifconfig"  Was I suppose to type "Sudo" before that though?  Anyways, I would get a message that said something like bash ... no such file or directory

---

### Post by mjp29 on 2009-11-01
I sure hope so, because it's not much fun for either of us to use Ubuntu offline.

---

### Post by mjp29 on 2009-11-01
> **uberg said:**
> If you are using Gnome on the top task bar on the right had side should be a set of bars (like as in the commercial "more bars in more places" to control your network connections.  At least some basic functionality.  Hover your mouse over it.  Try right clicking it.  Try left clicking it to see it's various tools.  This is the NetworkManager Applet.


This computer will be given to my mother.  I can add VPN dsl and edit it.  However, it wants a username, service, and password.  My other computers don't require that when connected wired to router via ethernet cable.  Plus, I want to configure mom's email and other stuff at my house and not have this computer set to just go through my router.

---

### Post by prshah on 2009-11-01
> **djotto said:**
> $ sudo mii-tool eth0
eth0: negotiated 100baseTx-FD flow-control, link ok

djotto00@djotto00-desktop:~$ sudo dhclient eth0
No DHCPOFFERS received.

eth0      Link encap:Ethernet  HWaddr 00:17:31:35:27:88  
          inet6 addr: fe80::217:31ff:fe35:2788/64 Scope:Link


You wired link is OK, but you probably do not have a DHCP server; which means that you probably have to assign an IP and relevant network settings manually. The exact settings and steps can be recommended if you can post some details about your current network setup, preferably from a machine with a working wired network connection. If you're using Ubuntu, use ifconfig to capture the relevant information; if you're using Windows, you can use the ipconfig command.

Is your network IPv4 or IPv6? You can ignore this question if you do not know these terms.


> **mjp29 said:**
> the command Sudo mii-tool eth0 gives me this reply: eth0 no link

There you go; your wired network is not connected; check the wire, check the router/switch, check the NIC (network interface card), in that order, until mii-tool reports a similar result as above.

---

### Post by mjp29 on 2009-11-01
> **prshah said:**
> You wired link is OK, but you probably do not have a DHCP server; which means that you probably have to assign an IP and relevant network settings manually. The exact settings and steps can be recommended if you can post some details about your current network setup, preferably from a machine with a working wired network connection. If you're using Ubuntu, use ifconfig to capture the relevant information; if you're using Windows, you can use the ipconfig command.

Is your network IPv4 or IPv6? You can ignore this question if you do not know these terms.




There you go; your wired network is not connected; check the wire, check the router/switch, check the NIC (network interface card), in that order, until mii-tool reports a similar result as above.

I actually copied the exact settings into the computer that a working ubuntu wired computer has.  It would not work.

So you know what I did.

I installed the new version of Ubuntu [9.10] on half the hard drive as a partition.

Guess what, upon booting into Ubuntu 9.10, it just works and goes on the internet.

I was weary about typing in an exact i.p. address anyways, because Verizon changes my I.P. every so often and if I turn my router off for 10 seconds and turn it back on it will change the i.p. address.  Also, this computer will be given to my mom and typing in any i.p. address for myself would not work when I gave it to her.

Anyways, there have been a lot of issues with the new Ubuntu because it is new and the bugs aren't worked out yet; however, it has solved a problem for me.

I would normally mark this thread as "solved"; however, I won't because the problem wasn't solved in Ubuntu 6.10, the problem was only solved by my updated to Ubuntu 9.10.  Users out there with 6.10 may still want to read this and continue posting here concerning Ubuntu 6.10 and a Pentium 4 Desktop.

---

