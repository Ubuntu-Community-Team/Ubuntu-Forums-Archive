---
title: "Nforce4 based onboard NIC"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by Davepet on 2005-05-30
System specs:
AMD64 3200
Gigabyte GA K8NF-9
1GB ram

I built this new system last week & the only thing I haven't been able to get working is the onboard NIC. I've downloaded & installed nvidia's drivers & they seem to be loading, but I can't even ping my router:
_________________________________________________________________________
root@davepet:/home/davepet # ifconfig
eth0 Link encap:Ethernet HWaddr 00:0F:EA:8AB6
inet6 addr: fe80::20f:eaff:fe8a:dbd6/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:54 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 b) TX bytes:31572 (30.8 KiB)
Interrupt:10 Base address:0x4000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:97137 errors:0 dropped:0 overruns:0 frame:0
TX packets:97137 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:7324634 (6.9 MiB) TX bytes:7324634 (6.9 MiB)


root@davepet:/home/davepet # ifup eth0
ifup: interface eth0 already configured

root@davepet:/home/davepet # ping 192.168.0.1
connect: Network is unreachable
_________________________________________________________

Ubuntu also loads the open source (reverse engineered) nvidea driver "forcedeth" which should be removed from the startup file according to nvidia. Can anyone tell me which file I need to edit? 
Disableing forcedeth after boot still doesn't get things working , & the Ubuntu networking config tool will let me seem to enable eth0, but then it unchecks itself in a few seconds.

Short of sticking another NIC in the machine, I'm out of ideas & I'd kinda like to get the onboard card working.

Thanks,
Dave

---

### Post by Davepet on 2005-06-05
I got the NIC working, but man am I  embarassed


I was digging through the log files & discovered that during boot up it kept trying to get a DHCP address but it wasn't getting a response......

So I checked the network connecter on the back & sure enough it wasn't seated properly (It *DID* look like it was seated properly, though).

I'm typing this on the new box....  

Dave

---

