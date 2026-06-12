---
title: "[SOLVED] Unable to access school's wired network"
date: 2007-09-08
forum: Networking &amp; Wireless
---

### Post by topher200 on 2007-09-08
I've been using Ubuntu for nearly a year now, and I've searched these forums and google for any problem I've had. This is the first time that I can't find someone else who has successfully solved the same problem.

I cannot get online using my school's wired network in Ubuntu. Wireless works fine, and both work in Windows. When connect to the wired, I am given an IP address (using Network Manager) and no errors appear. However, nothing (Firefox, Opera, Hamachi) can access the internet. I have already tried many things, including stopping possible interfering services from booting, booting into "safe mode" (or whatever the Ubuntu equivalent is called), trying other ports and cables, and disabling ipv6.

Can anyone help me?

---

### Post by noob12 on 2007-09-09
Does the school require use of a web proxy by any chance?

What are your proxy settings in Firefox (From within firefox: Edit |  Preferences | Network | Advanced | Connection Settings...).

---

### Post by topher200 on 2007-09-09
Good suggestion, but unfortunately there is no proxy. I have the feeling it's something obvious like that, so any other ideas?

---

### Post by gerbman on 2007-09-09
> **topher200 said:**
> Good suggestion, but unfortunately there is no proxy. I have the feeling it's something obvious like that, so any other ideas?

What does```
ifconfig
```output?

---

### Post by noob12 on 2007-09-09
While you're at it can you also post the output of
```

route -n

cat /etc/resolv.conf

```

---

### Post by topher200 on 2007-09-09
In wireless (that works):
```
topher@topher-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7047 (6.8 KiB)  TX bytes:4017 (3.9 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:60:E2:DA  
          inet addr:172.16.29.92  Bcast:172.16.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265300 errors:0 dropped:5268 overruns:0 frame:0
          TX packets:4985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37201630 (35.4 MiB)  TX bytes:1566825 (1.4 MiB)
          Interrupt:18 Base address:0xc000 Memory:54000000-54000fff 

eth0:avah Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:169.254.5.126  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

ham0      Link encap:Ethernet  HWaddr 4A:E9:50:91:08:90  
          inet addr:5.115.121.67  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:17425 (17.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19252 (18.8 KiB)  TX bytes:19252 (18.8 KiB)
```

if wired (with no internet):```

topher@topher-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:131.128.213.95  Bcast:131.128.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:16183 (15.8 KiB)  TX bytes:10783 (10.5 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:60:E2:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:5799 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:38416413 (36.6 MiB)  TX bytes:1573102 (1.5 MiB)
          Interrupt:18 Base address:0xc000 Memory:54000000-54000fff 

ham0      Link encap:Ethernet  HWaddr 4A:E9:50:91:08:90  
          inet addr:5.115.121.67  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:17425 (17.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:269 errors:0 dropped:0 overruns:0 frame:0
          TX packets:269 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19252 (18.8 KiB)  TX bytes:19252 (18.8 KiB)
```
["http://podcast.uri.edu/~helpdesk/wiki/index.php/How_The_Internet_Works"]("http://podcast.uri.edu/~helpdesk/wiki/index.php/How_The_Internet_Works") states that (the ip I get on wired)
> 131.128.x.x
On the URI network, 131 is the 'life is good' IP net. It means that a computer successfully obtained a valid IP address from the URI DHCP server and, if they're having network problems, it isn't DHCP related. In this case, if a user cannot access the internet, it is software related.
and (the ip I get on wireless)> 
172.x.x.x
On the URI wireless network, a 172 indicates successful connection with the Access Point (AP). This does not always indicate that the user is able to surf the internet, because the IP assignment is done before user authentication. The user's signal must pass through the AP.

---

### Post by gerbman on 2007-09-09
Can you ping anything?```
ping www.google.com
```

---

### Post by topher200 on 2007-09-10
On wireless:
```
topher@topher-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.16.0.0      0.0.0.0         255.255.0.0     U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
0.0.0.0         172.16.1.13     0.0.0.0         UG    0      0        0 eth1
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0
```
```
topher@topher-laptop:~$ cat /etc/resolv.conf
search uri.edu
nameserver 131.128.1.127
nameserver 131.128.1.126
```

on wired:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.128.213.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0
```

```
topher@topher-laptop:~$ cat /etc/resolv.conf
# generated by NetworkManager, do not edit!

search reshall.uri.edu


nameserver 131.128.1.127
nameserver 131.128.1.126
```

Thanks for the help!

---

### Post by topher200 on 2007-09-10
No ping.
```
topher@topher-laptop:~$ ping google.com
ping: unknown host google.com
```

Wait- hold on. I just tried something.

Localhost:
```
topher@topher-laptop:~$ ping 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.047 ms
64 bytes from 127.0.0.1: icmp_seq=4 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=5 ttl=64 time=0.028 ms
64 bytes from 127.0.0.1: icmp_seq=6 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_seq=7 ttl=64 time=0.029 ms

--- 127.0.0.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6020ms
rtt min/avg/max/mdev = 0.028/0.032/0.047/0.009 ms
```

My ip this session:
```
topher@topher-laptop:~$ ping 131.128.213.95
PING 131.128.213.95 (131.128.213.95) 56(84) bytes of data.
64 bytes from 131.128.213.95: icmp_seq=1 ttl=64 time=0.036 ms
64 bytes from 131.128.213.95: icmp_seq=2 ttl=64 time=0.037 ms
64 bytes from 131.128.213.95: icmp_seq=3 ttl=64 time=0.036 ms
64 bytes from 131.128.213.95: icmp_seq=4 ttl=64 time=0.040 ms

--- 131.128.213.95 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
```

My friend's ip from across the hall:
```
topher@topher-laptop:~$ ping 131.128.213.223
PING 131.128.213.223 (131.128.213.223) 56(84) bytes of data.
64 bytes from 131.128.213.223: icmp_seq=1 ttl=128 time=0.413 ms
64 bytes from 131.128.213.223: icmp_seq=2 ttl=128 time=0.392 ms
64 bytes from 131.128.213.223: icmp_seq=3 ttl=128 time=0.404 ms

--- 131.128.213.223 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 0.392/0.403/0.413/0.008 ms
```

Ummm... What?

Oh- I've done it before, but I'm going to go back and check again now- pinging google's ip does not work.

---

### Post by topher200 on 2007-09-10
Pinging google's ip:
```
topher@topher-laptop:~$ ping 64.233.167.99
connect: Network is unreachable
```

---

### Post by gerbman on 2007-09-10
> **topher200 said:**
> Pinging google's ip:
```
topher@topher-laptop:~$ ping 64.233.167.99
connect: Network is unreachable
```

Ping "www.google.com"...I get packet loss myself when trying to ping "google.com". My guess is that you won't be able to ping it, but try anyway.

---

### Post by topher200 on 2007-09-10
It was the first one I tried:

> **topher200 said:**
> No ping.
```
topher@topher-laptop:~$ ping google.com
ping: unknown host google.com
```

---

### Post by noob12 on 2007-09-10
Here's your problem.  On wired you show:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.128.213.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
5.0.0.0         0.0.0.0         255.0.0.0       U     0      0        0 ham0

```

You have no default gateway configured.  You can ping the friend across the hall because he's on the same subnet.  You can't get off the subnet in this situation.  

If your friend has a Windows box, ask him to open a command window and type **route print**.  If he has a Mac, have him do **netstat -nr**.  If he has an Ubuntu box have him do **route -n** or **netstat -nr**.  In Windows the default gateway will be labelled Default Gateway.  In Mac and Ubuntu, it will show up in the Gateway column with a UG flag and 0.0.0.0 in the first column.

You want to set your gateway the same, manually for now.  I'm not sure why you aren't getting a gateway from your DHCP service.  We'll look into that next.  Whatever you're using to configure **ham0** might have something to do with it.

ADDED:

The gateway will probably be 131.128.213.1.  But replace the actual one you find in the command below:

To add the default gateway use the command
```

sudo route add default gw *xxx.xxx.xxx.xxx*

```

---

### Post by topher200 on 2007-09-10
You are a genius. It works perfectly. Any suggestions on how to make this not happen again? You're probably right about it being hamachi's fault (or how I set up hamachi).

---

### Post by noob12 on 2007-09-10
Gotta sleep.  Yes; we can look into why tomorrow.

---

### Post by topher200 on 2007-09-10
If you think it'd be easier, we can try figuring it out over AIM. My screen name is topher680.

---

### Post by noob12 on 2007-09-10
We may need to resort to IM, but not yet. 

We know the problem but not what's causing it now, and you have a temporary workaround at least.

You have a couple things in your situation that are unusual.  You seem to run with both eth0 (wired) and eth1 (wireless) UP at the same time (at least in one ifconfig you showed).  They're on separate nets.  For traffic that is supposed to go to an address that is on neither of these nets but somewhere external to both, the DHCP providers on both nets will probably supply a default gateway.  Somehow you are ending up with no default gateway.

You also have **ham0**, and I don't know how you are configuring this.  Is it possible that as part of configuring that you dropping the default gateway assigned from DHCP from eth0 and/or eth1?

Let's take a look at some things on your box:
```

cat /etc/network/interfaces

cat /etc/dhcp3/dhclient.conf

grep dhclient /var/log/syslog

```

Also, can you try this experiment to see if you you get the gateway assigned automatically when the other interfaces are not in the picture?
```

# these put down eth1 and ham0
sudo ifdown eth1
sudo ifdown ham0

# put down eth0
sudo ifdown eth0
# wait 10 seconds and bring it back up
sudo ifup eth0

# see if you have an address and the default gateway route is there
ifconfig eth0
route -n

```

---

### Post by topher200 on 2007-09-10
OK, thanks

```
topher@topher-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0
iface eth0 inet dhcp 
```
```
topher@topher-laptop:~$ cat /etc/dhcp3/dhclient.conf 
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

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, host-name,
        netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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
```
```
topher@topher-laptop:~$ grep dhclient /var/log/syslog
Sep 10 11:22:39 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:22:39 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:22:39 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 292 seconds.
Sep 10 11:27:31 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:27:31 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:27:31 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 283 seconds.
Sep 10 11:32:14 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:32:14 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:32:14 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 264 seconds.
Sep 10 11:36:38 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:36:38 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:36:38 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 239 seconds.
Sep 10 11:40:37 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:40:37 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:40:37 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 279 seconds.
Sep 10 11:45:16 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:45:16 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:45:16 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 247 seconds.
Sep 10 11:49:23 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:49:23 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:49:23 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 276 seconds.
Sep 10 11:53:59 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:53:59 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:53:59 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 252 seconds.
Sep 10 11:58:11 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 11:58:11 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 11:58:11 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 254 seconds.
Sep 10 12:02:25 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:02:25 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:02:25 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 230 seconds.
Sep 10 12:06:15 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:06:15 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:06:15 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 259 seconds.
Sep 10 12:10:34 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:10:34 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:10:34 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 254 seconds.
Sep 10 12:14:48 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:14:48 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:14:48 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 286 seconds.
Sep 10 12:19:34 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:19:34 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:19:34 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 262 seconds.
Sep 10 12:23:56 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:23:56 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:23:56 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 297 seconds.
Sep 10 12:28:53 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:28:53 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:28:53 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 264 seconds.
Sep 10 12:33:17 topher-laptop dhclient: DHCPREQUEST on eth1 to 172.16.1.14 port 67
Sep 10 12:33:17 topher-laptop dhclient: DHCPACK from 172.16.1.14
Sep 10 12:33:17 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 241 seconds.
Sep 10 12:33:57 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6605
Sep 10 12:33:57 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:33:57 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.14 port 67
Sep 10 12:33:59 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 10 12:34:04 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep 10 12:34:04 topher-laptop dhclient: DHCPOFFER from 131.128.213.2
Sep 10 12:34:04 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:34:04 topher-laptop dhclient: DHCPACK from 131.128.213.3
Sep 10 12:34:04 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 3260 seconds.
Sep 10 12:36:49 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 12779
Sep 10 12:36:49 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:36:49 topher-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 10 12:36:49 topher-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 10 12:36:49 topher-laptop dhclient: All rights reserved.
Sep 10 12:36:49 topher-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 10 12:36:49 topher-laptop dhclient: 
Sep 10 12:36:49 topher-laptop dhclient: Listening on LPF/eth0/00:16:d4:2e:b8:11
Sep 10 12:36:49 topher-laptop dhclient: Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sep 10 12:36:49 topher-laptop dhclient: Sending on   Socket/fallback
Sep 10 12:36:49 topher-laptop dhclient: DHCPRELEASE on eth0 to 131.128.1.56 port 67
Sep 10 12:36:49 topher-laptop dhclient: send_packet: Network is unreachable
Sep 10 12:36:49 topher-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 10 12:37:14 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Sep 10 12:37:14 topher-laptop dhclient: Internet Systems Consortium DHCP Client V3.0.4
Sep 10 12:37:14 topher-laptop dhclient: Copyright 2004-2006 Internet Systems Consortium.
Sep 10 12:37:14 topher-laptop dhclient: All rights reserved.
Sep 10 12:37:14 topher-laptop dhclient: For info, please visit http://www.isc.org/sw/dhcp/
Sep 10 12:37:14 topher-laptop dhclient: 
Sep 10 12:37:15 topher-laptop dhclient: Listening on LPF/eth0/00:16:d4:2e:b8:11
Sep 10 12:37:15 topher-laptop dhclient: Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sep 10 12:37:15 topher-laptop dhclient: Sending on   Socket/fallback
Sep 10 12:37:18 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 10 12:37:18 topher-laptop dhclient: DHCPOFFER from 131.128.213.2
Sep 10 12:37:18 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:37:18 topher-laptop dhclient: DHCPACK from 131.128.213.2
Sep 10 12:37:18 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 3116 seconds.
Sep 10 12:39:04 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:39:04 topher-laptop dhclient: DHCPACK from 131.128.213.2
Sep 10 12:39:04 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 3059 seconds.
Sep 10 12:39:41 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 13392
Sep 10 12:39:41 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:39:41 topher-laptop dhclient: DHCPRELEASE on eth0 to 131.128.1.56 port 67
Sep 10 12:39:41 topher-laptop dhclient: send_packet: Network is unreachable
Sep 10 12:39:41 topher-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 10 12:40:09 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 10 12:40:10 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 10 12:40:10 topher-laptop dhclient: DHCPRELEASE on eth0 to 131.128.1.56 port 67
Sep 10 12:40:10 topher-laptop dhclient: send_packet: Network is unreachable
Sep 10 12:40:10 topher-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 10 12:40:14 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Sep 10 12:40:14 topher-laptop dhclient: DHCPOFFER from 131.128.213.2
Sep 10 12:40:14 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:40:14 topher-laptop dhclient: DHCPACK from 131.128.213.3
Sep 10 12:40:14 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 3203 seconds.
Sep 10 12:40:40 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 10 12:40:44 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 10 12:40:51 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
Sep 10 12:40:51 topher-laptop dhclient: DHCPOFFER from 172.16.1.11
Sep 10 12:40:51 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:40:51 topher-laptop dhclient: DHCPACK from 172.16.1.11
Sep 10 12:40:51 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 261 seconds.
Sep 10 12:40:52 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 14070
Sep 10 12:40:52 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:40:53 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.11 port 67
Sep 10 12:42:11 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Sep 10 12:42:15 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 10 12:42:23 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Sep 10 12:42:35 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Sep 10 12:42:37 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Sep 10 12:42:37 topher-laptop dhclient: DHCPOFFER from 172.16.1.12
Sep 10 12:42:37 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:42:37 topher-laptop dhclient: DHCPACK from 172.16.1.12
Sep 10 12:42:38 topher-laptop dhclient: No DHCPOFFERS received.
Sep 10 12:42:38 topher-laptop dhclient: Trying recorded lease 131.128.213.95
Sep 10 12:42:42 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 293 seconds.
Sep 10 12:42:59 topher-laptop dhclient: No working leases in persistent database - sleeping.
Sep 10 12:44:43 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 5971
Sep 10 12:44:43 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:44:43 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.12 port 67
Sep 10 12:44:45 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 10 12:44:45 topher-laptop dhclient: DHCPRELEASE on eth0 to 131.128.1.56 port 67
Sep 10 12:44:45 topher-laptop dhclient: send_packet: Network is unreachable
Sep 10 12:44:45 topher-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 10 12:44:48 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:44:48 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 10 12:44:48 topher-laptop dhclient: DHCPACK from 131.128.213.2
Sep 10 12:44:48 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 2933 seconds.
Sep 10 12:44:53 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 10 12:44:53 topher-laptop dhclient: DHCPOFFER from 172.16.1.15
Sep 10 12:44:53 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:44:53 topher-laptop dhclient: DHCPACK from 172.16.1.15
Sep 10 12:44:53 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 289 seconds.
Sep 10 12:44:58 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6575
Sep 10 12:44:58 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:44:58 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.15 port 67
Sep 10 12:45:01 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 10 12:45:03 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Sep 10 12:45:03 topher-laptop dhclient: DHCPOFFER from 172.16.1.11
Sep 10 12:45:03 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:45:03 topher-laptop dhclient: DHCPACK from 172.16.1.11
Sep 10 12:45:03 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 230 seconds.
Sep 10 12:45:06 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6691
Sep 10 12:45:06 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:45:06 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.11 port 67
Sep 10 12:45:11 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:45:11 topher-laptop dhclient: DHCPACK from 131.128.213.3
Sep 10 12:45:11 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 3204 seconds.
Sep 10 12:45:19 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 6754
Sep 10 12:45:19 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:45:19 topher-laptop dhclient: DHCPRELEASE on eth0 to 131.128.1.56 port 67
Sep 10 12:45:19 topher-laptop dhclient: send_packet: Network is unreachable
Sep 10 12:45:19 topher-laptop dhclient: send_packet: please consult README file regarding broadcast address.
Sep 10 12:45:33 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 10 12:45:35 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
Sep 10 12:45:35 topher-laptop dhclient: DHCPOFFER from 172.16.1.11
Sep 10 12:45:35 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:45:35 topher-laptop dhclient: DHCPACK from 172.16.1.11
Sep 10 12:45:35 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 289 seconds.
Sep 10 12:46:33 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 6954
Sep 10 12:46:33 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:46:33 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.11 port 67
Sep 10 12:46:35 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 134993440
Sep 10 12:46:40 topher-laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 10 12:46:40 topher-laptop dhclient: DHCPOFFER from 172.16.1.11
Sep 10 12:46:40 topher-laptop dhclient: DHCPREQUEST on eth1 to 255.255.255.255 port 67
Sep 10 12:46:40 topher-laptop dhclient: DHCPACK from 172.16.1.11
Sep 10 12:46:40 topher-laptop dhclient: bound to 172.16.29.92 -- renewal in 283 seconds.
Sep 10 12:48:17 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth1.pid with pid 7135
Sep 10 12:48:17 topher-laptop dhclient: killed old client process, removed PID file
Sep 10 12:48:17 topher-laptop dhclient: DHCPRELEASE on eth1 to 172.16.1.11 port 67
Sep 10 12:48:19 topher-laptop dhclient: There is already a pid file /var/run/dhclient.eth0.pid with pid 134993440
Sep 10 12:48:24 topher-laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep 10 12:48:24 topher-laptop dhclient: DHCPOFFER from 131.128.213.2
Sep 10 12:48:24 topher-laptop dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Sep 10 12:48:24 topher-laptop dhclient: DHCPACK from 131.128.213.2
Sep 10 12:48:24 topher-laptop dhclient: bound to 131.128.213.95 -- renewal in 2946 seconds.

```

The experiment didn't go to well.
```
topher@topher-laptop:~$ sudo ifdown eth1
ifdown: interface eth1 not configured
topher@topher-laptop:~$ sudo ifdown ham0
ifdown: interface ham0 not configured
topher@topher-laptop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 8103
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:2e:b8:11
Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 131.128.1.56 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
topher@topher-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:2e:b8:11
Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 131.128.213.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 131.128.213.2
SIOCADDRT: Network is unreachable
bound to 131.128.213.95 -- renewal in 3470 seconds.
Error connecting to 5.139.115.67 (Network is unreachable)
8565: Connection to 5.139.115.67 failed
SMB connection failed
topher@topher-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:131.128.213.95  Bcast:131.128.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:431 errors:0 dropped:0 overruns:0 frame:0
          TX packets:223 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71644 (69.9 KiB)  TX bytes:54123 (52.8 KiB)

topher@topher-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.128.213.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
topher@topher-laptop:~$ 
```

---

### Post by noob12 on 2007-09-10
You're right; the experiment didn't go as hoped.

Instead of **sudo ifdown eth1** you will need to disable wireless in your connection manager.  I had thought you'd configured it in /etc/network/interfaces.

Instead of **sudo ifdown ham0** try doing **sudo ifconfig ham0 down**.

Then try the sequence:
```

sudo ifdown eth0
# wait 10 seconds and bring it back up
sudo ifup eth0

# see if you have an address and the default gateway route is there
ifconfig eth0
route -n

```
Can you tell me more about **ham0**, and how you configured that?

If we don't figure out why this is happening, then I suggest you do the following.  This tells your DHCP client that if it gets no routers from the DHCP server for eth0, then it should use the default you specify.  If it does get routers from the DHCP server it will use the ones provided from the server.

Edit your DHCP client configuration:
```

sudo gedit /etc/dhcp3/dhclient.conf

```
Add this block. You can put it at the end.  Substitute *xxx.xxx.xxx.xxx* with the address of your default router for the wired net that you were setting manually:
```

interface "eth0" {
  default routers *xxx.xxx.xxx.xxx*;
}

```
Note the semi-colon after the address.  It is needed.

---

### Post by topher200 on 2007-09-11
Ok, the workaround didn't work. My current /etc/dhcp3/dhclient.conf:
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
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

interface "eth0" {
  default routers 131.128.213.1;
}
```

I still need to do the "sudo route add default gw 131.128.213.1" to get online. I get the idea, but it just didn't work. Any suggestions why?

---

### Post by topher200 on 2007-09-11
I'm going to try the experiment again. My ifconfig at boot:
```
topher@topher-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:131.128.213.95  Bcast:131.128.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:53985 (52.7 KiB)  TX bytes:13882 (13.5 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:60:E2:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:54000000-54000fff 

ham0      Link encap:Ethernet  HWaddr 26:B6:C1:F0:9D:23  
          inet addr:5.115.121.67  Bcast:5.255.255.255  Mask:255.0.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1200  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 b)  TX bytes:6703 (6.5 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452 (452.0 b)  TX bytes:452 (452.0 b)
```
I turn off hamachi and turn off power to my wireless (hit the wifi switch):
```
topher@topher-laptop:~$ sudo ifconfig ham0 down
topher@topher-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:131.128.213.95  Bcast:131.128.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:658 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89267 (87.1 KiB)  TX bytes:14835 (14.4 KiB)

eth1      Link encap:Ethernet  HWaddr 00:13:02:60:E2:DA  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:3 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Memory:54000000-54000fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:452 (452.0 b)  TX bytes:452 (452.0 b)
```
Stop and start eth0:
```
topher@topher-laptop:~$ sudo ifdown eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 5418
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:2e:b8:11
Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 131.128.1.56 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
topher@topher-laptop:~$ sudo ifup eth0
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:16:d4:2e:b8:11
Sending on   LPF/eth0/00:16:d4:2e:b8:11
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 131.128.213.2
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 131.128.213.2
SIOCADDRT: Network is unreachable
bound to 131.128.213.95 -- renewal in 2801 seconds.
Error connecting to 5.139.115.67 (Network is unreachable)
7034: Connection to 5.139.115.67 failed
SMB connection failed
```
No internet, and no gateway:
```
topher@topher-laptop:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:16:D4:2E:B8:11  
          inet addr:131.128.213.95  Bcast:131.128.213.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:166 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:179462 (175.2 KiB)  TX bytes:25114 (24.5 KiB)

topher@topher-laptop:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
131.128.213.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
```
Sorry, but that just doesn't seem to do it. I'm completely lost.

---

### Post by noob12 on 2007-09-11
You have the file right. I should have clarified, and I'm hoping you understood that the change would only work on the next boot or the next time the interface is brought up.

If it isn't working on reboots or networking restarts there's another alternative way you can do the same type of thing, but  this way will always set the default gateway rather than use what comes from the server if there is something sent.

Edit **/etc/network/interfaces** (using **sudo gedit /etc/network/interfaces**).  Find your stanza for eth0 and add the post-up line shown here:
```

auto eth0
iface eth0 inet dhcp
post-up route add default gw 131.128.213.1

```

We really haven't figured out why you aren't getting the default route from DHCP.  Since your friend across the hall does, we should expect that it is being sent in the response.  I'm still wondering whether you get it but something in the configuration of the other interfaces is causing it to be dropped.

We may still see the same problem here if it is getting dropped after we set it using these  automatic commands as a result of some other interface being configured.  We know that once everything is up, you can manually type it like you have been doing.  But that may just be because all the interfaces have finished getting configured by then.  This level of debugging gets a bit hard remotely.

If the above still doesn't work for you can you also try adding this line to your /etc/network/interfaces
```

iface ham0 inet manual

```
and seeing if that helps (after reboot or networking restart).

---

### Post by topher200 on 2007-09-11
Ok, so I edited the line in **/etc/network/interfaces**. When I restart networking (**sudo /etc/init.d/networking restart**), I connect perfectly. However, when I boot, I must manually restart networking before the connection is reached.

I'm going to keep experimenting.

---

### Post by topher200 on 2007-09-11
OK, with this configuration, network manager doesn't let me control the wired connection, so I'm taking the line out of **/etc/network/interfaces**. Any idea why **dhclient.conf** one didn't work? Or, better yet, any new ideas on what could be stopping my computer from getting the gateway automatically? This is all completely over my head.

---

### Post by noob12 on 2007-09-12
I really don't have any idea, but I suspect that it isn't working in the dhclient.conf file because the router information actually is being sent in the DHCP response.  I think that the route is getting deleted later by something else that starts up.  That's also why you have to restart networking after booting.

I also noticed you had the eth1 UP at the same time in an earlier ifconfig, and it is also DHCP configured, and the default route from that also gets dropped.

Have you tried disabling hamachi from starting up at boot?  I'm suspecting it has something to do with that.

---

### Post by topher200 on 2007-09-12
I have tried disabling hamachi at boot- it was one of the first things I tried, but I think I'm going to try again. This is the startup script used to start hamachi:
```
#!/bin/sh
# Hamachi startup script
# Original contributor post found at http://forums.hamachi.cc/viewtopic.php?t=3421

hamachi_start() {
   echo "Starting hamachi..." 
   /sbin/tuncfg
   /usr/bin/hamachi -c /home/topher/.hamachi start
   /bin/chmod 760 /var/run/tuncfg.sock
   /bin/chgrp topher /var/run/tuncfg.sock
}

hamachi_stop() {
   echo "Stopping hamachi..."
   killall tuncfg
   /usr/bin/hamachi -c /home/topher/.hamachi stop
}

hamachi_restart() {
   hamachi_stop
   sleep 1
   hamachi_start
}

case "$1" in
'start')
   hamachi_start
   ;;
'stop')
   hamachi_stop
   ;;
'restart')
   hamachi_restart
   ;;
*)
   hamachi_start
esac
```

It looks like one of the major things it does is start tuncfg. I remember having to install it while configuring hamachi- and I think it was some kind of driver, but I'm not sure. It seems to me like the most likely thing that would be causing interference, so I'm going to play around with that for a while.

---

### Post by topher200 on 2007-10-16
So I tried to find other files that may be interfering, but nothing came up, and I wrote a script to add the default gateway every time I logged on. That worked fine, until this week I realized that I was connected to the internet before running the script. I haven't had to run it since. Apparently, some update has fixed the problem.

Thanks for all your help. I didn't mean to just leave the thread unanswered before, but I just had nothing new to add. I'm marking it solved. Thanks again.

---

