---
title: "Wireless section removed from NM box"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by Icielost on 2009-08-09
Here's the facts: Was gifted a refurbished Del Mini 9 with Ubuntu/Gnome installed with no partitions. Ubuntu 8.04 Hardy Heron

When I first had it, it work fine, played music, got wireless, and had space.

After updates all of that dissappeared. Even wireless started acting funny.

Things I did: Removed programs for space on hard drive.

Discovered wireless option was not even listed in the box anymore, I rebooted. Nothing happend.

Unistalled and then reinstalled NM. Nothing changed.

Reinstalled bluetooth(one program deleted). Nothing.

Enabled network packages in the Synaptic Package Manager. Still nothing.

Did Terminal commands.Kept getting bash and some other thing saying command not found.Then got:

icie@icie:~$ ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:21:70:ca:3d:d3 
inet addr:192.168.1.73 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::221:70ff:feca:3dd3/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:6119 errors:0 dropped:0 overruns:0 frame:0
TX packets:2149 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:2688916 (2.5 MB) TX bytes:326851 (319.1 KB)
Interrupt:220 Base address:0x8000 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:9550 errors:0 dropped:0 overruns:0 frame:0
TX packets:9550 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:478348 (467.1 KB) TX bytes:478348 (467.1 KB)

icie@icie:~$ 
icie@icie:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

icie@icie:~$ lshw -C network
bash: lshw: command not found
icie@icie:~$ 
---------------------------------------------------------------------------------

Heres what it looks like since I can't get a screenshot:
________________
Wired Connection
o Auto Eth0
VPN Connections
Edit Connections
_______________

I dont have a LiveCD(any cd it all), Flash drive, external machines, and etc. Just a internet cable and the del mini infront of me.

I cant find anyone that has anywhere near the same problem as I do.Did I really screw up bad?Please help.Thanks in advance.

---

### Post by Icielost on 2009-08-09
Nevermind solved by this thread:[http://ubuntuforums.org/showthread.php?t=197102](http://ubuntuforums.org/showthread.php?t=197102).

---

