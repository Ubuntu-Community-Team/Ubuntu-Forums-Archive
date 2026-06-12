---
title: "[SOLVED] Not able to ping router and internet"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by Surendra on 2008-11-27
Hi, i have a issue with my network. It's working fine till y'day.

I installed ubuntu server 8.04 on my virtual pc 2007. I am not getting internet on  ubuntu server and also not able to ping my wireless router. But at the same time i am able to access internet on Win XP.
Here is my network setting on ubuntu.

[PHP]cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate themm. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.110
netmast 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.0.1

[/PHP]



[PHP]cat /etc/resolv.conf

nameserver 192.168.88.1
nameserver 68.x.x.x
nameserver 68.x.x.x[/PHP]


[PHP]ifconfig
eth0     Link encap:Ethernet HWaddr 00:03:fc:63:e0:49
         inet addr:192.168.1.110 Bcast:192.168.1.255 Mask:255.255.255.0
         inet6 addr: f380::203:ffff:fe6e:80c9/64 Scope: Link
         UP BROADCAST MULTICAST MTU:1500 Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:411 errors:0 dropped:0 overruns:0 carrier:0
	 collisions:0 txqueuelen:1000
 	 RX bytes:0 (0.0 B) TX bytes:25185 (24.5 B)
	 Interrup:11 base address:0xec00

lo 	 Link encap:Local Loopback
	 inet addr:127.0.0.1 Mask:255.0.0.0
   	 inet6 addr: ::1/128 Scope:Host
	 UP LOOPBACK RUNNING MTU:16436 Metric:1
	 RX packets:1203 errors:0 dropped:0 overruns:0 frame:0
	 TX packets:1203 errors:0 dropped:0 overruns:0 carrier:0
	 collisions:0 txqueuelen:0
	 RX bytes:286611 (279.8 KB) TX bytes:286611(279.8 KB)

[/PHP]

[PHP]route -n

Kernel IP routing table
Destination Gateway Genmask       Flags Metric Ref Use Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 	0 	0   0  wlan0
home@ubuntu:~$[/PHP]

When i restart the network, i am getting below message

[PHP]
sudo /etc/init.d/networking restart

 * Reconfiguring network interfaces...
RTNETLINK answers: No such process
postconf: fatal: open /etc/postfix/main.cf: No such file or directory
SIOCDELRT: No such process
SIOCADDRT: No such process


[/PHP]


Please tell how to ping router and internet for permanently. I did some changes week ago it's working fine, then i reboot my ssystem got a issue. 

Thanks in Advance
Surendra

---

### Post by Surendra on 2008-11-28
Today i was successfully installed ndiswrapper. But still i am not getting wireless connection.

iwconfig
[PHP]
lo no wireless extensions.

eth0 no wireless extensions.

br0 no wireless extensions.
[/PHP]

please tell me how to i get wireless connection.

---

### Post by superprash2003 on 2008-11-29
post output of lshw -C network.. your static ip looks weird you have set an ip 192.168.1.110 and gateway as 192.168.0.1 .. thats weird..

---

### Post by Surendra on 2008-12-04
Superprash2003,
I did something on server. now i got the different ifconfig. i am giving both. please have look yet it.

ifconfig
[PHP]
br0       Link encap:Ethernet  HWaddr e2:6a:c0:49:7b:25
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e06a:c0ff:fe49:7b25/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:3879 (3.7 KB)

eth0      Link encap:Ethernet  HWaddr 00:03:ff:6e:80:c9
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe6e:80c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:163 errors:0 dropped:0 overruns:0 frame:0
          TX packets:128 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:18618 (18.1 KB)  TX bytes:14388 (14.0 KB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:44 errors:0 dropped:0 overruns:0 frame:0
          TX packets:44 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22505 (21.9 KB)  TX bytes:22505 (21.9 KB)
[/php]

[PHP]
 lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: DECchip 21140 [FasterNet]
       vendor: Digital Equipment Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 20
       serial: 00:03:ff:6e:80:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.15 ip=192.168.1.104 latency=64 module=tulip multicast=yes
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: br0
       serial: e2:6a:c0:49:7b:25
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.1.110 multicast=yes
[/PHP]

---

### Post by sleepyjon on 2008-12-04
> **Surendra said:**
> 

[PHP]cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate themm. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.110
netmast 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.0.1

[/PHP]



Your IP address & your default gateway are on separate networks.

Either you need to change your default gateway, or your ip address so they're on the same network.

Try booting into windows and checking the default gateway there. If it doesn't match the default gateway you have here, change it. Otherwise, change your ip address to 192.168.0.110

I think the command to change the ip address is:

```

ifconfig eth0 down
ifconfig eth0 address 192.168.0.110
ifconfig eth0 up

```

---

### Post by gpsmikey on 2008-12-05
Sleepyjon is on the correct track.  With a netmask of 255.255.255.0, only the last octet should be different for all machines on your LAN (including the gateway which is how you get to the internet).  Whatever the address of your router is should match the first 3 octets of all the machines on your LAN (if the router is at 192.168.1.1 then the rest of the machines AND the default gateway should be 192.168.1.x (usually, the "default gateway" will be the same address as the router).  All addresses outside of the 192.168.1.x get passed through the gateway outside to be handled (sort of - the 192.168.x.x range is special and is usually considered "unroutable" - most routers will not forward to those addresses).

mikey

---

### Post by Surendra on 2008-12-06
I changed the default gateway. Now iam able to get the internet through cable. Still i am not able to get the internet or ping router on wireless.

[PHP]
cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

#Gateway -
auto eth0
iface eth0 inet dhcp
pre-up iptables-restore < /etc/iptables.rules
post-down iptables-save > /etc/iptables.rules

#Wireless Setup
auto wlan0
iface wlan0 inet dhcp
#wireless-mode master
wireless-essid your_essid



# The primary network interface

#Bridge interface
auto br0
iface br0 inet static
address 192.168.1.110
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
bridge-ports eth1 ath0
gateway 192.168.1.1

[/PHP]

iwconfig

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

br0       no wireless extensions.


Please let me know, how do i activate the wireless network on this.

---

### Post by sleepyjon on 2008-12-06
> **Surendra said:**
> 
I changed the default gateway. Now iam able to get the internet through cable. Still i am not able to get the internet or ping router on wireless.

Alright, making progress :D

I notice in your /etc/network-interfaces you have:
> **Surendra said:**
> 
#Wireless Setup
auto wlan0
iface wlan0 inet dhcp
#wireless-mode master
wireless-essid your_essid


But when you run iwconfig, wlan0 is not listed. Also, when you ran lshw -C network, the only things listed were eth0 which is the wired connection, and br0 which I'm pretty sure is a bridge.

You also need to set your essid where it says "your_essid"

Do you have the right driver installed?

Edit: 
What's the output of 

```

ifconfig -a

```

---

### Post by Surendra on 2008-12-09
Sleepyjon,
Here is the ifconifg -a. I was create a virutal PC on windows XP on IBM Think pad.  Please let me know which driver i need to install for this.

[PHP]
 ifconfig -a
br0       Link encap:Ethernet  HWaddr ba:7c:8f:8e:03:89
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b87c:8fff:fe8e:389/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:3739 (3.6 KB)

eth0      Link encap:Ethernet  HWaddr 00:03:ff:6e:80:c9
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::203:ffff:fe6e:80c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:552 errors:0 dropped:0 overruns:0 frame:0
          TX packets:737 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:58687 (57.3 KB)  TX bytes:62653 (61.1 KB)
          Interrupt:11 Base address:0xec00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:46 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:22689 (22.1 KB)  TX bytes:22689 (22.1 KB)


[/PHP]

I installed ndiswrapper. But when i check the nidswrapper -l, nothing will come up.

[PHP]
 make install
make -C driver install
make[1]: Entering directory `/home/sbollu/ndiswrapper-1.53/driver'
make -C /usr/src/linux-headers-2.6.24-21-generic M=/home/sbollu/ndiswrapper-1.53/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.24-21-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.24-21-generic'
echo /lib/modules/2.6.24-21-generic/misc
/lib/modules/2.6.24-21-generic/misc
mkdir -p /lib/modules/2.6.24-21-generic/misc
install -m 0644 ndiswrapper.ko /lib/modules/2.6.24-21-generic/misc
/sbin/depmod -a 2.6.24-21-generic -b /
make[1]: Leaving directory `/home/sbollu/ndiswrapper-1.53/driver'
make -C utils install
make[1]: Entering directory `/home/sbollu/ndiswrapper-1.53/utils'
install -D -m 755 loadndisdriver /sbin/loadndisdriver
install -D -m 755 ndiswrapper /usr/sbin/ndiswrapper
install -D -m 755 ndiswrapper-buginfo /usr/sbin/ndiswrapper-buginfo

NOTE: Windows driver configuration file format has changed since 1.5. You must re-install Windows drivers if they were installed before.
make[1]: Leaving directory `/home/sbollu/ndiswrapper-1.53/utils'
mkdir -p -m 0755 /usr/share/man/man8
install -m 644 ndiswrapper.8 /usr/share/man/man8
install -m 644 loadndisdriver.8 /usr/share/man/man8

root@ubuntu:/home/sbollu/ndiswrapper-1.53# ndiswrapper -l
root@ubuntu:/home/sbollu/ndiswrapper-1.53#

[/PHP]

Pleae let me know is the corruct install or not?

---

### Post by Surendra on 2008-12-12
I resolved the issue. Curruently i am using ubuntu on Virtual PC 2007. I installed Virtual PC additions. Now i am able to get the internet.

Thanks for all your support.

---

