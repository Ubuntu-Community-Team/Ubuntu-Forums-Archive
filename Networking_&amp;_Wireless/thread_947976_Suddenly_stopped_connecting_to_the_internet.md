---
title: "Suddenly stopped connecting to the internet"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by cowznofsky on 2008-10-14
I have a 5yr old Dell set up with a dual-boot.  Just this past week, I often cannot connect to the internet in Ubuntu.  I'm a newbie, and I don't know how to troubleshoot this.  
If I boot into WinXP, I can always connect.  It's ethernet cable.

---

### Post by Iowan on 2008-10-14
Start with results of **ifconfig -a** to see if interface has an address.  Post contents of **/etc/network/interfaces** file. Occasionally, the interfaces fails to get a DHCP address and gets one via avahi (which usually doesn't allow internet access.)

---

### Post by cowznofsky on 2008-10-14
The interfaces file shows this:

auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

---

### Post by nexus604 on 2008-10-15
I have been encountering the same problem as cowznofsky, this has started since couple of hours i am able to connect when i boot through windows xp  but unable to connect through Kubuntu 
here are the details:

for ifconfig -a

eth0      

Link encap:Ethernet  
HWaddr 52:54:05:fe:f8:ad
inet6 addr: fe80::5054:5ff:fefe:f8ad/64 
Scope:Link          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3239 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:310992 (303.7 KB)  TX bytes:438 (438.0 B)
          Interrupt:20 Base address:0xd000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:428 (428.0 B)  TX bytes:428 (428.0 B)

and this is the contents of /etc/network/interfaces file

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf

provider dsl-provider
auto eth0
iface eth0 inet manual

Thanks in advance !!

---

### Post by thetechnaddict on 2008-10-15
Same issues here. Dell Latitude D410 - working one minute stopped suddenly. Connects on hardwire, no wireless at all.

output of ifconfig -a

eth0      Link encap:Ethernet  HWaddr 00:12:3f:21:73:e3  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::212:3fff:fe21:73e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1097 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1046 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1208454 (1.1 MB)  TX bytes:149765 (146.2 KB)
          Interrupt:16 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:f6:69:13  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0x2000 Memory:dfcff000-dfcfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1610 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1610 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:173865 (169.7 KB)  TX bytes:173865 (169.7 KB)

cat /etc/network/interfaces:

auto lo
iface lo inet loopback

I feared hardware failure.. any other suggestions?

---

### Post by thetechnaddict on 2008-10-15
Also here's output from $ iwconfig

lo        no wireless extensions.

eth1      radio off  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

---

### Post by mtrtm on 2008-10-15
I experienced what I believe was the same problem.  Additionally, logging in took ages, trying to "sudo -s" seemed to hang for several minutes, and attempts to connect to localhost by SSH was disconnected.

What solved the problem for me was (as root) to run restart the system logging utilities. You can do that with the command

"/etc/init.d/sysklogd restart"

After that, several hanging/queued actions were executed, and I could restart the network ("/etc/init.d/networking restart").

I hope this might help you.

---

