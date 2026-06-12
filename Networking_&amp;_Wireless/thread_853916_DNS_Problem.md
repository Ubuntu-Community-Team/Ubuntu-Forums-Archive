---
title: "DNS Problem"
date: 2008-07-09
forum: Networking &amp; Wireless
---

### Post by e30power on 2008-07-09
After messing around with virtualization, I think something broke DNS on the computer the virtual host was running on.
I can ping the IP's of websites, but cant ping the actual dns names (I can ping google.com by IP, but not by name).
I can ping my name servers, and can set them in nslookup, but my default server is the loopback. Is there a way to fix this?



route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
default         router          0.0.0.0         UG    100    0        0 eth0
```

/etc/network/interfaces:
```
# The loopback network interface
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet static
        address 192.168.1.3
        netmask 255.255.255.0
        broadcast 192.168.1.255
        network 192.168.1.0
        gateway 192.168.1.1
```

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:01:29:d6:bc:8e  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:29ff:fed6:bc8e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:423 errors:0 dropped:0 overruns:0 frame:0
          TX packets:364 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:41923 (40.9 KB)  TX bytes:52080 (50.8 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:672 (672.0 B)  TX bytes:672 (672.0 B)
```


/etc/nsswitch.conf:
```
passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis

```

/etc/hosts:
```
127.0.0.1       localhost
#127.0.1.1      server
192.168.1.3     server
192.168.1.1     router
192.168.1.2     wireless

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Also, this is what is happening when I run nslookup:
```
nslookup
> google.com
;; connection timed out; no servers could be reached
> server
Default server: 127.0.0.1
Address: 127.0.0.1#53
Default server: ::1
Address: ::1#53
> lserver 68.87.68.162
Default server: 68.87.68.162
Address: 68.87.68.162#53
> google.com
Server:		68.87.68.162
Address:	68.87.68.162#53

Non-authoritative answer:
Name:	google.com
Address: 72.14.207.99
Name:	google.com
Address: 64.233.187.99
Name:	google.com
Address: 64.233.167.99
> 

```


Thanks,
Rob

---

### Post by dmizer on 2008-07-09
i had the same thing happen to my virtual server a few days ago.  simply rebooting the virtual machine corrected the problem.

you might also consider disabling ipv6: [https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by e30power on 2008-07-09
I think I should clarify that virtualization is turned off on the computer that is having problems. It is not a virtualized computer, and there isnt any virtual network adapters anymore.
I will try the ipv6, thanks for the quick reply.

[edit] IPv6 didnt do the trick, the default server is still the loopback. [/edit]

---

### Post by dmizer on 2008-07-09
> **e30power said:**
> [edit] IPv6 didnt do the trick, the default server is still the loopback. [/edit]

try rebooting the router then.  even if other computers on the network are working okay, the router could still be at fault.

---

### Post by superprash2003 on 2008-07-09
are you able to access a webpage by its ip?

---

### Post by e30power on 2008-07-09
Yup.

---

### Post by dmizer on 2008-07-09
have you tried alternate dns servers?
[https://www.opendns.com/start?device=ubuntu](https://www.opendns.com/start?device=ubuntu)

according to your ifconfig output, the ip for the machine in question is 192.168.1.3.  in /etc/hosts ... you have your machine listed with it's external ip rather than the loopback:
```
127.0.0.1       localhost
#127.0.1.1      server
[COLOR="Red"]192.168.1.3     server[/COLOR]
192.168.1.1     router
192.168.1.2     wireless

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```
try commenting this line out, uncomment the loopback line above it, and then restart networking.

---

### Post by e30power on 2008-07-09
Alright, I tried that and no luck.
I am wondering if using the computer as a KVM host messed up my DNS settings, and when I took KVM off the computer, some of the things that were changed remain.
I guess I can look at my other computer running ubuntu and compare files.

Thanks
Rob

---

### Post by e30power on 2008-07-10
Alright, so I figured out what it was after looking at some logs. I had copied a resolv.conf from my file server, and it didnt have the right permissions.
If anyone else runs into this problem, chmod 644 your resolv.conf and make sure you chown root:root it.

DMizer, thanks for your help, sorry to waste your time on a problem I should have seen yesterday,

---

