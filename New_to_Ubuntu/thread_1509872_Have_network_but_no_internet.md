---
title: "Have network but no internet"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by svenoh on 2010-06-14
Hi:

I installed umbuto 9.1 on my laptop and loved it, no problem at all. 

Now I have installed on my wifes old desk top with 2 net work cards. I can see other computers on the network but can not connect to the Internet. Are the network cards having a conflict? I have the same manual settings that worked with windows.

I tried this: (maybe doing something else would have been better?)

amelia@amelia-desktop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:40:f4:58:e6:e8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=10.0.0.18 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:11 ioport:ec00(size=256) memory:dfffff00-dfffffff
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth1
       version: 74
       serial: 00:0a:e6:6b:98:37
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=half latency=32 link=no maxlatency=8 mingnt=3 multicast=yes port=MII speed=10MB/s
       resources: irq:5 ioport:d400(size=256) memory:dffffd00-dffffdff
amelia@amelia-desktop:~$


Thanks in advance

---

### Post by ubunterooster on 2010-06-14
I'm assuming your are using a wired connection?

---

### Post by svenoh on 2010-06-14
Sorry for not mentioning that. Yes, to a small office network.

Thanks

---

### Post by ubunterooster on 2010-06-14
So in places>network you can access files on other computers, yet you can not use firefox to get on line or Update manager to get updates?

is it connected directly to the router (diagram 1)or through another computer( diagram 2)? ([COLOR=Red]PC1[/COLOR] is assumed to be not working; with [COLOR=Lime]PC2[/COLOR] working)
```

   |
   |\
   |  \
   |    \
   |      \
 [COLOR=Red]PC1[/COLOR]   [COLOR=YellowGreen]PC2[/COLOR]
   \       /
    \     /
     \  /
   Router
      |
      |
      |
  Internet

```

```

[COLOR=Red]PC1[/COLOR]
  |
  |
[COLOR=Lime]PC2[/COLOR]
  |
  |
 Router
   |
   |
   |
Internet

```

---

### Post by svenoh on 2010-06-14
To a hub and then DSL router

---

### Post by Iowan on 2010-06-14
I *think* **ubunterooster** asked the same question:
To what does each card connect? eth0 shows an IP address - eth1 does not... but if both connect to the same DHCP server, that's not uncommon.

---

### Post by svenoh on 2010-06-14
Thanks for helping and as you can tell i know nothing.

the eth0 seams the only one to be working and the is the card that is connected with the wire.

---

### Post by svenoh on 2010-06-14
The eth1 is in the mother board and the eth0 an added one. Can I shut the eth1 off of shoud i try to take eth0 out?

---

### Post by ubunterooster on 2010-06-14
I would first try removing the add-in card

---

### Post by svenoh on 2010-06-14
Ok removed the secondary card and deleted that in the network manager.

Still have the same situation that I can see other computers on the net work but no Internet.

Please come with a recommenation wnat to do?

---

### Post by ubunterooster on 2010-06-14
to check to see if your are connected to the router enter the following in the terminal and paste the results: ```
ping -c 3 localhost

```

---

### Post by svenoh on 2010-06-14
amelia@amelia-desktop:~$ pingping -c 3 localhost
No command 'pingping' found, did you mean:
 Command 'pingpong' from package 'pingpong' (universe)
pingping: command not found
amelia@amelia-desktop:~$

---

### Post by svenoh on 2010-06-14
Sorry:

amelia@amelia-desktop:~$ ping -c 3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.129 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.126 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.130 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 0.126/0.128/0.130/0.009 ms
amelia@amelia-desktop:~$

---

### Post by svenoh on 2010-06-15
Does anyone else have any suggestions, this is driving me craxy?

---

### Post by CharlesA on 2010-06-15
Could you post these please:

```
ifconfig
```

```
route
```

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

---

### Post by Barrucadu on 2010-06-15
What does your /etc/resolv.conf file say, and can you ping external IPs? Like, say, 208.67.220.220.

---

### Post by doas777 on 2010-06-15
what is the output of 
```
nslookup ubuntuforums.org
```

---

### Post by svenoh on 2010-06-15
it says network unreachable

---

### Post by CharlesA on 2010-06-15
Please post the output of the commands that I have in my prevous post. :)

---

### Post by svenoh on 2010-06-15
connection timed out

---

### Post by CharlesA on 2010-06-15
> **CharlesA said:**
> Could you post these please:

```
ifconfig
```

```
route
```

```
cat /etc/resolv.conf
```

```
cat /etc/network/interfaces
```

These commands would tell you where the problem lies.

This is what they look like on my machine:

```
ubuntu@ubuntu:~$ **ifconfig**
eth0      Link encap:Ethernet  HWaddr 08:00:27:44:df:3e  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe44:df3e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:117 errors:0 dropped:0 overruns:0 frame:0
          TX packets:149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:70302 (70.3 KB)  TX bytes:16593 (16.5 KB)
          Interrupt:10 Base address:0xd020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```

```
ubuntu@ubuntu:~$ **route**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         gargoyle.asgard 0.0.0.0         UG    0      0        0 eth0
```

```
ubuntu@ubuntu:~$ **cat /etc/resolv.conf**
# Generated by NetworkManager
domain asgard.lcl
search asgard.lcl
nameserver 192.168.1.1
```

```
ubuntu@ubuntu:~$ **cat /etc/network/interfaces** 
auto lo
iface lo inet loopback
```

---

### Post by svenoh on 2010-06-15
amelia@amelia-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0a:e6:6b:98:37  
          inet addr:10.0.0.18  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe6b:9837/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:212494 (212.4 KB)  TX bytes:24791 (24.7 KB)
          Interrupt:5 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1512 (1.5 KB)  TX bytes:1512 (1.5 KB)

amelia@amelia-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     1      0        0 eth1
amelia@amelia-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
search 196.3.81.132
nameserver 196.3.81.5
amelia@amelia-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

amelia@amelia-desktop:~$

---

### Post by svenoh on 2010-06-15
I am new to this, so what does it tell you about my problem?

---

### Post by doas777 on 2010-06-15
> **svenoh said:**
> amelia@amelia-desktop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0a:e6:6b:98:37  
          inet addr:10.0.0.18  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e6ff:fe6b:9837/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2214 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:212494 (212.4 KB)  TX bytes:24791 (24.7 KB)
          Interrupt:5 Base address:0x2e00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1512 (1.5 KB)  TX bytes:1512 (1.5 KB)

amelia@amelia-desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.0        *               255.255.255.0   U     1      0        0 eth1
amelia@amelia-desktop:~$ cat /etc/resolv.conf
# Generated by NetworkManager
search 196.3.81.132
nameserver 196.3.81.5
amelia@amelia-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

amelia@amelia-desktop:~$

your issue appears to be that you don;t have a "Gateway" route defined. Do you configure your network connection yourself or do you get it automatically from a DHCP server?

---

### Post by svenoh on 2010-06-15
I use manual set up.

I have noticed that defining 10.0.0.1 as gateway it becomes blank when saving the settings.

---

### Post by CharlesA on 2010-06-15
Yah, you don't have any gateway to get out of the internal network.

Is there a reason why you set it up manually?

---

### Post by bodhi.zazen on 2010-06-15
Set a gateway

```
sudo route add default gw 192.168.1.0 eth0
```

You should now have internet, but we need to understand how and why you are setting up your network.

---

### Post by CharlesA on 2010-06-15
Going off the IP addresses in use, the gateway is probably 10.0.0.1, but I don't know for sure.

```
sudo route add default gw 10.0.0.1 eth0
```

If you've got a machine that can connect, can you post the routing table using route or ifconfig/ipconfig if it's a Windows box?

---

### Post by theozzlives on 2010-06-15
> **CharlesA said:**
> Going off the IP addresses in use, the gateway is probably 10.0.0.1, but I don't know for sure.

```
sudo route add default gw 10.0.0.1 eth0
```

If you've got a machine that can connect, can you post the routing table using route or ifconfig/ipconfig if it's a Windows box?

A Winows box would be ```
ipconfig /all
```

---

### Post by svenoh on 2010-06-15
You are right that was the problem. It is now working.

Thanks so much for your help.

I managed to set up the gateway by adding a second one .

---

### Post by doas777 on 2010-06-15
> **svenoh said:**
> I use manual set up.

I have noticed that defining 10.0.0.1 as gateway it becomes blank when saving the settings.
the entry fields in Network-Manager are sometimes really hard to work with. if you click in just the wrong place it creates a new collum/feild that has no meaning. these feilds are removed when you click off them. if you want to configure it again manually via the gui, make sure you click squarely in the center of the collum under "Gateway", and make sure that when you are done entering, that you click inside another collum to see if it sticks. if it doesn't, put it in again. 
I really hate the way they designed that UI, but hey, you work with what you have.

---

