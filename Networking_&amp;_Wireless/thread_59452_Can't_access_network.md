---
title: "Can't access network"
date: 2005-08-24
forum: Networking &amp; Wireless
---

### Post by pwaustin on 2005-08-24
Hi, I had a post a few days ago: [http://ubuntuforums.org/showthread.php?t=58488](http://ubuntuforums.org/showthread.php?t=58488)

I'm posting my issue again because I have messed around with ubuntu a lot the past few days and can maybe be a bit clearer. 

I cannot access my ADSL modem through my ethernet (eth0) or my usb port (eth1), both work fine in win2000.  I sometimes also use the internet connection from an xp computer, which I connect directly to with a cross-over cable (which also works fine in win2000).  But I cannot ping the other computer either.  When open konqueror, I can see the xp computer in my workgroup directory, but cannot access it (the xp computer can also see me in My Network Places, but cannot ping me either).

At first I thought maybe it was my NIC, but since the usb doesn't work either I am wondering if there is some setup with opening ports or some default firewall that is not letting me out?

This has been driving me crazy the past few days and I feel like I've tried everything.  Any help is very much appreciated!

---

### Post by pwaustin on 2005-08-25
So does this mean that in my previous post I have already tried everything to find the problem?  It seems strange that this doesn't work and even stranger that I'm not experiencing the typical problems associated with connecting to the network in ubuntu.  This is my first try with linux and I really like what I see, however having an internet connection is imperitive.  

Does anybody have any suggestion at all, no matter how simple or far fetched? I am at the point where I will try anything. Thanks, hope to hear something!

---

### Post by nad on 2005-08-25
Have you checked all the settings in the system network setup menus?

Are both computers on the same subnet (192.168.0.xxx)? Workgroup?

Do you have a share setup on each computer? Passwords, permissions, accounts?

It seems strange that the computers are recognized but you can't ping them.

---

### Post by pwaustin on 2005-08-25
I'm not exactly sure what settings to check in the system network setup menus.  The computers are on the same subnet (the XP computer acts as the gateway to the ADSL modem) and the same workgroup.

For the share setup, there are no permissions on the XP share folders, so I've always been able to connect to them. I haven't changed anything on the XP computer from when win2000 shared with it. I'm assuming that it would all be the same.  And I think I've setup Samba correctly for XP to share my folders.  However, please correct me if I'm wrong, shouldn't the computers still be able to ping each other, even if the shares aren't setup?

I've been wondering if the key to this is the fact that neither the ethernet card or the usb can correctly connect to the adsl modem (getting rid of the middle-man XP).  Is there some port being blocked or some protocol that isn't working correctly that causes this?

---

### Post by nad on 2005-08-25
To connect through the modem, Internet Connection Sharing has to be setup up on the XP computer to bridge your two network cards.

This. however, has nothing to do with your lan connection between the two computers.

Please post the output of the terminal commands:

ifconfig
route
cat /etc/resolv.conf

and the Connection-> Support configuration of the XP computer.

---

### Post by pwaustin on 2005-08-25
Yes, the Internet Connection Sharing is setup on the XP computer and works great with win2000 (dual boot on my computer). 

ifconfig

```

eth0
Link encap:Ehthernet  HWaddr 00:02:3F:B4:CB:69
inet addr:192.168.0.92 Bcast:192.168.0.255  Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500  Metric:1
RX packets:6 errors:0 dropped:0  overruns:0  frame:0
TX packets:47 errors:0 dropped:0  overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1248 (1.2 KiB)  TX bytes:4586 (4.4 KiB)
Interrupt:17 Base address:0x4000

lo
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets: 8  errors:0  dropped:0  overruns:0  frame:0
TX packets:8  errors:0  dropped:0  overruns:0  carrier:0
collisions:0 txqueuelen:0
RX bytes:788 (788.0.b)  TX bytes:788 (788.0.b)

```

route

```

Kernal IP routing table
Destination           Gateway         Genmask      Flags      Metric     Ref   Use Iface
192.168.0.0            *              255.255.255.0    U            0            0        0   eth0
default                192.168.0.1       0.0.0.0          UG          0            0        0   eth0

```

cat /etc/resolv.conf

```

search mshome.net
nameserver 192.168.0.1

```

I'm not sure where to find the Connection-> Support configuration of the XP computer.

---

### Post by nad on 2005-08-25
My Network Connections (oh the humanity).

You want to look at the settings for Network Bridge and Lan Connection #?

Make sure that the lan side of the bridge is 192.168.0.1 and that the XP computers' lan address is 192..168.0.1.

---

### Post by pwaustin on 2005-08-25
Sorry, early in the morning for me, I thought you were looking for something more complicated.

Connection status:

Address Type: Manually Configured
IP Address: 192.168.0.1
Subnet Mask: 255.255.255.0
Default Gateway:


This is the Local Area Connection which was configured automatically when I enabled Internet Connection Sharing for the ADSL Connection.

---

### Post by nad on 2005-08-25
If I'm not mistaken, there should be a default gateway address listed, which would also be this computer.

"Manually Configured" ?

Network bridge config?

---

### Post by pwaustin on 2005-08-25
Yeah, that makes sense about the gateway.  Like I said, when I setup Internet Connection Sharing with the ADSL connection and tell it to share Local Area Connection, it automatically configures it.  Anyways, I added 192.168.0.1 to default gateway and still nothing.

I'm not sure why it says Manually Configured.

If I try to Bridge Connections, it says I must select connections that are not being used by Internet Connection Sharing.

---

### Post by nad on 2005-08-25
I will take a look at a bridged MS network later and get back to you. I suspect that something is not configured correctly. Perhaps you have to bridge the connection before you set up Internet Connection Sharing.

---

### Post by pwaustin on 2005-08-25
Thanks for all of your help with this, much appreciated!!

I have now been trying to connect to the ADSL modem with the use of the XP computer.  I have tried running pppoeconf and it recognizes my card as eth0, but then returns a message saying that the Access Concentrator did not respond.  Could it be possible that Ubuntu thinks it sees my NIC, but in reality does not?

---

### Post by nad on 2005-08-25
Okay, network bridging is not an issue here. My bad.

As you are sharing the XP computers' pppoe connection, the ubuntu computer will not use pppoe. The XP computer is your gateway.

Let's start over.

cat /etc/network/interfaces

This file should have an eth0 stanza after the l0 stanza that looks like this:

auto eth0 inet static
address 192.168.0.92
netmask 255.255.255.0
gateway 192.168.0.1

That's it.

type: /etc/init.d/networking restart

ifconfig
route
cat /etc/resolv.conf

If everything looks correct, you should be connected.

---

### Post by pwaustin on 2005-08-26
ok made the changes and when I try to restart the network it says "Reconfiguring network interfaces... fail"

Here is my /etc/network/interfaces file

```

#The loopback network interface
auto lo
iface lo inet loopback

#This is a list of hotpluggable network interfaces
#They will be activated automatically by the hotplug subsystem.
mapping hotplug
.       script grep
.       map eth0

#The primary network interface
auto eth0 inet static
address 192.168.0.92
netmask 255.255.255.0
gateway 192.168.0.1


```

Not sure why it is failing, any ideas?

---

### Post by pwaustin on 2005-08-26
Ok, just tried:
```
iface eth0 inet static
```
on the first line instead of:
```
auto eth0 inet static
```

The network restarts without errors, but still cannot ping the XP computer

---

### Post by nad on 2005-08-26
Is there a software firewall setup on the XP computer?

---

### Post by pwaustin on 2005-08-26
Yes, Zone Alarm is installed there.  But it is set to allow anything on the 192.168.0.x domain.  Plus, just to be sure, I've tried to ping with the firewall disabled.

---

