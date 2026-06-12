---
title: "Can't connect to server anymore"
date: 2014-07-02
forum: Networking &amp; Wireless
---

### Post by masciam on 2014-07-02
Hi everyone,
I have 0 experience with ubuntu or network problems, and I've been trying to figure this out for 2 days now, so any help is appreciated.

So this friend of mine has apache running on ubuntu. The hosting company he's using only provides the server, and you're responsible for managing it. Two days ago for no apparent reason he couldn't open his website anymore, so I thought I'd try and restart apache.

When I tried to connect to the server using SSH I got a timeout (connection refused). The hosting company provided him with 2 public IPs (main one and an additional IP), and when I tried to SSH using the additional IP it worked. Any ideas on why this is happening? He hasn't changed anything at all in the last days.

Here's what /etc/network/interfaces looks like:

```
auto loiface lo inet loopback


auto eth0
iface eth0 inet dhcp
auto eth0:0
iface eth0:0 inet static
address 10.1.41.3
netmask 255.255.255.192
```

And ifconfig:

```


eth0      Link encap:Ethernet  HWaddr 7e:ef:53:cc:0d:f5
          inet addr:10.1.41.2  Bcast:10.1.41.63  Mask:255.255.255.192
          inet6 addr: fe80::7cef:53ff:fecc:df5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:509 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:36329 (36.3 KB)  TX bytes:57910 (57.9 KB)
          Interrupt:16


eth0:0    Link encap:Ethernet  HWaddr 7e:ef:53:cc:0d:f5
          inet addr:10.1.41.3  Bcast:10.1.41.63  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:504 (504.0 B)  TX bytes:504 (504.0 B)



```


Also I just noticed I can't ping anything from the server. When I ping google.com or even 8.8.8.8 here's what it shows:

```
ping: unknown host google.com

```
Does this look like a network configuration issue or something on the hosting company side? 

Thank you!

---

### Post by TheFu on 2014-07-03
Those IPs are internal - non-routed over the internet. That explains why you cannot get there from anywhere. That's inbound. The fact that you can ssh in at all is surprising to me. Something else must be happening.

As to how the networking works outbound, that is hard to say from the provided data.
[http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking](http://blog.jdpfu.com/2013/03/01/linux-troubleshooting-101-networking) should help determine if it is a routing issue or DNS.

---

### Post by masciam on 2014-07-03
I too don't understand how I'm able to SSH in.
It's not a DNS issue either, even if I ping the IPs directly I still get a timeout.
I think this is a routing issue. I'm trying to contact the hosting company.
Thank you for your reply.

---

### Post by SeijiSensei on 2014-07-03
I'd switch to a company like [Linode]("http://www.linode.com/") that provides real public IP addresses.  Their least expensive package is just $10/month.

---

### Post by TheFu on 2014-07-03
> **SeijiSensei said:**
> I'd switch to a company like [Linode]("http://www.linode.com/") that provides real public IP addresses.  Their least expensive package is just $10/month.

I'm not a linode customer, but did get a bunch of conference swag from them a few weeks ago. ;) They support YAPC every year and are well-thought-of in the Linux community.

I suspect the ISP does port translation at their edge routers for ssh and http.  Nothing wrong with that, IMHO.  I'd rather have only the specific ports available on the internet than have EVERY port available.  Perhaps if you posted the output from my Networking 101 sheet, we could help?  Like the 'route' table?

It is odd for a hosting provider to screw that up, IME, though it does happen.

---

### Post by masciam on 2014-07-03
Hi!
Here's the output:

root@cpro11511:~# dmesg |grep eth[0-9]
```

[   38.040054] eth0: no IPv6 routers present
```

root@cpro11511:~# sudo lshw -C network
```

  *-network               
       description: Ethernet interface
       physical id: 1
       logical name: eth0
       serial: 7e:ef:53:cc:0d:f5
       capabilities: ethernet physical
       configuration: broadcast=yes ip=10.1.41.2 link=yes multicast=yes
```

root@cpro11511:~# ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 7e:ef:53:cc:0d:f5
          inet addr:10.1.41.2  Bcast:10.1.41.63  Mask:255.255.255.192
          inet6 addr: fe80::7cef:53ff:fecc:df5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10490 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:729278 (729.2 KB)  TX bytes:1670416 (1.6 MB)
          Interrupt:17


eth0:0    Link encap:Ethernet  HWaddr 7e:ef:53:cc:0d:f5
          inet addr:10.1.41.3  Bcast:10.1.41.63  Mask:255.255.255.192
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

root@cpro11511:~# more /etc/resolv.conf
```
nameserver 186.202.26.26
nameserver 186.202.27.27
domain locaweb.com.br
search locaweb.com.br
```

root@cpro11511:~# route
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.41.0       *               255.255.255.192 U     0      0        0 eth0

```

---

### Post by TheFu on 2014-07-04
That route is bad. Won't get you anywhere. It is missing a default gateway. Something similar to this is needed - clearly, your router/gw and subnet will be different:
```
$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         rt1             0.0.0.0         UG    0      0        0 eth0
172.22.22.0     *               255.255.255.0   U     0      0        0 eth0

```

---

### Post by masciam on 2014-07-04
Hi,
Sorry, I tried it again and I do have 2 lines.. but it takes a few seconds for it to show the 2nd one.

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.41.0       *               255.255.255.192 U     0      0        0 eth0
default         10.1.41.1       0.0.0.0         UG    100    0        0 eth0

```

Any ideas on how I'm able to ssh in to the server using the 2nd IP (187.XXX.XXX.XXX) ? I don't see it assigned anywhere?

---

### Post by TheFu on 2014-07-04
NAT performed at the router.  The hosting provider is doing this.

---

### Post by masciam on 2014-07-04
Turns out it was a routing issue. They have finally fixed it.
THanks everyone!

---

