---
title: "Need help with wireless!"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Lord Voldemort on 2010-11-19
So, day 1 of Linux/Ubuntu for me. 
I'm running Ubuntu 10.10 with Gnome of some sort. 

I got it set up with the wired connection, but I've been rather frustrated trying to connect to my existing wireless network. I have been searching around for quite a while now, but with little luck. I did learn (is this true?) that Ubuntu 10.10 comes with Network Manager. How can I open network manager? Sorry if this is elementary, but I've been searching quite a bit and can't figure this out. Is it the up/down arrow in the top right bar? It only allows VPN connections when I go under wireless connection.

---

### Post by I8NY on 2010-11-20
go to system>preferences>network connection and there will be a tab for wireless.  In the wireless tab click add in the menu and input all the need information to connect to your wifi.  It should work after that.

---

### Post by mr_luksom on 2010-11-21
Yes - it is the up/down arrow. When you are connected wirelessly it shows a radio.

Just to check to see if ubuntu can see you wireless card.

List network devices:

```
lshw - C network
```

See what is currently configured:

```
ifconfig
```

If you can post the results of these, it might show us the issue.

---

### Post by Lord Voldemort on 2010-11-21
Thanks! I figured out that I had a driver issue, and apparently everything's working right now, but it says my computer has a Wireless network connection and that it is active and 100%, but for some reason it still does not connect to the internet. Would the information that the person below asked for still be of use here?

---

### Post by Lord Voldemort on 2010-11-21
nitin@ubuntu:~$ lshw - C network
Hardware Lister (lshw) - B.02.14
usage: lshw [-format] [-options ...]
       lshw -version

	-version        print program version (B.02.14)

format can be
	-html           output hardware tree as HTML
	-xml            output hardware tree as XML
	-short          output hardware paths
	-businfo        output bus information

options can be
	-class CLASS    only show a certain class of hardware
	-C CLASS        same as '-class CLASS'
	-c CLASS        same as '-class CLASS'
	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
	-quiet          don't display status
	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)
	-numeric        output numeric IDs (for PCI, USB, etc.)

---

### Post by Lord Voldemort on 2010-11-21
nitin@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:b9:be:1d:ff  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:b9ff:febe:1dff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4377 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2983 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4145699 (4.1 MB)  TX bytes:444307 (444.3 KB)
          Interrupt:27 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 78:e4:00:1f:12:b8  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::7ae4:ff:fe1f:12b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:3164
          TX packets:11 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2797 (2.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

---

