---
title: "lan network issue"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by superazo on 2008-11-15
Please help I am on ubuntu 8.10 for about one week and i managed to Configure my lan network on  my college I just plug in network cable from my laptop-pc to one of lan ports and it works great but when I try to plug the Cable in some other port it does not work.

Problem is that I am not availible to plug my cable in same port every time becouse they are taken from some other guys.

So please help!!! The network is student campus type, it also requires authenthication on windows (securew2) but on ubuntu it works without it:)

---

### Post by ub007 on 2008-11-15
The post lacks clarity.Are you trying to connect to the internet through uni n/w ,or you only are connecting to the uni intranet?


Anyways,if you aint getting connected when plugged into a different port ,try this

> $sudo /etc/init.d/networking restart

---

### Post by superazo on 2008-11-15
> **ub007 said:**
> The post lacks clarity.Are you trying to connect to the internet through uni n/w ,or you only are connecting to the uni intranet?


Anyways,if you aint getting connected when plugged into a different port ,try this

I am sorry I am from non english country.
And I am sorry if my english is bad.
 
I am connecting to internet through lan network.

also i had configured wpa_supplicant and it works on ubuntu 8.04 but now it is ittle funny it works only at 1 port

---

### Post by superazo on 2008-11-15
$sudo /etc/init.d/networking restart 

I try it and nothing!
So help please.

---

### Post by puppywhacker on 2008-11-15
hi

wpa_supplicant is for wireless connections, but you said you connect to a LAN port with a cable. To me it sounds like your network card should ask for the network configurations using DHCP 

can you either post your ifconfig or look at "System" "Preferences" "Network Configuration" "Wired" "ifdownup (eth0)" "IPv4 Settings" usually the method should be "Automatic (DHCP)"

I agree with ub007 there is not much information to help you with, perhaps you can ask a local guy to help?

P.S. Your English is fine, we understand you perfectly =)

goodluck

---

### Post by iponeverything on 2008-11-15
Perhaps that windows authentication application that you mentioned, is setting up MAC filtering and because the port that you like to plug into has a slightly different configuration than the rest -- you can bypass the filter when connected to that port.

---

### Post by superazo on 2008-11-15
> **puppywhacker said:**
> hi

wpa_supplicant is for wireless connections, but you said you connect to a LAN port with a cable. To me it sounds like your network card should ask for the network configurations using DHCP 

can you either post your ifconfig or look at "System" "Preferences" "Network Configuration" "Wired" "ifdownup (eth0)" "IPv4 Settings" usually the method should be "Automatic (DHCP)"

I agree with ub007 there is not much information to help you with, perhaps you can ask a local guy to help?

P.S. Your English is fine, we understand you perfectly =)

goodluck

dhcp is set to automatic.
and My wirelles works without wpa_supplicant I write my username and pass which i get from college.
but lan does not, just one port, my problem is to set it to work on all ports.

---

### Post by superazo on 2008-11-15
> **iponeverything said:**
> Perhaps that windows authentication application that you mentioned, is setting up MAC filtering and because the port that you like to plug into has a slightly different configuration than the rest -- you can bypass the filter when connected to that port.
How to bypass the filter?
So if  I manage to bypass that filter then i could connect to everyone port on my college?

---

### Post by ub007 on 2008-11-15
mate,plz post the output of ifconfig & vi /etc/network/interfaces

---

### Post by superazo on 2008-11-16
> **ub007 said:**
> mate,plz post the output of ifconfig & vi /etc/network/interfaces
 here it is:[IFCONFIG]
eth0      Link encap:Ethernet  HWaddr 00:1e:33:49:79:64  
          inet addr:172.21.1.199  Bcast:172.21.1.255  Mask:255.255.254.0
          inet6 addr: fe80::21e:33ff:fe49:7964/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3188 errors:0 dropped:2895322261 overruns:0 frame:0
          TX packets:2853 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3396572 (3.3 MB)  TX bytes:516250 (516.2 KB)
          Interrupt:220 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:246 errors:0 dropped:0 overruns:0 frame:0
          TX packets:246 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:15416 (15.4 KB)  TX bytes:15416 (15.4 KB)

and vi /etc/network/interfaces:
auto lo
iface lo inet loopback

---

### Post by ub007 on 2008-11-16
You havent made the configuration to accept IP through DHCP.

Edit /etc/network/interfaces to read

vi /etc/network/interfaces:

> auto eth0
iface eth0 inet dhcp

After that you need to do


> $sudo /etc/init.d/networking restart 

---

### Post by superazo on 2008-11-16
> **ub007 said:**
> You havent made the configuration to accept IP through DHCP.

Edit /etc/network/interfaces to read

vi /etc/network/interfaces:



After that you need to do

And this should fix my issue?
Anyway tnx a lot.

---

### Post by ub007 on 2008-11-16
> And this should fix my issue?
Anyway tnx a lot.

Why dont you try that out and come back with your results...

---

### Post by Iowan on 2008-11-16
You can use **nano** as an editor (if you prefer) - or even **gedit**. Either way, you'll need to use **sudo** (or **gksudo**).
**sudo nano /etc/network/interfaces** or 
**gksudo gedit/etc/network/interfaces**.

---

### Post by superazo on 2008-11-27
> **ub007 said:**
> Why dont you try that out and come back with your results...

thnx a lot m8 this works

---

