---
title: "Connection problem -- on ethernet"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by mahiyar on 2007-05-02
Hi,
 I use ethernet to connect to the internet using pppoe protocol. Till yesterday there was no problem at all (10 days of use in feisty and three months in edgy). In feisty there are two connections one for wired, and one for eth0 I guess, both connect well but no internet even though I can see few packets exchanged to and fro. I'am not at all an expert so I have attached thumbnails of whatever I thought is necessary. I have made file descriptions as user friendly as possible.
 
BTW: I have another edgy install on the same computer and that too shows the same conky behaviour, Windows connections works fine though.

---

### Post by mahiyar on 2007-05-03
Hey guys, unable to connect t o the internet is really a question of life and death for me, In the mean time I have done the following things without any success...
1) Change the MTU using CLI - Unsuccessfull.
2) Run pppoeconf -- Unsuccessfull, except that there is now a error message that it cannot get the DNS. Surprisingly the same error is replicated in my edgy install.

---

### Post by mahiyar on 2007-05-03
I do not know why isnt anybody answering my post, is it because my question is too tough or my english is wrong or what. Anway going ahead I have done the following things without success
 
1) Blacklist ipv6.
2) Booted from 7.04 live cd without avail, same problem was observed there.
 
Now another intresting thing is that when I remove the wire fro the back of my LAN card the wired connection box disconnects however the other pppo box stays connected? Is this normal? I tried this when in live cd.

---

### Post by mahiyar on 2007-05-03
Seems like this is becoming blog of sorts. Another live cd - Knoppix fails to connect, same problem pppoeconf works fine but no internet. Now what does windows do to handle connection differently then Linux. This problem it seems is certainly not due to Ubuntu, but something to do with the way linux treats differently than windows, I also asked my service provider he is at a loss to explain, is this problem related to windows? **Am getting desperate please help.**

---

### Post by dbott67 on 2007-05-03
Can you please post the output of the following commands:

1. Interfaces file:
```
dbott@feisty:~$ **cat /etc/network/interfaces** 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

```2. ifconfig -a
```
dbott@feisty:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:579776 errors:0 dropped:0 overruns:0 frame:0
          TX packets:474754 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:385862054 (367.9 MiB)  TX bytes:71295585 (67.9 MiB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:484422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:484422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52744400 (50.3 MiB)  TX bytes:52744400 (50.3 MiB)

```3. Network Hardware
```
dbott@feisty:~$ **sudo lshw -C network**
Password:
  *-network               
       description: Ethernet interface
       product: RTL8139 Ethernet
       vendor: D-Link System Inc
       physical id: b
       bus info: pci@02:0b.0
       logical name: eth0
       version: 10
       serial: 00:50:ba:c0:a7:55
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.106 latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: ioport:b000-b0ff iomemory:be800000-be8000ff irq:16

```4. Routing table:
```
dbott@feisty:~$ **route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

```5. Firewall status:
```

dbott@feisty:~$ **sudo iptables -L**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   
```-Dave

---

### Post by mahiyar on 2007-05-03
At last a glimmer of hope. Please remember that I have to go to and fro from windows to linux.

---

### Post by dbott67 on 2007-05-03
If you have a USB thumb drive (or floppy or some other removable media you can write to) you can use the 'redirect' function to write the output of the commands to a file and then copy them to the USB.  Start in your home directory (***cd ~***):

```
cat /etc/network/interfaces > interfaces.txt
``````
ifconfig -a > ifconfig.txt
``````
sudo lshw -C network > lshw.txt
``````
route -n > route.txt
``````
sudo iptables -L > iptables.txt
```Copy all 5 files to floppy/USB, bring them over to Windows and then post them here.  All four files should be in your home directory.

-Dave

---

### Post by mahiyar on 2007-05-03
Thanks for all the help. I have one ntfs partition which I have made read/write and am using the same to share. Here are the outputs. I'am sure there is no problem with Ubuntu as the same problem is exhibited in edgy(seperate partition), 7.04 live cd and even knoppix live cd. SOme problem with my service provider maybe? but what? And working in windows.
 
BTW this output is after the so called connection is connected.
 
[FONT=Courier New][SIZE=2]cat /etc/network/interfaces[/SIZE][/FONT]
> 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ cat /etc/network/interfaces[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]auto lo[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface lo inet loopback[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto eth1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface eth1 inet dhcp[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto eth2[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface eth2 inet dhcp[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto ath0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface ath0 inet dhcp[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto wlan0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface wlan0 inet dhcp[/COLOR][/FONT][/SIZE]
 
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto dsl-provider[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]iface dsl-provider inet ppp[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]provider dsl-provider[/COLOR][/FONT][/SIZE]
 
 
 
[SIZE=2][FONT=Courier New][COLOR=#000000]iface eth0 inet dhcp[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]auto eth0[/COLOR][/FONT][/SIZE]
 

 
ifconfig -a
> 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ ifconfig -a[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]eth0 Link encap:Ethernet HWaddr 00:08:A1:78:37:B4 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX packets:5449 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]TX packets:3673 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]collisions:0 txqueuelen:1000 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX bytes:433186 (423.0 KiB) TX bytes:393952 (384.7 KiB)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Interrupt:16 Base address:0x8c00 [/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]eth0:avah Link encap:Ethernet HWaddr 00:08:A1:78:37:B4 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]inet addr:169.254.7.19 Bcast:169.254.255.255 Mask:255.255.0.0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Interrupt:16 Base address:0x8c00 [/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]lo Link encap:Local Loopback [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]inet addr:127.0.0.1 Mask:255.0.0.0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]inet6 addr: ::1/128 Scope:Host[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]UP LOOPBACK RUNNING MTU:16436 Metric:1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX packets:4 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]TX packets:4 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]collisions:0 txqueuelen:0 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX bytes:200 (200.0 b) TX bytes:200 (200.0 b)[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]ppp0 Link encap:Point-to-Point Protocol [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]inet addr:202.149.32.29 P-t-P:202.63.175.78 Mask:255.255.255.255[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1492 Metric:1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX packets:3574 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]TX packets:3624 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]collisions:0 txqueuelen:3 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]RX bytes:218789 (213.6 KiB) TX bytes:306144 (298.9 KiB)[/COLOR][/FONT][/SIZE]
 
 

 
lshw -C network
> 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo lshw -C network[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]*-network [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]description: Ethernet interface[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]product: RTL-8139/8139C/8139C+[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]vendor: Realtek Semiconductor Co., Ltd.[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]physical id: 2[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]bus info: pci@02:02.0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]logical name: eth0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]version: 10[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]serial: 00:08:a1:78:37:b4[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]size: 100MB/s[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]capacity: 100MB/s[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]width: 32 bits[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]clock: 33MHz[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]resources: ioport:b800-b8ff iomemory:feaffc00-feaffcff irq:16[/COLOR][/FONT][/SIZE]
 

 
route -n
> 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ route -n[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]Kernel IP routing table[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Destination   Gateway    Genmask         Flags  Metric Ref Use Iface[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]202.63.175.78  0.0.0.0   255.255.255.255   UH    0      0   0  ppp0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]169.254.0.0    0.0.0.0   255.255.0.0       U     0      0   0  eth0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]0.0.0.0        0.0.0.0   0.0.0.0           U     0      0   0  ppp0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]0.0.0.0        0.0.0.0   0.0.0.0           U    1000    0   0  eth0[/COLOR][/FONT][/SIZE]
 

 
iptables
```

[SIZE=2][COLOR=#000000][FONT=Courier New]mahiyar@mahiyar-desktop:~$ sudo iptables -L[/FONT][/COLOR][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Chain INPUT (policy ACCEPT)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]target     prot opt source               destination         [/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]Chain FORWARD (policy ACCEPT)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]target     prot opt source               destination         [/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]Chain OUTPUT (policy ACCEPT)[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]target     prot opt source               destination         [/COLOR][/FONT][/SIZE]
 

```

---

### Post by dbott67 on 2007-05-03
I haven't used pppoe client before, so I don't know if your configuration looks proper.  The one thing I do notice is that your routing table lacks a default gateway.  The default gateway should be the IP of your ppp0 adapter (which may change from time-to-time).  In the previous session it was [COLOR=Blue]202.63.175.78[/COLOR]:
```
sudo route add -net default gw [COLOR=Red]**123.123.123.123**[/COLOR] dev ppp0
```where 123.123.123.123 is the IP address of ppp0.  Before running this command, login to Ubuntu and type:
```
ifconfig -a
```Look for the IP address that is bound to the ppp0 adapter & use that one in the above command instead of 123.123.123.123.

After that, try getting on the internet.

-Dave

---

### Post by mahiyar on 2007-05-03
No -- does not work. Tried that, tried restarting network also. Tried disconnectiong the network from windows before moving on to Ubuntu, but no hope. I can see the faint glimmer of hope too go away? Like it or not I guess I have to turn to Windows.

---

### Post by mahiyar on 2007-05-04
Continuing on the attached thumbnail contains the output of plog, there are two lines that are troubling me.
 
1)Not replacing the existing defaut route through eth0.
2)Cannot determine ethernet address for proxy ARP.
 
Are these two lines OK?

---

### Post by mahiyar on 2007-05-04
Bump

---

### Post by sdide on 2007-05-04
I have little experience wiht ppp, but could you post what is running on your system? 
ie: 

~# ps -ef | grep ppp

---

### Post by zekica on 2007-05-04
@mahiyar:
note: you should type all commands as root (prefix them with **sudo**)

> mahiyar@mahiyar-desktop:~$ route -n
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
202.63.175.78 0.0.0.0 255.255.255.255 UH 0 0 0 ppp0
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 0.0.0.0 0.0.0.0 U 0 0 0 ppp0
0.0.0.0 0.0.0.0 0.0.0.0 U 1000 0 0 eth0

can you try to do the following:
type: **ifconfig ppp0**
look for: **P-t-P:** and do:
and: **ping <p-t-p address>**

If that works, you can try:
**route del default**. Repeat that several times (until you get: **SIOCDELRT: No such process**)
after that, type:
**route add default dev ppp0**
and try: **ping 209.85.129.99** (one of IP addresses of [www.google.com)](www.google.com)).
if that works, you have a problem with DNS, and to fix this, you should first check if there is a file: /etc/ppp/resolv.conf (**ls /etc/ppp**), and if there is, type: **cp /etc/ppp/resolv.conf /etc/resolv.conf**, and everything should be working. If this file doesn't exist, you can ask your provider for DNS addresses and type them in Ubuntu's Network Configuration.

After this, everything should be working (try to open Firefox).

Now, try to reboot Ubuntu and see if everything works, if it doesn't, again type: **rotue del default**, again several times if needed and after that **route add default dev ppp0**.

If that works, then you can edit file rc.local (**sudo gedit /etc/rc.local**) and right above line **exit 0**, add:
[B]/sbin/route del default
/sbin/route del default
...
/sbin/route add default dev ppp0[/B]

then restart Ubuntu again and see if it works.

---

### Post by mahiyar on 2007-05-04
Thanks Zekica and sdide, I will try all that the moment I get back home on my Linux box.
 
@zekica **ping <p-t-p> **works, the balance steps I will try.
 
Thanks again

---

### Post by mahiyar on 2007-05-04
These are the outputs
 
```

[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo ifconfig ppp0[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]Password:[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]ppp0      Link encap:Point-to-Point Protocol  [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         inet addr:221.128.174.235  P-t-P:202.63.175.78  Mask:255.255.255.255[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         RX packets:41 errors:0 dropped:0 overruns:0 frame:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         TX packets:108 errors:0 dropped:0 overruns:0 carrier:0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         collisions:0 txqueuelen:3 [/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]         RX bytes:4244 (4.1 KiB)  TX bytes:6551 (6.3 KiB)[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ ping 202.63.175.78[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]PING 202.63.175.78 (202.63.175.78) 56(84) bytes of data.[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=1 ttl=64 time=0.530 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=2 ttl=64 time=0.685 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=3 ttl=64 time=0.824 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=4 ttl=64 time=0.685 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=5 ttl=64 time=0.844 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=6 ttl=64 time=0.532 ms[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]64 bytes from 202.63.175.78: icmp_seq=7 ttl=64 time=0.499 ms[/COLOR][/FONT][/SIZE]
 
[SIZE=2][FONT=Courier New][COLOR=#000000][1]+  Stopped                 ping 202.63.175.78[/COLOR][/FONT][/SIZE]
[SIZE=2][COLOR=#000000][FONT=Courier New]mahiyar@mahiyar-desktop:~$ route del default[/FONT][/COLOR][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]SIOCDELRT: Operation not permitted[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo route del default[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo route del default[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo route del default[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]SIOCDELRT: No such process[/COLOR][/FONT][/SIZE]
 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo route add default dev ppp0[/COLOR][/SIZE][/FONT]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ ping 209.85.129.99[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]PING 209.85.129.99 (209.85.129.99) 56(84) bytes of data.[/COLOR][/FONT][/SIZE]
 
 
[SIZE=2][FONT=Courier New][COLOR=#000000][2]+  Stopped                 ping 209.85.129.99[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ [/COLOR][/FONT][/SIZE]
 
 
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo route -n[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Kernel IP routing table[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]202.63.175.78   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0[/COLOR][/FONT][/SIZE]
[SIZE=2][FONT=Courier New][COLOR=#000000]mahiyar@mahiyar-desktop:~$ [/COLOR][/FONT][/SIZE]
 

```
 
The next step I cannot complete, I cannot ping the google site, the packets are sent however there is no answer.
 
Thanks

---

### Post by mahiyar on 2007-05-04
Sdide here is your required output,
 
[FONT=Courier New][SIZE=2][COLOR=#000000]mahiyar@mahiyar-desktop:~$ sudo ps -ef | grep ppp
root      6348     1  0 19:11 ?        00:00:00 /usr/sbin/pppd call dsl-provider
mahiyar   desktop:~$[/COLOR][/SIZE][/FONT]

---

### Post by dunedust on 2007-05-04
same problem here

[http://ubuntuforums.org/showthread.php?t=432347](http://ubuntuforums.org/showthread.php?t=432347)

hope there's some solution to this 
don wanna go back to windows

---

### Post by mahiyar on 2007-05-04
@dunedust -- It is almost certain that we share the same ISP, now we depend on the forum and its experts to tell us that what the ISP would have done to enable windows to connect and Linux (of all forms) to fail. I have even tried Knoppix, edgy live cd, edgy install, festy live cd, feisty install, and in each one of them the pppoe connected but internet failed.
 
BTW: Which part of mumbai do u stay?

---

### Post by dunedust on 2007-05-04
i have filed a report in launchpad ( 6090) I am hoping that will help 
i was thinking of reinstalling Ubuntu but i don't think that will work as I am having the same problems using the live cd

hope something works out

---

### Post by mahiyar on 2007-05-05
No reinstalling is certainly not going to help, as I said even live cd's have the same problem and if you have problem in your live cd rest assured that problems is sure to carry on in your install. We can only take it up with our isp's, but even that will not help I guess.

---

### Post by sdide on 2007-05-05
Hey, 

you could try running the pppd with option "defaultroute"

ie do (as root or with sudo)

~# ps -ef | grep ppp 

find the pppd pid, 
(in your entry before - "root 6348 1 0 19:11 ? 00:00:00 /usr/sbin/pppd call dsl-provider" - its 6348)

kill the process.

~# kill <pid>

restart pppd with defaultroute arg.

~#  /usr/sbin/pppd defaultroute call dsl-provider

---

### Post by zekica on 2007-05-05
Hm, i really do not know what is happening, but can you try to do the following:
**tracepath 209.85.129.99**
and post the output...

---

### Post by mahiyar on 2007-05-05
Thanks one and all for the support during "tough" times, however it turned out that the solution was with the isp. Now everything is back to normal, no more windows every day.

---

