---
title: "No internet ubuntu server"
date: 2016-02-05
forum: Networking &amp; Wireless
---

### Post by george138 on 2016-02-05
Hello All

I just installed Ubuntu server 14.0.4.3 LTS and am VERY new to linux. It is the only thing on that computer. I was trying to install vsftpd and it would fail everytime. I did a ifconfig and all looks good except the last line under lo   It is RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)    If I ping my router ping my router it works but if I try to ping out side on the internet if fails.  Any ideas?

Thanks alot everyone for the help

---

### Post by chili555 on 2016-02-05
Where and how did you set the IP address? In /etc/network/interfaces? Or where?

---

### Post by george138 on 2016-02-05
yes  vim /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gatway 192.168.1.254
dns-nameserver 8.8.8.8 192.168.1.254



root@ubuntuserver:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:0c:6b:98
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe0c:6b98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:63621 (63.6 KB)  TX bytes:207302 (207.3 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by chili555 on 2016-02-05
> # The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gatway 192.168.1.254
dns-nameserver 8.8.8.8 192.168.1.254
Do you perhaps have a couple of typos here? I recommend:```
# The loopback network interface
auto lo
iface lo inet loopback


# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.251
netmask 255.255.255.0
gat[COLOR="#FF0000"]e[/COLOR]way 192.168.1.254
dns-nameserver[COLOR="#FF0000"]s[/COLOR] 8.8.8.8 192.168.1.254

```After you make the changes, restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```And check:```
ping -c3 192.168.1.254
ping -c3 www.ubuntu.com
```If you get ping returns from the latter, you are all set.

---

### Post by george138 on 2016-02-05
root@ubuntuserver:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:0c:6b:98
          inet addr:192.168.1.251  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe0c:6b98/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:680 errors:0 dropped:0 overruns:0 frame:0
          TX packets:673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:57230 (57.2 KB)  TX bytes:129946 (129.9 KB)


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:11 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1348 (1.3 KB)  TX bytes:1348 (1.3 KB)


That worked  thanks alot

---

### Post by chili555 on 2016-02-05
I'm glad it's working! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

