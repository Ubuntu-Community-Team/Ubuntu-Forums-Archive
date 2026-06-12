---
title: "[SOLVED] Internet &amp;amp; network problem"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by ogost on 2008-04-18
Good day everyone!

I'm running Ubuntu 7.10 on AMD64 (dualboot with Windows to share internet) and everything worked pretty much fine, until yesterday. Since I'm spending more time with Ubuntu now, I've decided to share the internet under Ubuntu too, so i've found some tutorials and followed them. It actually did work and everyone was happy, until the next reboot. Now I have internal network, but no internet. Right now I'm writing under XP and I can't find the tutorial I've followed :(

Here's some info:

```
 ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:13:D4:25:E4:19   
          inet addr:10.10.35.71  Bcast:10.10.255.255  Mask:255.255.0.0 
          inet6 addr: fe80::213:d4ff:fe25:e419/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:243 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:20961 (20.4 KB)  TX bytes:2662 (2.5 KB) 
          Interrupt:23 Base address:0x8000  
 
eth1      Link encap:Ethernet  HWaddr 00:14:78:09:AC:86   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 
          Interrupt:17 Base address:0xc000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b) 

```

```
#
# /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
#net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
#net.ipv4.conf.default.forwarding=1

# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1
```

---

### Post by SpaceTeddy on 2008-04-18
essentially, you need two things to do internet sharing 

1.) masquerading
2.) ip_forwarding

looking at your sysctl.conf, i'd say your ip_forwarding is turned off. 
remove the # in front of the following line to enable it upon boot:
```
#net.ipv4.conf.default.forwarding=1
```

if you do not wish to reboot after that and only test, use this command to enable the forwarding temporarily (to test of everything else was setup properly), you can use this command
```
sudo "echo 1 > /proc/sys/net/ipv4/ip_forward"
```

hope it helps :)

---

### Post by Kebabman on 2008-04-18
Just a quick note, rather than echo'ing 1 to /proc/sys/net/ipv4/ip_forward; you should use the following to set the sysctl ip_forward variable :

sudo sysctl -w net.ipv4.ip_forward=1

This is good practice to avoid possible problems as described [here]("http://ubuntuforums.org/showthread.php?t=23261").

---

### Post by ogost on 2008-04-18
I've forgot to mention something:

eth0 is the NICard connected to the internet.
eth1 is the one connected with my laptop with cross-over cable.

at the moment i've posted the first one the laptop was switched off.
I'll try uncommenting and hopefully will be back under Ubuntu :)

---

### Post by ogost on 2008-04-18
Thanks a lot! it worked! big big big thanks, guys! You're great!

---

