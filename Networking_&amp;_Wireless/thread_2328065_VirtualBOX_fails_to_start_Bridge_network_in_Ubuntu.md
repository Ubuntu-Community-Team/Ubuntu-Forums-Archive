---
title: "VirtualBOX fails to start Bridge network in Ubuntu VM"
date: 2016-06-17
forum: Networking &amp; Wireless
---

### Post by Anshuman_Gholap on 2016-06-17
I have setup ubuntu server edition (version 16 LTS) in Virtualbox VM . the vm boots but gets stuck at "RAISING NETWORK INTERFACE" and it never starts network, i have manually run ifdown enp0s3 then ifupenp0s3 to get DHCP assign ip, there is no file called [COLOR=#333333][FONT=&amp] /etc/udev/rules.d/70-persistent-net.rules    
[/FONT][/COLOR]for me to delete. not sure whts the issue. 

you can see me doing the entire step in this video [https://youtu.be/NX-d5Zr_zTY?t=253](https://youtu.be/NX-d5Zr_zTY?t=253) . Aplogies about the song which got recorded accidentally  when i started listening to it to kill time. 

help. 

Edit: 

I have feeling i have to do something in interfaces. 

[IMG]http://i.imgur.com/FByxh1h.png[/IMG]


Okay, for anyone who cant bother to watch boring video, here are screengrabs .


1) Waiting to raise network interface.

 [IMG]http://i.imgur.com/xZtZgtR.png[/IMG]

2) machine is up, wih no IP .

[IMG]http://i.imgur.com/561HbaK.png[/IMG]

3) restarting network, still no IP.

[IMG]http://i.imgur.com/5Xy9pZd.png[/IMG]

4) IF DOWN  

[IMG]http://i.imgur.com/6T3mm9P.png[/IMG]

5) IF UP

[IMG]http://i.imgur.com/1LIHG6d.png[/IMG]

6) Finally , got IP, and netowork is working.

[IMG]http://i.imgur.com/fHH6oEV.png[/IMG]

---

### Post by Anshuman_Gholap on 2016-06-17
I did not solve this on the default network 1 adapter, after banging head on different configs, i had to add another adapter, and select BRIDGE-NETWORK on that iface, modify interface file like following and boom , i can ping in and ping out,. bothways. i think there is BUG either in UBUNTU distro or virtualbox network by not allowing bridging on network-adapter 1.

```

    * Documentation:  https://help.ubuntu.com/

7 packages can be updated.
7 updates are security updates.




Last login: Fri Jun 17 11:35:11 2016
ubuntu-admin@ubuntuVM:~$ ifconfig -a
enp0s3    Link encap:Ethernet  HWaddr 08:00:27:b1:0c:2f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


enp0s8    Link encap:Ethernet  HWaddr 08:00:27:ec:dc:82  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:27ff:feec:dc82/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:89 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13492 (13.4 KB)  TX bytes:11190 (11.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:12176 (12.1 KB)  TX bytes:12176 (12.1 KB)


ubuntu-admin@ubuntuVM:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


source /etc/network/interfaces.d/*


# The loopback network interface
auto lo
iface lo inet loopback
auto enp0s8
iface enp0s8 inet dhcp


# The primary network interface
#auto enp0s3
#allow-hotplug enp0s3
#iface enp0s3 inet static
#address 192.168.1.103
#netmask 255.255.255.0
#network 192.168.1.0
#gateway 192.168.1.254
#broadcast 192.168.1.255
#dns-search 192.168.1.1
#dns-nameservers 8.8.8.8 8.8.4.4
ubuntu-admin@ubuntuVM:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 enp0s8
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 enp0s8
ubuntu-admin@ubuntuVM:~$ ping google.com
PING google.com (216.58.220.14) 56(84) bytes of data.
64 bytes from google.com (216.58.220.14): icmp_seq=1 ttl=56 time=34.4 ms
64 bytes from google.com (216.58.220.14): icmp_seq=2 ttl=56 time=33.6 ms
^C
--- google.com ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1002ms
rtt min/avg/max/mdev = 33.670/34.077/34.484/0.407 ms

```

---

