---
title: "Can't set up static IP address"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by Nitewalker on 2008-06-10
Everytime that I try and set up a static IP address for my laptop it won't connect to the network anymore.  Only way I can get to network is thru using "enable roaming", what do I need to do to get it to accept a static address.  My current "ifconfig" shows
nitewalker@smj:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:16:cf:0b:01:d2  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:cfff:fe0b:1d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1732 errors:1 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1731419 (1.6 MB)  TX bytes:198561 (193.9 KB)

and my /etc/hosts is:
nitewalker@smj:~$ cat /etc/hosts
127.0.0.1 localhost
127.0.0.1.1 smj
192.168.0.100 smj.homeip.net smj
192.168.0.101 smj2.homeip.net smj2

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.0.100 smj.home.net smj

What I am wanting to do is assign static IP's to both smj & smj2 or 192.168.0.110 & 111.  
thanks:confused:

---

### Post by nixscripter on 2008-06-11
Would a secondary IP do?

In other words, a machine would have _two_ addresses, one static and one dynamic. Assuming the ranges don't conflict, and you want interface ath0 to be set up, try this:
```
sudo ifconfig ath0:1 **192.168.0.static** up
```

If that works, and you like it, you can make it do this on boot with this entry in the /etc/network/interfaces file:

```

iface ath0:1 inet static
    address **192.168.0.static**
    netmask 255.255.255.0
    network 192.168.0.0

```

---

