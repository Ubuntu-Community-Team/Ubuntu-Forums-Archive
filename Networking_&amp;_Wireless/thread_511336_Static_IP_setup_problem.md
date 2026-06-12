---
title: "Static IP setup problem"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by rabideau on 2007-07-27
I have researched everything I can find and am totally baffled with my inability to make a static ip server visible on the web. I have a DSL modem as my web interface it is not providing DHCP nor wireless (it has a staTic IP address of 63.239.238.22)... immediately 'beneath that I have a wireless router 63.239.238.18' in parallel I am attempting to place my Linux Ubuntu Web Server 63.239.238.17-- Jeeves).

I have created the following

File: **/etc/network/interfaces**  

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 63.239.238.17
        netmask 255.255.255.248
        network 63.239.238.16
        broadcast 63.239.238.21
        gateway 63.239.238.22

I have also created the following files:

 File: **/etc/resolve.conf **                             

nameserver 63.239.238.22

 File: **/etc/hostname  **                              

Jeeves

_**From this machine I am unable to access the internet.  From my internal network I am able to access Jeeves.**_

The following diagnostics are what I see:

root@Jeeves:~# netstat -nat
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:2208          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:80              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:50930           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:5432          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:25              0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:697             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:443             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:38719           0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:2207          0.0.0.0:*               LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN  

root@Jeeves:~# /sbin/route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
63.239.238.16   *               255.255.255.248 U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         63.239.238.22   0.0.0.0         UG    0      0        0 eth0


***Would someone be generous enough to tell me what I am doing wrong?  Thanks!***

---

### Post by tgm4883 on 2007-07-27
Do you get 63.239.238.17 from your ISP or did you assign that to the computer yourself?  I find it odd (unless of course you have several static ip addresses from your ISP) that you have set your internal network ip address the same as your external IP address.

What you should be doing if you only have 1 static IP address is setting your DSL modem to forward port 80 (or whatever port you have set for your web server) to your web server.  Have your internal IP address be private addresses (ie 192.168.x.x)

If you do have multiple IP addresses from your ISP, then let me know, as the above answer is for only one

---

### Post by rabideau on 2007-07-28
Thank you for the response...

I have a block of 5 static IPs and three reserved IPs (owned by my provider) so basically there is a total of 8 in house.  The three 'reserved' IPs are for:

63...16 is Reserved Network
63..22 is Reserved Gateway
63 ...23 is Reserved Broadcast

The remaining 5 are user assignable (meaning me...)

btw... I have the following layout:

 DSL Modem (63...22)
|
V
Ethernet Switch-----> Wireless Router (63..18 ) -----> Internal Private Network (192...)
|
V
|--------------> Ubuntu WebServer (63...17)


I hope this helps explain my situation better.

---

### Post by rabideau on 2007-07-28
Hi all,

I managed to solve the problem.  The issue was in two places:
[LIST=1]
[*]resolv.conf needed new dns server addresses
[*]I needed to change the netmask to 255.255.255.0[/LIST]Once I did those things everything worked perfectly!  Hooray!:guitar:

---

