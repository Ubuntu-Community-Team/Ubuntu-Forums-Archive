---
title: "Cannot see other machine on 192.168.0.x address"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by jimmy_k on 2006-07-30
Hello,

I have installed ubuntu, and am very impressed with how easy it was to set up, but I have a problem seeing another machine on my wireless network.

My ubuntu machine is on 192.168.0.3
The wireless router is on 192.168.0.1
The NSLU2 (Slug) is on 192.168.0.5

Under Windows I can see the slug with no problems (and its shares) and I can ping it.

I cannot, however see it from ubuntu. I originally thought this might be a routing issue but now I'm not so sure. My routing table is as follows:

Destination  Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0  *               255.255.255.0   U     0      0        0 eth1
default      192.168.0.1     0.0.0.0         UG    0      0        0 eth1

and if I run ifconfig I get:

eth1      Link encap:Ethernet  HWaddr 00:13:CE:32:7B:A4
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe32:7ba4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2640 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2458 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2225569 (2.1 MiB)  TX bytes:396268 (386.9 KiB)
          Interrupt:201 Memory:dfcfd000-dfcfdfff


ping reports all packets lost and traceroute reports:
traceroute to 192.168.0.5 (192.168.0.5), 30 hops max, 40 byte packets
 1  * * *
 2  * * *
 3  * * *
 4  Tomatoes (192.168.0.5)  7.006 ms  10.803 ms  13.331 ms

Any help would be gratefully received. Many thanks.

---

### Post by costoa on 2006-07-30
Can you ping 127.0.0.1, 192.168.0.3 and the router successfully? I'm guessing yes, yes and no. Could you also post a copy of you /etc/network/interfaces please?

---

### Post by jimmy_k on 2006-07-30
Hello,

(un)fortunately I can ping all those addresses successfully (127.0.0.1, 192.168.0.3 and 192.168.0.1) - I can connect to the internet too - just cannot connect to 192.168.0.5 - which I know is working because windows connects to it.

The content of the interfaces file is as follows:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth1
iface eth1 inet static
wireless-essid Pickles
wireless-key 0A4D3A1AA949A7681A6727C404
address 192.168.0.3
netmask 255.255.255.0
gateway 192.168.0.1

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Many thanks (this is not in the interfaces file :p )

---

### Post by tripwire45 on 2006-07-30
Hmmm. Interesting. What OS is NSLU2 (Slug) running? Also, the traceroute is able to get to the 192.168.0.5 host with four hops but why is the host identified as "tomatoes" rather than "slug" and why four hops? If both machines are on the same subnet, you should get a result like this:
```
root@ubuntu:~# traceroute 10.9.8.219
traceroute to 10.9.8.219 (10.9.8.219), 30 hops max, 40 byte packets
 1  10.9.8.219 (10.9.8.219)  0.384 ms  0.245 ms  0.161 ms
```

I'm on an Ubuntu 6.06 machine with an IP address of 10.9.8.205. Both machines are connected through a layer 2 switch so routing isn't involved. Your wireless router shouldn't try to "route" packets on the same subnet, it should just switch the packets between the two machines.

Any other information you can provide about your network would be helpful. Thanks.

---

### Post by jimmy_k on 2006-07-30
It's called tomatoes because I've set up an alias for it (I was struggling for names that day!) - slug is the commonly used name of the box - it is called a linksys nslu2 which isn't very catchy. It is running a flavour of linux (debian I think) there's more info on it here: [http://www.nslu2-linux.org/](http://www.nslu2-linux.org/) - it is a great little box for about 50 uk pounds. It essentially hosts usb hard disks on a network - a sort of NAS.

I have no idea why it takes 4 hops - I tried to alter the route table but with limited success - if I routed via 192.168.0.1 I seemed to get a redirect when I pinged it.

---

### Post by costoa on 2006-07-30
Yeah I've got a nslu2 running unslung too. Fun little (I mean tiny) box to play with. I don't think anything is wrong with your Ubuntu box. Is it possible that the slug went back to it's default ip (192.168.1.77)? If so you could setup eth0 as 192.168.1.1 with a gateway of 192.168.1.77 and connect with a crossover cable.

Here's a link for the benefit of others curious about the the slug's [installation]("http://download.berlios.de/unslung/Unslung-6.8-beta-README.txt") process.

Also you might want to change WEP key. =)

---

### Post by jimmy_k on 2006-07-30
WEP key changed as soon as I posted it - didn't realise then thought "pants" so had to change all systems.:oops: I was wondering what the guy was doing outside my door with a laptop :) 

I've checked the slug - it is still on 192.168.0.5. It's kind of odd - because I also have a streamium sl50 wifi music box and that sits on 192.168.0.2 and I can ping that with no problems.

If I remove the route entry for 192.168.0.x just leaving the default entry then I  have this in my route table:

Destination Gateway         Genmask         Flags Metric Ref    Use Iface
default     192.168.0.1     0.0.0.0         UG    0      0        0 eth1

I can then run ping which comes back with:

PING 192.168.0.5 (192.168.0.5) 56(84) bytes of data.
64 bytes from 192.168.0.5: icmp_seq=1 ttl=64 time=5.12 ms
From 192.168.0.1: icmp_seq=2 Redirect Host(New nexthop: 192.168.0.5)
64 bytes from 192.168.0.5: icmp_seq=2 ttl=64 time=4.57 ms

I presume this redirect is the router saying "Oi this isn't the most efficient route - go directly to the machine".

If this is the case is there anyway of switching off the redirect on the router or getting ubuntu to ignore it.

I was wondering about static routing but I am not very proficient in this area.

My router is a netgear DG834GT

Thanks

---

### Post by jimmy_k on 2006-08-14
OK I just thought I'd let you know that I found a work around for this. I forced did a static route via the router to the slug and then had to add a static route on the slug back (via the router) - otherwise you get ICMP redirects. I know this isn't the ideal solution and I still don't know why I can't see the slug directly but it works.:-P

---

