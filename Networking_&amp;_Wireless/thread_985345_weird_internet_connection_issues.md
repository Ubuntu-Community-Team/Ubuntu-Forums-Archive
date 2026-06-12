---
title: "weird internet connection issues"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by techno91 on 2008-11-17
In the past week that I have used my Ubuntu laptop my eathernet connection is 

not working at all. well when I looked at the setting for eth0 they were all 

wrong. so I set my DNS and MAC address and assumed the problem would go away. I 

was wrong.

first the network manager refused to use the auto eth0 and instead created auto 

Ethernet. this had the orgianal bad settings. now I'm stuck on my windows box 

because that is the only this that WILL connect to the internet. 

BTW I checked the help center provided with ubuntu, and preformed the ifdown 

then ifup. sudo ifdown eth0 said the interface wasn't configured. and sudo ifup 

eth0 came up with some odd error.

If anybody can help please do. I do know quite a bit about the cmd line.

---

### Post by techno91 on 2008-11-18
Is this that rare that nobody will help?

---

### Post by superprash2003 on 2008-11-18
post output of ifconfig from your terminal

---

### Post by jamb on 2008-11-18
could you post the output of (type in a terminal)
```
cat /etc/resolv.conf
```

---

### Post by techno91 on 2008-11-19
eth0      
          Link encap:Ethernet  HWaddr 00:03:0d:12:70:bf  
          inet6 addr: fe80::203:dff:fe12:70bf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1369664 (1.3 MB)  TX bytes:24965 (24.9 KB)
          Interrupt:19 Base address:0xe800 

lo        
          Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13536 (13.5 KB)  TX bytes:13536 (13.5 KB)

wlan0     
          Link encap:Ethernet  HWaddr 00:0c:76:c9:f7:a1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:
       avahi Link encap:Ethernet  HWaddr 00:0c:76:c9:f7:a1  
          inet addr:169.254.10.85  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  
          Link encap:UNSPEC  HWaddr 00-0C-76-C9-F7-A1-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2008-11-19
well i would suggest that you try to use a static ip.. presuming that your router ip address is 192.168.1.1 .. try this [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by Jean248 on 2008-11-19
I have the same problem. I have tried to make what you suggest using a static IP address (as described in your link). But this does not work! Unfortunately!

---

### Post by techno91 on 2008-11-19
I tried the procedeure above. but the result was faliure. I'm going to post my terminal output as well. I might mention that that when I preformed Ipconfig /all to get the gateway and ip off my windows box it told me that the ip was leased out today and and would expire tomorrow. this confirms that I have a dynamic Ip Not a static one. 

the last thing is that when I made the edit to the network interfaces the congiuration file was nearly compleatly barren. I'll post that to.

```
 

heres the cinfig file

auto lo
iface lo inet loopback

and here is the terminal output

patrick@patrick-laptop:~$ sudo gedit /etc/network/interfaces
[sudo] password for patrick: 
patrick@patrick-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
patrick@patrick-laptop:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
patrick@patrick-laptop:~$ sudo ifup eth0
SIOCSIFNETMASK: Invalid argument
Failed to bring up eth0
```

---

### Post by superprash2003 on 2008-11-20
what is your router's ip address?? post your /etc/network/interfaces file here.. also post output of ifconfig

---

### Post by techno91 on 2008-11-21
ifconfig
```
eth0
Link encap:Ethernet HWaddr 00:03:0d:12:70:bf
inet6 addr: fe80::203:dff:fe12:70bf/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:22512 errors:0 dropped:0 overruns:0 frame:0
TX packets:121 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1369664 (1.3 MB) TX bytes:24965 (24.9 KB)
Interrupt:19 Base address:0xe800

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:216 errors:0 dropped:0 overruns:0 frame:0
TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:13536 (13.5 KB) TX bytes:13536 (13.5 KB)

wlan0
Link encap:Ethernet HWaddr 00:0c:76:c9:f7:a1
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0:
avahi Link encap:Ethernet HWaddr 00:0c:76:c9:f7:a1
inet addr:169.254.10.85 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1

wmaster0
Link encap:UNSPEC HWaddr 00-0C-76-C9-F7-A1-00-00-00-00-00-00-00-00-00-00
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

```

network interfaces
```
auto lo
iface lo inet loopback

```

my windows box has static DNS servers, but dynamic IP address.

---

### Post by techno91 on 2008-11-21
help?

---

### Post by superprash2003 on 2008-11-22
you dont seem to have followed that link because your /etc/network/interfaces file is almost blank and doesnt contain the static ip.. which interface is connected to the internet??

---

### Post by techno91 on 2008-11-22
actualy yes I did, but it didn't work. I thought about it and decided that the best thing to do is remove the change I made.

the interface that is connected is eth0. to be more specific it is an sis 900 mobile Ethernet card. The laptop is hooked up to a cable modem with road runner high speed internet.

my DNS servers are
208.67.220.220
208.67.222.222

Here is what I got from ipconfig all on my windows box

        Node Type . . . . . . . . . . . . : Unknown
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : tx.rr.com

Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : tx.rr.com
        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC
        Physical Address. . . . . . . . . : 00-16-76-67-0D-1D
        Dhcp Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 76.185.137.119
        Subnet Mask . . . . . . . . . . . : 255.255.240.0
        Default Gateway . . . . . . . . . : 76.185.128.1
        DHCP Server . . . . . . . . . . . : 10.5.192.1
        DNS Servers . . . . . . . . . . . : 208.67.220.220
                                            208.67.222.222
        Lease Obtained. . . . . . . . . . : Saturday, November 22, 2008 7:27:19
AM
        Lease Expires . . . . . . . . . . : Sunday, November 23, 2008 7:27:19 AM

---

### Post by techno91 on 2008-11-22
I also have thought about hooking up the internet through windows box on a wireless network. would this possibly help?

---

### Post by techno91 on 2008-11-23
bump

---

### Post by superprash2003 on 2008-11-24
well i would say , that you follow the link i gave you to setup static ip.. looking at your windows ipconfig , im sure that you need to setup static ip as those are your ISP settings.. so follow that link by adding this to the /etc/netowrk/interfaces file.Be sure to restart after that

iface eth0 inet static
address 76.185.137.119
netmask 255.255.240.0
gateway 76.185.128.1

---

### Post by techno91 on 2008-11-25
the gateway and the address changed. I've used yours and the updated code, but this ridicules.

windows uses dchp so hopefully that will mean something.

---

### Post by superprash2003 on 2008-11-28
which ubuntu version are you running?

---

