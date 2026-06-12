---
title: "[Query] Using dnsmasq with D-Link 502T"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by ShirishAg75 on 2007-05-22
Hi all,
      This is a single machine. I want to set up dnsmasq for faster net access. I have read [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/) & I have few queries. Some points to consider :-

1. I'm not using any dialer to make the net connection. All the dialing & authentication is done by the router. 

2. I 'm using the D-Link 502T ADSL 2+  modem+ router where in the the router itself I have given DNS Addresses as :-

```
 208.67.222.222 
208.67.222.220 . 
```3.  DHCP server 

```
 192.168.1.2
192.168.1.254

Lease time 3600 seconds
```Query time 

Now, do I need to make some changes in the router also alongwith changes in /etc/resolv.conf as well as /etc/resolv.dnsmasq.conf

 my /etc/resolv.conf is as under :-

```
 nameserver 192.168.1.1
nameserver 61.1.96.69
nameserver 218.248.255.145
search opendns.com bsnl.co.in
``` The reason behind having these nameservers different from the ones in the router is a kind of backup.

There is nothing in /etc/ppp/peers/dsl-provider as I'm not using any dsl-dialer. As I understand this is only used when one is using a pppoe dialer. Please lemme know what things I need to do/change.Cheers !

---

### Post by ubuntonista on 2007-05-22
I don't see what your problem is - is caching working - are lookups faster?
Generally speaking the cache is on your computer, and you can't have the cache be on the router. So all changes you make will be to your computer only.

---

