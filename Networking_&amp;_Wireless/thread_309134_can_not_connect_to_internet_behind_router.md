---
title: "can not connect to internet behind router"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by changliang on 2006-11-29
my computer is behind tp-link router R410, my windows 2000 can connect to network using dhcp, but my ubuntu 6.10 do not work.

following is command result, can you give me some light? thanks

```
oem@ubuntuxcl:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:20:ED:45:05:C2  
          inet addr:192.168.1.100  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::220:edff:fe45:5c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2287 (2.2 KiB)  TX bytes:6456 (6.3 KiB)
          Interrupt:209 Base address:0x8000 

oem@ubuntuxcl:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=64 time=0.563 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=64 time=0.574 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=64 time=0.556 ms
64 bytes from 192.168.1.1: icmp_seq=4 ttl=64 time=0.549 ms

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3010ms
rtt min/avg/max/mdev = 0.549/0.560/0.574/0.025 ms

oem@ubuntuxcl:~$ ping www.google.com

oem@ubuntuxcl:~$ lspci |grep Eth
00:10.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
oem@ubuntuxcl:~$ cat /etc/resolv.conf
search domain
nameserver 202.96.128.68
nameserver 202.96.134.188
nameserver 202.96.134.133
nameserver 192.168.1.1
oem@ubuntuxcl:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp
address 192.168.1.100
netmask 255.255.255.0
gateway 192.168.1.1
oem@ubuntuxcl:~$ cat /etc/dhcp3/dhclient.conf
# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
oem@ubuntuxcl:~$ 


C:\Documents and Settings\xue changliang>ipconfig/all

Windows 2000 IP Configuration

        Host Name . . . . . . . . . . . . : xcl
        Primary DNS Suffix  . . . . . . . :
        Node Type . . . . . . . . . . . . : Broadcast
        IP Routing Enabled. . . . . . . . : No
        WINS Proxy Enabled. . . . . . . . : No
        DNS Suffix Search List. . . . . . : domain

Ethernet adapter ????:

        Connection-specific DNS Suffix  . : domain
        Description . . . . . . . . . . . : Realtek RTL8139(A) PCI Fast Ethernet
 Adapter
        Physical Address. . . . . . . . . : 00-20-ED-45-05-C2
        DHCP Enabled. . . . . . . . . . . : Yes
        Autoconfiguration Enabled . . . . : Yes
        IP Address. . . . . . . . . . . . : 192.168.1.100
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.1.1
        DHCP Server . . . . . . . . . . . : 192.168.1.1
        DNS Servers . . . . . . . . . . . : 202.96.128.68
                                            202.96.134.188
                                            202.96.134.133
                                            192.168.1.1
        Lease Obtained. . . . . . . . . . : 2006?11?29? 18:49:55
        Lease Expires . . . . . . . . . . : 2006?11?29? 20:49:55

C:\Documents and Settings\xue changliang>
```

---

### Post by _simon_ on 2006-11-29
Are the DNS being assigned by the ISP or have you manually entered them into your router?

With my Linksys setup, I found that Ubuntu would only connect if the router had the DNS entered manually.

---

### Post by apral on 2006-11-29
Had the same problem.Manually entering the dns seems to be the only solution.If you need more help just add to thread. :)

---

### Post by changliang on 2006-11-30
yes, very thanks

---

### Post by stream303 on 2006-12-01
Glad to see you got this fixed.  For a couple more options check this howto:

[http://www.ubuntuforums.org/showthread.php?t=307758](http://www.ubuntuforums.org/showthread.php?t=307758)

---

