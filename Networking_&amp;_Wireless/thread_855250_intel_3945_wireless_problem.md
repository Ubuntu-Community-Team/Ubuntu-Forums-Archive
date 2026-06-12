---
title: "intel 3945 wireless problem"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by amedac on 2008-07-10
On the start, i'm sorry because my bad english....
I have problem with wireless network on ubuntu hardy, i'm connected to my unsecured network, and i can ping computer with shared connection, but i don't have internet connection...
On the same laptop, when i boot into slax, wireless network works perfect... Any solutions?

---

### Post by chili555 on 2008-07-10
May we please see these terminal commands:```
ifconfig
iwconfig
cat /etc/resolv.conf
```Thanks.

---

### Post by amedac on 2008-07-10
amedac@amedac-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:4b:61:75:0e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1b:77:bd:14:29  
          inet addr:192.168.0.183  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:386 (386.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Memory:e4100000-e4101000 

eth0:avahi Link encap:Ethernet  HWaddr 00:1a:4b:61:75:0e  
          inet addr:169.254.3.238  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20101 (19.6 KB)  TX bytes:20101 (19.6 KB)

amedac@amedac-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"asus"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:F3:2B:C1:48   
          Bit Rate=54 Mb/s   
          RTS thr=1600 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-28 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

amedac@amedac-laptop:~$ cat /etc/resolv.conf
### BEGIN INFO
#
# Modified_by:  NetworkManager
# Process:      /usr/bin/NetworkManager
# Process_id:   5793
#
### END INFO

search mshome.net


nameserver 192.168.0.1

---

### Post by amedac on 2008-07-10
I have forget to write, my drivers are installed trough ndisswrapper

---

### Post by chili555 on 2008-07-10
Looks good so far. Now, let's see:```
ping -c3 192.168.0.1
ping -c3 209.85.165.99
ping -c3 www.google.com
```Thanks.

---

### Post by amedac on 2008-07-10
This is output, same is with using sudo 
> amedac@amedac-laptop:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

amedac@amedac-laptop:~$ ping -c3 209.85.165.99
PING 209.85.165.99 (209.85.165.99) 56(84) bytes of data.
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted

--- 209.85.165.99 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2008ms

amedac@amedac-laptop:~$ sudo ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


Thank you for helping me

---

### Post by chili555 on 2008-07-10
Please do:```
sudo ifdown eth0
```Then re-try the pings.

If that doesn't fix it, then I wonder if this is the problem: [http://ubuntuforums.org/showthread.php?t=345251](http://ubuntuforums.org/showthread.php?t=345251)

---

### Post by amedac on 2008-07-10
This is output of ifdown, i'dont know is it good:
> amedac@amedac-laptop:~$ sudo ifdown eth0
[sudo] password for amedac: 
There is already a pid file /var/run/dhclient.eth0.pid with pid 6839
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:1a:4b:61:75:0e
Sending on   LPF/eth0/00:1a:4b:61:75:0e
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Operation not permitted

After that, ping outputs are same sa before... Problem is maybe in the link that you have provided but i don't have that program installed.I think i don't have any firewall. I don't know how to set iptables

---

### Post by chili555 on 2008-07-10
> DHCPRELEASE on eth0 to 192.168.1.1 port 67Your ethernet thinks the router or access point is at 192.168.**1**.1. However, *resolv.conf* thinks it's 192.168.**0**.1.> nameserver 192.168.0.1So, evidently does your wireless:> eth1 Link encap:Ethernet HWaddr 00:1b:77:bd:14:29
inet addr:192.168.0.183 Bcast:192.168.0.255 Mask:255.255.255.0That can't be good!

May we please see:```
cat /etc/network/interfaces
```We are getting closer.

---

### Post by amedac on 2008-07-10
Here is output:

> amedac@amedac-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider


iface wlan0_rename inet dhcp

iface br0 inet dhcp
bridge_ports eth0 eth1



iface eth0 inet dhcp

auto eth0

By default i connect to internet with ppp connection. Now i don't have ethernet cable plugged, end eth0 interface is down when i'm tryin wireless

---

