---
title: "no network connection 8.10"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by DavidFourer on 2009-02-03
I upgraded from 8.04 to 8.10 3 days ago.  Works great but no network connection.  I found this giant thread with a dozen fixes:
[http://ubuntuforums.org/showthread.php?p=6062560#poststop](http://ubuntuforums.org/showthread.php?p=6062560#poststop)
I'm lost.  Maybe I should have come here first.

I have a few specific questions.
What is really my IP Address?  is it 192.168.254.104 like in this:
> david@davidf:~$ sudo dhclient eth0
[sudo] password for david:
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:14:22:da:6f:e2
Sending on   LPF/eth0/00:14:22:da:6f:e2
Sending on   Socket/fallback
DHCPREQUEST of 192.168.254.104 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.254.104 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.254.104 from 192.168.254.254
bound to 192.168.254.104 -- renewal in 913835058 seconds.

Or is it 192.168.254.254 like in this:
> ubuntu@ubuntu:~$ route -n | grep UG
0.0.0.0         192.168.254.254 0.0.0.0         UG    0      0        0 eth0

What is meant by "route" as in
> 3. Manually set up eth0 using ifconfig and route:
Code:
$ ifconfig eth0 10.0.0.10
$ route add default gw 10.0.0.2

I started trying to do this:
[http://ubuntuforums.org/showthread.php?p=6075466#post6075466](http://ubuntuforums.org/showthread.php?p=6075466#post6075466)  (I think that's the link)
Basically it says, 
Disable NetworkManager 
Manually set up eth0 using ifconfig and route 
Edit /etc/resolv.conf
I'm affraid I may have to undo some things.

I am able to get a  connection on this home computer by running my Ubuntu 7.10 Live CD.  That's how I'm getting on the net now, and also getting ifo on the connection.
The old network tools report:
> eth0
IP Address     192.168.254.104
Broadcast addr 255.255.255.255
Subnet Mask    255.255.255.0
Default Route  192.168.254.254
Primary DNS    192.192.254.254
Secondary DNS  0  .0  .0  .0
Hdwr address   00 14 22 DA 6F E2

Last resort, I ordered Ubuntu 8.04.2 CD.
Must get home/business computer connected.
That's way more than enough for now.
Thanks for your help

---

### Post by lykwydchykyn on 2009-02-03
> **DavidFourer said:**
> 
What is really my IP Address?  is it 192.168.254.104 like in this:

Yes, that's it.
> 
Or is it 192.168.254.254 like in this:

That would be your default gateway address -- i.e., the IP address of your router.
> 
What is meant by "route" as in

route is your default gateway, sometimes called default route.  It's an address where the computer sends data that isn't addressed to a computer on the local network.
> 
I started trying to do this:
[http://ubuntuforums.org/showthread.php?p=6075466#post6075466](http://ubuntuforums.org/showthread.php?p=6075466#post6075466)  (I think that's the link)
Basically it says, 
Disable NetworkManager 
Manually set up eth0 using ifconfig and route 
Edit /etc/resolv.conf
I'm affraid I may have to undo some things.

Is the dhclient output you posted above from the liveCD or your harddrive install?  Because the output you posted shows a functioning network situation, and if you have no internet connectivity after that command then either something is wrong upstream (your router, modem, ISP having trouble), or the problem is in the gateway or DNS settings.  Since your gutsy liveCD works, I'd have to guess one of the last two. 

> 
I am able to get a  connection on this home computer by running my Ubuntu 7.10 Live CD.  That's how I'm getting on the net now, and also getting ifo on the connection.
The old network tools report:

This is information obtained during a liveCD session, correct?

---

### Post by DavidFourer on 2009-02-03
> **lykwydchykyn said:**
> 
Is the dhclient output you posted above from the liveCD or your harddrive install?  Because the output you posted shows a functioning network situation, 
dhclient is from the hard-drive session, 8.10.
> eth0
IP Address 192.168.254.104
Broadcast addr 255.255.255.255
Subnet Mask 255.255.255.0
Default Route 192.168.254.254
Primary DNS 192.192.254.254
Secondary DNS 0 .0 .0 .0
Hdwr address 00 14 22 DA 6F E2
that is from the live CD session.

It's quite a pain to go back and forth between the two.  At least I figured  out I can keep my notes on a USB drive.

David

---

### Post by lykwydchykyn on 2009-02-03
If you're getting that output from dhclient on the HD session, your network card is working fine.  The question to figure out is why aren't you getting internet access.

As I mentioned before, it's likely either a problem with the gateway, or the DNS settings.

For gateway, just type "route".  Based on what you've posted, you should see the following in the output:
```

default         192.168.254.254    0.0.0.0         UG    100    0        0 eth0

```

If that's good, check your DNS settings.  That's in resolv.conf.  If you open /etc/resolv.conf, you should see a line like this:
```

nameserver 192.168.254.254

```

If you don't add it and see if that gives you your internet back.

Let me know where that takes you.

---

### Post by DavidFourer on 2009-02-03
> **lykwydchykyn said:**
> If you're getting that output from dhclient on the HD session, your network card is working fine.  The question to figure out is why aren't you getting internet access.

As I mentioned before, it's likely either a problem with the gateway, or the DNS settings.
I've got it working.  There were some problems as you suspected.

> david@davidf:~$ sudo route
[sudo] password for david: 
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
so I run dhlient again
> david@davidf:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:14:22:da:6f:e2
Sending on   LPF/eth0/00:14:22:da:6f:e2
Sending on   Socket/fallback
DHCPREQUEST of 192.168.254.104 on eth0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.254.104 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.254.104 from 192.168.254.254
bound to 192.168.254.104 -- renewal in 913786064 seconds.
and route
> david@davidf:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.254.0   *               255.255.255.0   U     0      0        0 eth0
default         192.168.254.254 0.0.0.0         UG    0      0        0 eth0
then
> david@davidf:~$ gksudo gedit /etc/resolv.conf 
After which I see only one line:  #generated by NetworkManager, 
so I add a line a second line and save, so now:
> david@davidf:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.254.254

also ifconfig
> david@davidf:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:14:22:da:6f:e2  
          inet addr:192.168.254.104  Bcast:255.255.255.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3061 (3.0 KB)  TX bytes:2931 (2.9 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:752 (752.0 B)  TX bytes:752 (752.0 B)

All looks good now, so I load Firefox, and I have a connection !!!!  Very cool.

Next I reboot, NetworkManager has not been running and is not running on startup.
No connection.:(
> david@davidf:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

I run "sudo dhclient eth0" again
Network is up and running again.

So I have my computer back.  Should I set something to run "sudo dhclient eth0" on startup?

Anyway, we did it.  Thanks very much.  it feels great.

David

---

### Post by krzysz00 on 2009-02-03
Add all the relevant commands to /etc/rc.local before the line that says "exit 0" Open it with ```
gksudo gedit /etc/rc.local
```

---

### Post by lykwydchykyn on 2009-02-03
If you want to do it the "correct" way, you'd need to edit /etc/network/interfaces, and add lines like this:

```

auto eth0
iface eth0 inet dhcp

```

That should do it.

---

### Post by krzysz00 on 2009-02-05
If you don't want to bring up the whole interface, just use rc.local

---

