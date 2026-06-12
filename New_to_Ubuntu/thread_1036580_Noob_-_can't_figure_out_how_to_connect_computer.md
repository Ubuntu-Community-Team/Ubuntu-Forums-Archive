---
title: "Noob - can't figure out how to connect computer"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by capeKO71 on 2009-01-11
Hi all - I'm a real noob at Ubuntu. While I usually manage to get around technical things - i don't fully understand networking - so that's part of the problem. I'm hoping someone here will be able to walk me through setting up my network config in Ubuntu. 

From the wall out: 
-Arris Modem w/ phone from Comcast
-Netgear Wireless Router 

Now I know in order to connect to our network, we have to use a keyword and our network name. I don't know what you call that... but it's some security. 

Off the router I have
1 - desktop running Vista Wired
1 - laptop running Vista Wireless
and I'm trying to get the 1 desktop running Ubuntu 8.10 Wired

I frankly think I have my settings wrong - I don't quite know where I'm supposed to put those network names & password... but I've also read on these forums that the comcast VOIP phone modems are sort of a PITA to deal with. 

Anyone have a step by step of what I should do to get this thing connected? 

I've reset my modem, plugged everything back in and re-booted... still no automatic detection.

When I ping from the Ubuntu computer, it just says its not connected. 

Any help would be greatly appreciated!

---

### Post by handydan918 on 2009-01-11
Oh, brother. What a nightmare to do remotely. 
First, break open your shiny new router manual and find out how to access the interface for the router. It will be something like opening a browser and typing 192.168.1.1 in the address bar. Or it could be 192.168.0.1 or 192.168.2.1 or 10.0.0.1...................
you get the idea.

Once you've done that, disable any security, like wep or wpa.
After you get Ubu to connect, then you can decide how to proceed with the security issue, but trying to trouble shoot with enrcyption on is masochistic.
Post back before you burst into flames...

---

### Post by thinking2loud on 2009-01-11
Hang on...I'm trying to understand what you have here...you have a desktop running Windows and you're trying to get Ubuntu running on it?  (Or do you have a 2nd desktop, which is running only Ubuntu [albeit with no networking] ?)  

Go to Windows, open a command prompt, and type ipconfig /all 
Send back what it tells you.

Issues are that you have to have the correct settings on Ubuntu for the DHCP, gateway, IP address (if you don't use DHCP), DNS servers, etc....

---

### Post by capeKO71 on 2009-01-11
1 laptop, and 2 desktops. 1 is 100% vista (blah) and the other is 100% ubuntu. I didn't do any dual booting stuff. so the 2 window computers are online just fine. 

yeah - I can try to get into my router (it's not new... god knows where the friggin manual is... ) - but I think that is the ip address I've used before to get into it...

---

### Post by capeKO71 on 2009-01-11
Microsoft Windows [Version 6.0.6000]
Copyright (c) 2006 Microsoft Corporation.  All rights reserved.

C:\Users\Kate>ipconfig/all

Windows IP Configuration

   Host Name . . . . . . . . . . . . : O
   Primary Dns Suffix  . . . . . . . :
   Node Type . . . . . . . . . . . . : Hybrid
   IP Routing Enabled. . . . . . . . : No
   WINS Proxy Enabled. . . . . . . . : No

Ethernet adapter Local Area Connection:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : NVIDIA nForce Networking Controller
   Physical Address. . . . . . . . . : 00-1D-60-E0-CF-3B
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::6cb7:cf7f:2f7b:913b%8(Preferred)
   IPv4 Address. . . . . . . . . . . : 192.168.1.4(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Lease Obtained. . . . . . . . . . : Saturday, January 10, 2009 10:31:31 PM
   Lease Expires . . . . . . . . . . : Sunday, January 11, 2009 10:31:31 PM
   Default Gateway . . . . . . . . . : 192.168.1.1
   DHCP Server . . . . . . . . . . . : 192.168.1.1
   DHCPv6 IAID . . . . . . . . . . . : 201333756
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled

Tunnel adapter Local Area Connection* 6:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Teredo Tunneling Pseudo-Interface
   Physical Address. . . . . . . . . : 02-00-54-55-4E-01
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e50:34ef:7b9:3f57:fefb(Prefe
rred)
   Link-local IPv6 Address . . . . . : fe80::34ef:7b9:3f57:fefb%9(Preferred)
   Default Gateway . . . . . . . . . : ::
   NetBIOS over Tcpip. . . . . . . . : Disabled

Tunnel adapter Local Area Connection* 7:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : isatap.{EE8227C0-2ACF-47E5-9DFF-89E830265
40A}
   Physical Address. . . . . . . . . : 00-00-00-00-00-00-00-E0
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::5efe:192.168.1.4%10(Preferred)
   Default Gateway . . . . . . . . . :
   DNS Servers . . . . . . . . . . . : 192.168.1.1
   NetBIOS over Tcpip. . . . . . . . : Disabled

C:\Users\Kate>

---

### Post by blackened on 2009-01-11
Since this is a wired connection, there is absolutely no need for you to disable your router-level wireless security. The problem is either in auto-recognition of your network interface card or your network settings are all screwed up (I'll put money on the former). Either way, your wireless security settings are not the problem, and you'll only cause problems if you disable them on an already functioning setup.

Please post the output (wrapped in code tags) of the following commands:
```
lshw -C network
```
and
```
ifconfig
```

---

### Post by capeKO71 on 2009-01-11
Ok - the lshw -C network: 

WARNING: you should run this program as super-user.

*-network
[INDENT]description: Ethernet interface
product: 3c905C-TX/TC-M Tornado
vendor: 3 Com Corporation
physical ID: 9
bus info: pci@0000:02:09:0
logical name: eth0
version: 78
serial: 00:01:03:c4:f1:cc
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=3c59x latency=64 maxlatency - 10mingnt
=10 module=3c59x multicast=yes[/INDENT]

*-network DISBLED
description: Ethernet interface
physical id: 1
logical name: pan0
serial: 2e:4f:19:cd:a5:49
capabilities: ethernet physical
configuration: broadcast = yes driver=bridge driverversion =2.3 firmware=N/A Multicast=yes



Does that all help at all?

---

### Post by capeKO71 on 2009-01-11
Oh - and Iconfig on the Ubuntu computer is giving: 

etho0
Link encap: Ehternet MTU: 1500 Metric:1
RX packets: 0 Error:0 dropped 0 overruns 0 frame 0
TX packets 0 errors: 0 dropped 0 overruns: 0 carrier: 0 collissions 0 txqueuelen: 1000
RX bytes: 0 (0.0 B) TX bytes: 0 (0.0B)
Interrupt: 3 Base address: 0x4c00

lo
Link encap: local loopback
inet addr: 127:0:0:1 Mask: 255:0.0.0
inet6 addr: ::1/128 Scope: Host
Up Loopback running MTU: 16436 Metric: 1
rx packets 240 errors 0 dropped 0 overruns 0 frame 0
TX packets 240 erros 0 dropped 0 overruns 0 carrier 0 collissions 0 txqueuelen 0
rx bytes: 15040 (15.0 kb) tx bytes: 15040 (15.0 kb)

---

### Post by theozzlives on 2009-01-11
1. Get your Ubuntu connected.
2. Open a terminal and type the following:
```
sudo apt-get install samba
```
```
sudo smbpasswd -a username(type the password)
```
```
sudo gedit /etc/samba/smb.conf
```
when you see an entry after [global] that says workgroup=WORKGROUP, change WORKGROUP to whatever your workgroup is. Save and exit.

Reboot and you'll be on the network

---

### Post by handydan918 on 2009-01-11
> **blackened said:**
> Since this is a wired connection, there is absolutely no need for you to disable your router-level wireless security.Nie catch. I misread the OP. My bad.>  The problem is either in auto-recognition of your network interface card or your network settings are all screwed up (I'll put money on the former). Agree. That nic was autodetected ten years ago. It should be fine.> Either way, your wireless security settings are not the problem, and you'll only cause problems if you disable them on an already functioning setup.

Please post the output (wrapped in code tags) of the following commands:
```
lshw -C network
```
and
```
ifconfig
```

---

### Post by handydan918 on 2009-01-11
> **theozzlives said:**
> 1. Get your Ubuntu connected.
2. Open a terminal and type the following:
```
sudo apt-get install samba
```
```
sudo smbpasswd -a username(type the password)
```
```
sudo gedit /etc/samba/smb.conf
```
when you see an entry after [global] that says workgroup=WORKGROUP, change WORKGROUP to whatever your workgroup is. Save and exit.

Reboot and you'll be on the network

And samba has WHAT to do with tcp/ip connectivity?

---

### Post by ugm6hr on 2009-01-11
Could be an issue with the 3c59x driver: [http://forums.whirlpool.net.au/forum-replies-archive.cfm/790517.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/790517.html)

Did a bit more searching for you - a bit of hacking may be required:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/94186](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/94186)
[http://shallowsky.com/blog/linux/udev-ifup.html](http://shallowsky.com/blog/linux/udev-ifup.html)
[https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/211955](https://bugs.launchpad.net/ubuntu/+source/netbase/+bug/211955)

Something to try (with ethernet plugged in):
```
sudo ifdown eth0
sudo ifup eth0
ifconfig
```

---

