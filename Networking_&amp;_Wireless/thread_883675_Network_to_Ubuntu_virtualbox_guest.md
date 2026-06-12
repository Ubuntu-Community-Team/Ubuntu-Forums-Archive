---
title: "Network to Ubuntu virtualbox guest?"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by lugoteehalt on 2008-08-08
Have Debian Etch AMD64 host with Ubuntu, hardy heron - I assume since pic of heron on screen, in the 'virtual computer' virtualbox - Ubuntu is the 'guest'.

Trying to get a network between host and guest.  Total ignorant cock up.  Below some network files, etc..  Anyone feel like giving me some pointers?

```
lugo@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:27:41:fd:a2  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:fe41:fda2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:170 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:21066 (20.5 KB)
          Interrupt:11 Base address:0xc020 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:444 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22636 (22.1 KB)  TX bytes:22636 (22.1 KB)

lugo@ubuntu:~$

lugo@asus:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:1E:8C:1F:93:B1  
          inet addr:192.168.1.10  Bcast:192.168.1.255 Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:233 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:276 errors:0 dropped:0 overruns:0 frame:0
          TX packets:276 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19504 (19.0 KiB)  TX bytes:19504 (19.0 KiB)

vbox0     Link encap:Ethernet  HWaddr 32:2C:C3:24:06:8B  
          inet6 addr: fe80::302c:c3ff:fe24:68b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:6 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


For Ubuntu guest:
/etc/hosts:
127.0.0.1 localhost
127.0.1.1 ubuntu.smegma.org ubuntu.smegma.org

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
192.168.1.10 vbox0

For Debian amd64 host:
/etc/hosts:
127.0.0.1 localhost localhost.localdomain localhost
127.0.1.1 asus

::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

169.26.8.48 ubuntu.smegma.org ubuntu


Sorry I’ve forgotten which this is from, will sort out:
/etc/network/interfaces:
auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.10
netmask 255.255.255.0

auto eth0



Host Debian:
lugo@asus:~$ less /etc/networks
default         0.0.0.0
loopback        127.0.0.0
link-local      169.254.0.0
apricot.domain.org      192.168.1.2     apricot
asus.domain.org         192.168.1.3     asus
debian.domain.org       192.168.1.1     debian

/etc/networks (END) 


Guest Ubuntu:
# symbolic names for networks, see networks(5) for more information
link-local 169.254.0.0
/etc/networks (END) 

```
TIA.

---

