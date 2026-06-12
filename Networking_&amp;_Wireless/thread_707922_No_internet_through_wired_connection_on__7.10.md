---
title: "No internet through wired connection on  7.10"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Fire Hazard on 2008-02-25
I've recently re-installed Ubuntu Linux on my laptop and have internet connecting problems.  I had zero problems with the older version of Ubuntu, I think it was 7.04.  Anyways I use my laptop to connect to the internet through my University that uses DHCP to assign IPs and such.  This is a wired connection too by the way.

On the first attempt I wouldn't be able to connect at all about I could see in the bottom of the Firefox browser it was trying to connect to the webpage I have to log into in order to use the internet at my University.  But it would never connect.  Just state that it was trying to to connect to it.  Here is the ifconfig info from that session.

> firehazard@WMDv1:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:C0:9F:0D:D9:B8  
          inet addr:164.107.186.25  Bcast:164.107.186.127  Mask:255.255.255.128
          inet6 addr: fe80::2c0:9fff:fe0d:d9b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:266 errors:0 dropped:0 overruns:0 frame:0
          TX packets:156 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:63454 (61.9 KB)  TX bytes:23956 (23.3 KB)
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3638 (3.5 KB)  TX bytes:3638 (3.5 KB)




I thought it might just be that that location had changed and no longer wanted people to connect there.  So I went to a different location where I know I should be able to connect.  That time I didn't even get the message that the browser was trying to connect to the website that I have to log on too.  It didn't even time out but just sat there frozen like.  Here is my ifconfig from that session.

> eth0      Link encap:Ethernet  HWaddr 00:C0:9F:0D:D9:B8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000 

eth0:avah Link encap:Ethernet  HWaddr 00:C0:9F:0D:D9:B8  
          inet addr:169.254.9.34  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:213 errors:0 dropped:0 overruns:0 frame:0
          TX packets:213 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21340 (20.8 KB)  TX bytes:21340 (20.8 KB)



I've fiddled with connection by switching from roaming to DHCP and it showed the DNS server name but it didn't get me anywhere to fixing the problem.  I just don't understand how the old Ubuntu version worked fine without any intervention on my part and this updated version doesn't work.  My laptop is over 5 years old, not like it's bleeding edge or anything.  And I've never had any problems with Linux working with it's hardware.  Anyone one got any ideas on why I'm not connecting to the internet and how I might be able to fix it?

---

### Post by Iowan on 2008-02-25
The older versions didn't have the roaming option or the "Local zeroconf" option.  I can't say I really understand either, but school-of-hard-knocks suggests that```
eth0:avah Link encap:Ethernet HWaddr 00:C0:9F:0D:D9:B8
inet addr:169.254.9.34 Bcast:169.254.255.255 Mask:255.255.0.0
UP BROADCAST MULTICAST MTU:1500 Metric:1
Interrupt:11 Base address:0xa000 
```  pops up when eth0 fails to get an address via "normal" means.  You can try restarting networking after you connect to your "known good" point.  You might also verify in **/etc/networking/interfaces** that eth0 is still set for "auto".

---

### Post by mrsteveman1 on 2008-02-25
You can force dhcp to get a new IP lease by doing ```
sudo dhclient eth0
```

If you can get dhcp to retrieve an address, the entire network stack should be working fine. The only 2 things left are default route and DNS, which both should have been set by dhcp but might not have been.

Check these:

```
sudo route
sudo cat /etc/resolv.conf
```

Also try to ping 4.2.2.2 which is a DNS server for Level3, it should always be up. If you can ping that address it means everything works except the DNS setting in resolv.conf

---

### Post by Fire Hazard on 2008-02-28
Here's my **/etc/networking/interfaces** file.
```
auto lo
iface lo inet loopback



iface eth0 inet dhcp



auto eth0

```

Here's what the results are from your commands.  I hope my pinging was fine.  I only know how to ping from the install manual of Gentoo Linux.
```
firehazard@WMDv1:~$ sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
164.107.186.0   *               255.255.255.128 U     0      0        0 eth0
default         se3-gig4-2.net. 0.0.0.0         UG    0      0        0 eth0
firehazard@WMDv1:~$ sudo cat /etc/resolv.conf
search classroom.ohio-state.edu
nameserver 128.146.12.140
nameserver 140.254.64.5
firehazard@WMDv1:~$ ping -c 3 4.2.2.2
PING 4.2.2.2 (4.2.2.2) 56(84) bytes of data.

--- 4.2.2.2 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 1999ms
```

And the internet is still down.  Any ideas?

---

### Post by Shakeysteve on 2008-02-29
It seems your gateway ip address isn't beeing set, note the setting is blank, so ping & browsers don't know how to get out. I don't know how you can set that without using static ip.
Anyone else?

---

### Post by mrsteveman1 on 2008-02-29
See if you can ping se3-gig4-2.net because thats what the default route is set to. the 0.0.0.0 part is just the netmask, which is correct in this case.

The settings are OK but it might not work if you can't reach that machine (se3-gig4-2.net).

I do notice that se3-gig4-2.net isn't a globally available domain (i can't ping it), so perhaps it is an internal domain where you are.

---

### Post by Shakeysteve on 2008-03-02
My interest here is that I believe I have the same issue with 7.10.
DHCP is working. I can ping my ISP's DNS server, DNS is working as I can ping eg. [www.newscientist.com](www.newscientist.com) and get replies. Yet firefox sits at "connecting to xxxx", w3b (the terminal browser) does the same, and synaptic package manager fails to download anything.
6.06 works perfectly, 7.04 works after clicking connect on "enable wired connection" in network manager applet.
I had 7.10 working fine once, having upgraded through the versions, but then the HDD crashed. I was hoping to reinstall directly from 7.10 live CD.
Anyone know what the problem could be?

Thanks for any help!

Bug #197601

---

