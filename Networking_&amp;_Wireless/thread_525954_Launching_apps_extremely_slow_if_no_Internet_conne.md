---
title: "Launching apps extremely slow if no Internet connection?"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by Tsu Dho Nimh on 2007-08-14
This got ZERO response in the beginner area ...
[http://ubuntuforums.org/showthread.php?t=523422](http://ubuntuforums.org/showthread.php?t=523422) 

Apps such as the screenshot maker, terminal, and notepad that have no reason to need a live internet connection are recently extremely slow to launch without one. They eventually launch, but the little spinner runs for 10-30 seconds. Other apps as well are having issues ... OpenOffice, graphics viewers, etc.

I have been accepting updates as they appear ... has something buggy been introduced?

I haven't a clue where to start looking for this problem.

*******
I tried one remedy, which was editing the hosts file, and it did no good. The slow launching persists unless the computer is connected to the Internet.

Code:
127.0.0.1 localhost
127.0.1.1 computername

I added my hostname to the first line as suggested:

Code:
127.0.0.1 localhost computername
127.0.1.1 computername

---

### Post by noob12 on 2007-08-15
When you connect to the internet, how are you connected?

When you disconnect, what are you doing to disconnect?

During a period in which you're having this problem, can you capture these
to post later?
```

ifconfig -a

cat /etc/network/interfaces

cat /etc/nsswitch.conf

top -b -n 1 | head -15

```

---

### Post by Tsu Dho Nimh on 2007-08-16
Connection is via mobo's built-in ethernet, through a DSL router.  100MB local network. 
Driver = forcedeth 

It's a near-vanilla 64-bit Ubuntu 7.04 install, on a decently powered system. I have not mucked with the networking parts.

I first saw the problem when the DSL line was having problems at the phone company's end and there was no internet connection at all. 

It doesn't matter if I rudely disconnect the cable from the router, disable networking using the "enable/disable" icon on the toolbar, or power down the router ... no internet = slow apps. When the internet connection is down, I can still reach the local network printer and file server but it is also very slow. 

I captured that data with the system working OK and I'll disconnect to get it when it's slow after I've done some work that has a deadline.

---

### Post by noob12 on 2007-08-16
See if anything improves if you stop networking using ```
sudo /etc/init.d/networking stop
```

---

### Post by Tsu Dho Nimh on 2007-08-23
As requested, I ran each of these commands when connected and when disconnected to the wired network. I have no clue what all this means, but ifconfig gave different results for disconnected.

ifconfig -a 
cat /etc/network/interfaces
cat /etc/nsswitch.conf
top -b -n 1 | head -15


*************************
ifconfig -a   (when working)

eth0      Link encap:Ethernet  HWaddr 00:16:EC:30:75:13  
          inet addr:192.168.6.130  Bcast:192.168.6.255  Mask:255.255.255.0
          inet6 addr: fe80::216:ecff:fe30:7513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:803452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:581159 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:708311058 (675.4 MiB)  TX bytes:87704682 (83.6 MiB)
          Interrupt:20 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:896 (896.0 b)  TX bytes:896 (896.0 b)


ifconfig -a  (disconnected via toolbar icon)

eth0      Link encap:Ethernet  HWaddr 00:16:EC:30:75:13  
          inet6 addr: fe80::216:ecff:fe30:7513/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4121999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2819690 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3975195676 (3.7 GiB)  TX bytes:837421992 (798.6 MiB)
          Interrupt:20 Base address:0xe000 
[B]
eth0:avah Link encap:Ethernet  HWaddr 00:16:EC:30:75:13  
          inet addr:169.254.4.178  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xe000 [/B]

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:482 errors:0 dropped:0 overruns:0 frame:0
          TX packets:482 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:43342 (42.3 KiB)  TX bytes:43342 (42.3 KiB)

[B]vmnet1    Link encap:Ethernet  HWaddr 00:50:56:C0:00:01  
          inet addr:192.168.115.1  Bcast:192.168.115.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:861 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:C0:00:08  
          inet addr:192.168.9.1  Bcast:192.168.9.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:860 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)[/B]


*******************
cat /etc/network/interfaces   (working)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp


cat /etc/network/interfaces  (disconnected)

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp



*******************************

cat /etc/nsswitch.conf   (working)
# /etc/nsswitch.conf:
# $Header: /var/cvsroot/gentoo/src/patchsets/glibc/extra/etc/nsswitch.conf,v 1.1 2006/09/29 23:52:23 vapier Exp $


#passwd:    db files nis
#shadow:    db files nis
#group:     db files nis

#hosts:       files nis dns
#networks:    files nis dns

#services:    db files
#protocols:   db files
#rpc:         db files
#ethers:      db files
#netmasks:    files
#netgroup:    files
#bootparams:  files

#automount:   files nis
#aliases:     files nis


cat /etc/nsswitch.conf   (disconnected) 
# /etc/nsswitch.conf:
# $Header: /var/cvsroot/gentoo/src/patchsets/glibc/extra/etc/nsswitch.conf,v 1.1 2006/09/29 23:52:23 vapier Exp $


#passwd:    db files nis
#shadow:    db files nis
#group:     db files nis

#hosts:       files nis dns
#networks:    files nis dns

#services:    db files
#protocols:   db files
#rpc:         db files
#ethers:      db files
#netmasks:    files
#netgroup:    files
#bootparams:  files

#automount:   files nis
#aliases:     files nis


*****************************

top -b -n 1 | head -15   (working)
top - 08:34:22 up 2 days, 16:43,  2 users,  load average: 0.29, 0.20, 0.12
Tasks:  90 total,   1 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.6%us,  0.5%sy,  0.0%ni, 91.7%id,  0.3%wa,  0.1%hi,  0.8%si,  0.0%st
Mem:   2060792k total,  1581076k used,   479716k free,   148220k buffers
Swap:   248996k total,    20380k used,   228616k free,   892468k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
24480 stephani  15   0 18900 1220  900 R  2.0  0.1   0:00.01 top                
    1 root      18   0  5064 1956  564 S  0.0  0.1   0:00.82 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.01 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.78 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper            
    7 root      12  -5     0    0    0 S  0.0  0.0   0:00.00 kthread     


top -b -n 1 | head -15   (disconnected) 
top - 15:43:35 up 9 days, 23:53,  2 users,  load average: 0.06, 0.20, 0.17
Tasks: 100 total,   1 running,  99 sleeping,   0 stopped,   0 zombie
Cpu(s):  6.2%us,  0.9%sy,  0.1%ni, 91.6%id,  0.4%wa,  0.1%hi,  0.8%si,  0.0%st
Mem:   2060792k total,  1886104k used,   174688k free,   217268k buffers
Swap:   248996k total,    46060k used,   202936k free,  1240680k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6702 stephani  17   0 18896 1236  900 R  1.9  0.1   0:00.01 top                
    1 root      18   0  5064 1912  520 S  0.0  0.1   0:00.92 init               
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.02 ksoftirqd/0        
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    5 root      10  -5     0    0    0 S  0.0  0.0   0:03.10 events/0           
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper            
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread          

*****************************

---

