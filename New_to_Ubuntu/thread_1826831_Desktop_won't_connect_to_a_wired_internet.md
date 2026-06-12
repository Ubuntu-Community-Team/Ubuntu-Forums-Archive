---
title: "Desktop won't connect to a wired internet"
date: 2011-08-17
forum: New to Ubuntu
---

### Post by jjsha2 on 2011-08-17
Hello All,

I have used ubuntu awhile but never had a major issue. Until now...

My problem is that my desktop computer will not connect to the internet.

The network manager is enabled, but it just says "wired Network Disconnected" 

The setup I have is a Netgear DG834G modem/router which provides an internet connection. The Desktop is connected via an Ethernet cable to the router. (I have tested the cable & modem with my laoptop & it works fine).

The desktop has a clean install of Ubuntu 11.04

if I type sudo lshw -C network into the terminal I get:

shaw@shaw-G41MT-ES2L:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller 
       vendor: Realtek Semiconductor Co., Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 03 
       serial: 6c:f0:49:61:1d:aa 
       size: 10Mbit/s 
       capacity: 1Gbit/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       resources: irq:42 ioport:de00(size=256) memory:fdeff000-fdefffff memory:fdef8000-fdefbfff memory:fde00000-fde1ffff 


whereas if config yields:

shaw@shaw-G41MT-ES2L:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:61:1d:aa  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:42 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:14240 (14.2 KB)  TX bytes:14240 (14.2 KB) 

Any ideas what is wrong?

Cheers

---

### Post by aeiah on 2011-08-17
does sudo dhclient give you anything? this asks for a dhcp request.

---

### Post by jjsha2 on 2011-08-17
Thanks for the help :)

Doesn't seem to do / change anything.

---

### Post by jjsha2 on 2011-08-17
Update:

I tried booting up the desktop from a live ubuntu **10.04** disc.

Still would not connect, but inputing "sudo dhclient" gave:

ubuntu@ubuntu:~$ sudo dhclient 
There is already a pid file /var/run/dhclient.pid with pid 3039 
killed old client process, removed PID file 
Internet Systems Consortium DHCP Client V3.1.3 
Copyright 2004-2009 Internet Systems Consortium. 
All rights reserved. 
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/) 

Listening on LPF/eth0/6c:f0:49:61:1d:aa 
Sending on   LPF/eth0/6c:f0:49:61:1d:aa 
Sending on   Socket/fallback 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13 
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11 
No DHCPOFFERS received. 
No working leases in persistent database - sleeping. 

Based off this, I am thinking the network card on-board the motherboard is faulty. I am considering putting in a spare network card I have (which I know works) in the computer and seeing if that works. Is this a good idea?

Thanks for your assistance so far :)

---

### Post by babakott on 2011-08-17
You could try:
```
ifconfig eth0 <ip address> netmask <netmask> up
```

Then check your /etc/resolv.conf and see if there are nameservers.
If not edit it and add

nameserver <yournsip>
nameserver <yournsip>

If you can connect after doing those, we know its just a configuration issue that we can tackle. If not, then it may be the nic card after all.

---

### Post by jjsha2 on 2011-08-17
how do I know what ip address and netmask to use? Can I get those off my other computer (which will connect via wire)?

---

### Post by babakott on 2011-08-17
> **jjsha2 said:**
> how do I know what ip address and netmask to use? Can I get those off my other computer (which will connect via wire)?

Yeah. See what your IP is on your other machine. Then change the last digigt to something like 100. Ping it to make sure its not in use. Use that ip

If you other computer is Windows use ipconfig /all to get the above info and the DNS entries.

If it is Linux get your ip from ifconfig and nameservers from /etc/resolv.conf.
+++Forgot a step+++
After doing the ifconfig eth0 <ip address> netmask <netmask> up
do=>  route add default gw <ip address of the gateway> (the gateway is the ip of your router. You can get it from ifconfig and ipconfig /all)
Then your nameservers.
Don't reboot after you do this, and check to see if you have a connection.

---

### Post by jjsha2 on 2011-08-18
Okay, so my other (linux) laptop computer gives an output for ifconfig of:

ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:61:37:f3  
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:8cff:fe61:37f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4793 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4277 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:4604701 (4.6 MB)  TX bytes:585911 (585.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:234 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19981 (19.9 KB)  TX bytes:19981 (19.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:11:ae:af  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:e0ff:fe11:aeaf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50363 (50.3 KB)  TX bytes:23898 (23.8 KB)

so, based off this, I put into the desktop (and got):

shaw@shaw-G41MT-ES2L:~$ ifconfig eth0 192.168.0.100 netmask 255.255.255.0 upSIOCSIFADDR: Permission denied 
SIOCSIFFLAGS: Permission denied 
SIOCSIFNETMASK: Permission denied 
SIOCSIFFLAGS: Permission denied 
shaw@shaw-G41MT-ES2L:~$ sudo ifconfig eth0 192.168.0.100 netmask 255.255.255.0 up 
[sudo] password for shaw: 
shaw@shaw-G41MT-ES2L:~$ 

I think that worked?

But with the next step, which number from the ifconfig result is the "ip address of the gateway"? Is it the one labeled "Bcast"?

I then went to have a look for the /etc/resolv.conf file, but it does not exist on the desktop. (I found it on my laptop, however) I don't suppose this could be causing a few issues?

Cheers

---

### Post by im.saravanan on 2011-08-19
Hi friend,

check this thread, [http://ubuntuforums.org/showthread.php?p=11166792&posted=1#post11166792](http://ubuntuforums.org/showthread.php?p=11166792&posted=1#post11166792)

for Step-by-step guidance

---

