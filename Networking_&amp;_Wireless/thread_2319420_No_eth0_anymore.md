---
title: "No eth0 anymore"
date: 2016-04-04
forum: Networking &amp; Wireless
---

### Post by ELMIT on 2016-04-04
Some strange things are happening on my system:

Since a few days I have troubles to find USB devices (separate post later), ... I even changed the motherboard. 

Now I find that my local web sites are not available to the world. I found that the router points to internal IP address *.20, while ifconfig shows:

```
sudo ifconfig
eth1      Link encap:Ethernet  HWaddr d0:50:99:29:b9:ab  
          inet addr:192.168.178.36  Bcast:192.168.178.255  Mask:255.255.255.0
          inet6 addr: 2001:b030:251c:0:2d19:8244:8584:c4d4/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:a8c3:a74f:52c3:5441/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:d250:99ff:fe29:b9ab/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:5063:804e:beea:fe3b/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:80cd:883b:e400:8ae0/64 Scope:Global
          inet6 addr: fe80::d250:99ff:fe29:b9ab/64 Scope:Link
          inet6 addr: 2001:b030:251c:0:7129:c1f2:f972:c56/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:643c:f44d:cb55:9aa6/64 Scope:Global
          inet6 addr: 2001:b030:251c:0:d15f:dc4c:398d:e884/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:71113501 errors:0 dropped:0 overruns:0 frame:0
          TX packets:69514103 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45461951285 (45.4 GB)  TX bytes:54935789086 (54.9 GB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4723016 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4723016 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:906737856 (906.7 MB)  TX bytes:906737856 (906.7 MB)

```

It shows the IP address of eth1 *.36  - No wonder that the world could not see the web site.
No eth0 !!!

I try to change that fixed setting in /etc/network/interfaces (the entire paragraph of the static ip got lost)

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet staic
address 192.168.178.20
netmask 255.255.255.0
gateway 192.168.178.1
dns-search elmit.biz elmit.net
dns-nameservers 168.95.192.1 168.95.1.1

```


I try to update this by issuing the command:

```
sudo ifup eth1
/etc/network/interfaces:6: unknown method
ifup: couldn't read interfaces file "/etc/network/interfaces"

```

Why? What to do? What means "6"

---

### Post by Azdour on 2016-04-04
Hi,

It's maybe because you have spelt static wrong. You have posted:

iface eth1 inet staic

When it should be:

iface eth1 inet static

---

### Post by slickymaster on 2016-04-04
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by ELMIT on 2016-04-04
> **Azdour said:**
> Hi,

It's maybe because you have spelt static wrong. You have posted:

iface eth1 inet staic

When it should be:

iface eth1 inet static

Thanks! However, still something wrong:

```
sudo ifup eth1
RTNETLINK answers: File exists
Failed to bring up eth1.

```

---

### Post by slickymaster on 2016-04-04
@ELMIT:
I've edited your two previous posts, replacing quote tags with code tags. Output code posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by Azdour on 2016-04-04
Do you have do run ifdown before ifup?

Also do you have network-manager installed any maybe that is controlling eth1?  Just some guesses.  I run a DRBL server and control the network cards via the interfaces file but have to uninstall network-manager to prevent it from taking over.

---

