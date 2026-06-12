---
title: "Unable to setup static ip"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by newtolinux1986 on 2007-06-05
Hello everyone,

I m unable to setup static ip on my comp.I have browsed through many websites which suggested to edit the file  /etc/network/interfaces...  I m using Ubuntu  version 7.04..  

My required settings are:

Required IP  to be setup :192.168.1.136
Gateway:192.168.1.1
DNS server :61.1.96.69
Alternate DNS server :61.1.96.71


My  current  /etc/network/interfaces looks as below::

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


 PLS tell me the changes that are required..THANX

---

### Post by bmeyer on 2007-06-05
> **newtolinux1986 said:**
> 
Required IP  to be setup :192.168.1.136
Gateway:192.168.1.1
DNS server :61.1.96.69
Alternate DNS server :61.1.96.71


Add this to the bottom of that file.  Replace "wlan0" with the name of your wireless interface.  Replace <my ESSIS> with your essid.

iface wlan0 inet static
wireless-essid <my ESSID>
address 192.168.1.136
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 61.1.96.69 61.1.96.71

Does your router use encryption (WEP, WPA)?  We'll need to add that if it does.
You can get this to start automatically when your computer reboots, but I forget how to do it.  When I turn my computer on, I type the following in the terminal to get this connection running:
sudo ifup wlan0

Remember to replace wlan0 with your interface name.

---

### Post by turinglabs on 2007-06-05
Use system->administration->network for a graphical utility to do this. If you want to edit the interfaces file, it would look like this (assuming eth1 is the static one):

auto eth1
iface eth1 static
    address 192.168.1.136
    gateway 192.168.1.1
    netmask 255.255.255.0 (or whatever you netmask is)
   
Then do sudo ifdown eth1; sudo ifup eth1

There are some other examples in /usr/share/doc/ifupdown/examples/network-interfaces.gz. Global DNS settings can be put in /etc/resolv.conf like this:

nameserver 61.1.96.69
nameserver 61.1.96.71

If you have the resolvconf package installed, and want to assign per-interface DNS servers, you can add 'dns-nameservers' line to the interface stanza, but this is not needed if you have a set of DNS servers you want to use all the time.

---

### Post by kevdog on 2007-06-05
Hold on for just a second.  

What interface name are you trying to configure, eth0, wlan0, or something else?????

Please post the results of:
ifconfig

so that we can see the interfaces you have.  That way we can delete some of this superfluous info in the interfaces file.

---

### Post by jamesford on 2007-06-05
try sudo /etc/init.d/networking restart

---

### Post by newtolinux1986 on 2007-06-05
> **kevdog said:**
> Hold on for just a second.  

What interface name are you trying to configure, eth0, wlan0, or something else?????

Please post the results of:
ifconfig

so that we can see the interfaces you have.  That way we can delete some of this superfluous info in the interfaces file.


~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:17:31:4F:B7:70  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fe4f:b770/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4215 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3939 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3966532 (3.7 MiB)  TX bytes:553717 (540.7 KiB)
          Interrupt:16 Base address:0x8000

---

