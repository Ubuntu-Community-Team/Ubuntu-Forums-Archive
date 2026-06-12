---
title: "Knocked out my eth0 somehow"
date: 2008-07-25
forum: Networking &amp; Wireless
---

### Post by outchy on 2008-07-25
I followed the last step in this post in order to have a mount point for my samba share:

[http://ubuntuforums.org/showthread.php?t=30377](http://ubuntuforums.org/showthread.php?t=30377)

It worked, but when I tried unmounting it, my machine hung up and I rebooted.

Now, I can no longer connect to that particular share at all (but I can connect to others) and I have no more internet connection on eth0 at all, getting a 169 IP address.

When I do a "ifdown eth0", I get interface eth0 not configured.

When I do a "ifup eth0", I get "Ignoring unknown interface eth0=eth0".

I have NO idea how to fix this.  My wireless still works, but it's super slow.

I'd love to get my lan back.  Thanks for any ideas.  Running 8.04 on a Dell Inspiron 600m.

---

### Post by Endwin on 2008-07-25
Could be a couple of things but some info would help what is the contents of **/etc/network/interfaces** and **/etc/udev/rules.d/70-persistent-net.rules**

And the command **ifconfig -a**

---

### Post by outchy on 2008-07-25
> **Endwin said:**
> Could be a couple of things but some info would help what is the contents of **/etc/network/interfaces** and **/etc/udev/rules.d/70-persistent-net.rules**

And the command **ifconfig -a**
nik@nik-ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---------------------------------------

nik@nik-ubuntu:~$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x14e4:0x16a6 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0b:db:05:29:11", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x1043 (ipw2100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:04:23:4c:20:66", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

---------------------------------------

nik@nik-ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5555 errors:0 dropped:0 overruns:0 frame:0
          TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:640443 (625.4 KB)  TX bytes:55872 (54.5 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:4c:20:66  
          inet6 addr: fe80::204:23ff:fe4c:2066/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:76081 errors:2 dropped:0 overruns:0 frame:0
          TX packets:52513 errors:2 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:74517162 (71.0 MB)  TX bytes:6180823 (5.8 MB)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          inet addr:169.254.2.202  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1881 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1881 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94792 (92.5 KB)  TX bytes:94792 (92.5 KB)

---

### Post by Endwin on 2008-07-25
Looks like the problem is in your **/etc/network/interfaces** there is no config information anymore.

Edit it as root:

```
sudo nano /etc/network/interfaces
```

and add 

```

auto eth0
     iface eth0 inet dhcp

```

Restart the networking with:
```
sudo /etc/init.d/networking restart
```

See if that solves your problem.

---

### Post by outchy on 2008-07-25
> **Endwin said:**
> Looks like the problem is in your **/etc/network/interfaces** there is no config information anymore.

Edit it as root:

```
sudo nano /etc/network/interfaces
```

and add 

```

auto eth0
     iface eth0 inet dhcp

```

Restart the networking with:
```
sudo /etc/init.d/networking restart
```

See if that solves your problem.
No, that didn't work :/  Now I'm not seeing any Wired Networks when I click the icon in the taskbar:

nik@nik-ubuntu:/var/run$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                      RTNETLINK answers: No such process
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:db:05:29:11
Sending on   LPF/eth0/00:0b:db:05:29:11
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 172.16.56.1 port 67
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:db:05:29:11
Sending on   LPF/eth0/00:0b:db:05:29:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

What else can I show you that might help?

---

### Post by Endwin on 2008-07-25
Maybe I should have asked this earlier, but what is the network setup? Do you have a router with a DHCP server?

Looks like it tries to get an IP but cannot find the dhcp server. 

I was working with this common network setup:

INTERNET <=> ROUTER <=> PC

---

### Post by outchy on 2008-07-25
> **Endwin said:**
> Maybe I should have asked this earlier, but what is the network setup? Do you have a router with a DHCP server?

Looks like it tries to get an IP but cannot find the dhcp server. 

I was working with this common network setup:

INTERNET <=> ROUTER <=> PC
Not exactly, I'm in a school building and to be honest, I'm a little out of my league when it comes to the network side of things (my boss/network manager isn't in today, otherwise I'd ask him).  So I think I'm just going to back my stuff up and reinstall the entire OS.  I only installed it the other day and don't have much to lose.  But thank you very much for your help on this, I really appreciate it.

---

### Post by outchy on 2008-07-25
> **outchy said:**
> Not exactly, I'm in a school building and to be honest, I'm a little out of my league when it comes to the network side of things (my boss/network manager isn't in today, otherwise I'd ask him).  So I think I'm just going to back my stuff up and reinstall the entire OS.  I only installed it the other day and don't have much to lose.  But thank you very much for your help on this, I really appreciate it.
Eek... so I reinstalled the entire OS and my Wired Network is showing up now... but I still can't connect to the internet or the share from before.  Does that mean it's something on the server side?

---

### Post by Endwin on 2008-07-25
Perhaps a lot depends on how your network is setup. If the DHCP sever does not work then well you either need to fix it or manually put in all the info.

You said eth0 was back up. What does ifconfig give you? Can you ping the server you want to get to? If you ping [www.google.com](www.google.com) from a machine with net, copy the IP from that, and ping that IP from the computer with problems does it work?

Possible you either have a DHCP or DNS issue.

---

### Post by outchy on 2008-07-25
> **Endwin said:**
> Perhaps a lot depends on how your network is setup. If the DHCP sever does not work then well you either need to fix it or manually put in all the info.

You said eth0 was back up. What does ifconfig give you? Can you ping the server you want to get to? If you ping [www.google.com](www.google.com) from a machine with net, copy the IP from that, and ping that IP from the computer with problems does it work?

Possible you either have a DHCP or DNS issue.
DCHP is definitely working in the building... perhaps my machine got blacklisted somehow?

I can ping some servers on the network, and some I cannot.  Here is my ifconfig:

nik@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          inet6 addr: fe80::20b:dbff:fe05:2911/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2807362 (2.6 MB)  TX bytes:329503 (321.7 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:4c:20:66  
          inet6 addr: fe80::204:23ff:fe4c:2066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:432 (432.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          inet addr:169.254.2.202  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108028 (105.4 KB)  TX bytes:108028 (105.4 KB)

And I cannot ping Google's IP.  The only ones that work are some of the ones on our intranet...

---

### Post by outchy on 2008-07-25
> **outchy said:**
> DCHP is definitely working in the building... perhaps my machine got blacklisted somehow?

I can ping some servers on the network, and some I cannot.  Here is my ifconfig:

nik@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          inet6 addr: fe80::20b:dbff:fe05:2911/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3809 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2302 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2807362 (2.6 MB)  TX bytes:329503 (321.7 KB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:04:23:4c:20:66  
          inet6 addr: fe80::204:23ff:fe4c:2066/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:432 (432.0 B)
          Interrupt:5 Base address:0xe000 Memory:fafef000-fafeffff 

eth0:avahi Link encap:Ethernet  HWaddr 00:0b:db:05:29:11  
          inet addr:169.254.2.202  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2010 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2010 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:108028 (105.4 KB)  TX bytes:108028 (105.4 KB)

And I cannot ping Google's IP.  The only ones that work are some of the ones on our intranet...
And this is still the same as before...

nik@ubuntu:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by Endwin on 2008-07-25
Doing some reading /etc/network/interfaces is edited by the GUI editor not how it was in ubuntu 6.06, but something new I will have to see how it is doing it now. I wonder if you are blacklisted for some reason. Look at the firewall for the router and see if your MAC or IP address is being blocked in the logs. If you can get around on the inside but not outside something is stopping the route.

---

### Post by outchy on 2008-07-25
I figured it out (well, my friend at work did).  I gave myself a static IP on the wrong subnet... and I also assigned the same IP to both my lan and my wireless.  Oops...

So, mystery solved.  Thanks again, man.  Good looking out.

---

