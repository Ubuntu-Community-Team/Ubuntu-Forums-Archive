---
title: "DHCP failed"
date: 2005-08-21
forum: Networking &amp; Wireless
---

### Post by lyam_kaskade on 2005-08-21
Okay here goes. I've been using Ubuntu for about a month, and the first time I used my router was fine. Connected through DHCP, no problems or anything. 
I was running a dual boot with Windows XP on the other partition. Then I decided to try install Gentoo on one of the other partitions, and my internet connection stopped working. 
Since I was planning on getting rid of Windows XP anyway, I did a fresh install of Hoary, but it still doesn't work. During the install, the DHCP auto-configuration failed, even though it's worked every time before. I'm not sure what to do and I'd really like to get back on the net.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=lyam_kaskade]Okay here goes. I've been using Ubuntu for about a month, and the first time I used my router was fine. Connected through DHCP, no problems or anything. 
I was running a dual boot with Windows XP on the other partition. Then I decided to try install Gentoo on one of the other partitions, and my internet connection stopped working. 
Since I was planning on getting rid of Windows XP anyway, I did a fresh install of Hoary, but it still doesn't work. During the install, the DHCP auto-configuration failed, even though it's worked every time before. I'm not sure what to do and I'd really like to get back on the net.[/QUOTE]

Could you post the output from the following two commands?
```

$ ifconfig -a
$ route

```
The first command will show the configuration associated with each of your network cards (IP address, hardware address, if it is up/down, errors, etc.).  The second shows your routing information.

Also, if you could briefly describe your physical network layout (what is plugged into what) and any related error messages you have observed, that can really be a big help.

Thanks.

NOTE to any moderators:  The above informations is so useful in diagnosing what is wrong with someone's home network setup-- I end up asking that in 80% or more of the network problems I look at.  Do you think we could come up with some sort of sticky that asks people to please provide this info if they suspect they have network related configuration problems?

---

### Post by lyam_kaskade on 2005-08-21
I would have posted it before, but it's a bit of a pain copying all the information over to this computer. Here it is:


[INDENT]tony@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:11:D8:EA:8E:29
          inet6 addr: fe80::211:d8ff:feea:8e29/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:feafc000-0

eth1      Link encap:Ethernet  HWaddr 00:0E:35:CA:A0:B5
          inet6 addr: fe80::20e:35ff:feca:a0b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21396 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:22 Base address:0xa000 Memory:feafa000-feafafff

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:36823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36823 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:3131495 (2.9 MiB)  TX bytes:3131495 (2.9 MiB)

sit0      Link encap:IPv6-in-IPv4
          inet6 addr: ::127.0.0.1/96 Scope:Unknown
          UP RUNNING NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:154 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

tony@ubuntu:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface[/INDENT]

I'm running Ubuntu on my laptop, which is hooked up to a D-Link router. Also hooked up to the router is my sister's computer running Windows XP which works fine (I'm on it right now). The router connects to the cable modem through PPPoE. If there's any other information I should list please tell me.

---

### Post by cwaldbieser on 2005-08-21
[QUOTE=lyam_kaskade]
I'm running Ubuntu on my laptop, which is hooked up to a D-Link router. Also hooked up to the router is my sister's computer running Windows XP which works fine (I'm on it right now). The router connects to the cable modem through PPPoE. If there's any other information I should list please tell me.[/QUOTE]
Well, it looks like you have no (IPv4) IP address and no routing information.  Let's see if we can get you back on the net with a static IP, and then we'll try to explore why dhclient is failing.

It will help if you open a command prompt on your sister's WinXP PC and enter a couple commands.  They are basically the same things I wanted to see on the Ubuntu machine:
```

C:\> ipconfig
C:\> route print

```
This will tell us what her IP address is as well as the routing information, IP address of your router, etc.

Now I noticed that your Ubuntu machine seems to believe it has 2 network cards.  Is this correct?  If so, what network card is connected to your router?  (I am looking for "eth0" or "eth1" as an answer.  If you are not sure what physical piece of hardware corresponds to which logical device, that's OK, we can just try them out one at a time.

Once you gather the pertinant info, we will then issue commands to bring down your network card and bring it back up with a static IP address that makes sense for your home network.  Then we have to add routing information so your PC knows to forward all its network traffic to your router.  The same two commands "ifconfig" and "route" are pretty much used for the whole process.  If successful, you should be able to have connectivity.

---

### Post by lyam_kaskade on 2005-08-22
output from Win XP:

ipconfig
[INDENT]
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.104
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1[/INDENT]

route print
[INDENT]===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 11 09 2d 02 5a ...... NVIDIA nForce MCP Networking Controller - Packet
 Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.104       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.104   192.168.0.104       20
    192.168.0.104  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255    192.168.0.104   192.168.0.104       20
        224.0.0.0        240.0.0.0    192.168.0.104   192.168.0.104       20
  255.255.255.255  255.255.255.255    192.168.0.104   192.168.0.104       1
Default Gateway:       192.168.0.1
===========================================================================
Persistent Routes:
  None[/INDENT]


eth0 is the ethernet card, eth1 is the wireless ethernet card. the router is connected to eth0.

---

### Post by TeleTommy on 2005-08-22
I have exactly the same problem on my ASUS M2N Notebook using Realtek 8139too.

At first, the 8139cp module is trying to start while booting. How can I deactivate this? It's not the right one. Afterwards, the 8139too module is started correctly. But configuring the interfaces takes looong time. There is a messge "interface name is "eth0" at line 2, cant't be mapped reliable". What does it mean?

Thank you,
Thomas

---

### Post by cwaldbieser on 2005-08-22
[QUOTE=lyam_kaskade]output from Win XP:

ipconfig
[INDENT]
Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . :
        IP Address. . . . . . . . . . . . : 192.168.0.104
        Subnet Mask . . . . . . . . . . . : 255.255.255.0
        Default Gateway . . . . . . . . . : 192.168.0.1[/INDENT]

route print
[INDENT]===========================================================================
Interface List
0x1 ........................... MS TCP Loopback interface
0x2 ...00 11 09 2d 02 5a ...... NVIDIA nForce MCP Networking Controller - Packet
 Scheduler Miniport
===========================================================================
===========================================================================
Active Routes:
Network Destination        Netmask          Gateway       Interface  Metric
          0.0.0.0          0.0.0.0      192.168.0.1   192.168.0.104       20
        127.0.0.0        255.0.0.0        127.0.0.1       127.0.0.1       1
      192.168.0.0    255.255.255.0    192.168.0.104   192.168.0.104       20
    192.168.0.104  255.255.255.255        127.0.0.1       127.0.0.1       20
    192.168.0.255  255.255.255.255    192.168.0.104   192.168.0.104       20
        224.0.0.0        240.0.0.0    192.168.0.104   192.168.0.104       20
  255.255.255.255  255.255.255.255    192.168.0.104   192.168.0.104       1
Default Gateway:       192.168.0.1
===========================================================================
Persistent Routes:
  None[/INDENT]


eth0 is the ethernet card, eth1 is the wireless ethernet card. the router is connected to eth0.[/QUOTE]

OK, so first we take the ethernet card down and then bring it back up with an IPv4 address.  It looks like you have a 192.168.0.x network at home, so I am going to assume that 192.168.0.17 is not taken, and we will use that for your address.
```

$ sudo ifdown eth0
$ sudo ifconfig eth0 192.168.0.17

``` 

Next, we need to set some routing information.  Basically, we want to tell your computer that anything for your LAN can just be broadcast over the ethernet (it doesn't need to go through your router).  Anything not destined for the local network needs to go to the router.
```

$ sudo route add -net 192.160.0.0 netmask 255.255.255.0 dev eth0
$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 192.168.0.1

```
Now, you should be able to do a few tests successfully at this point:
Ping your router.
```
$ ping -c 3 192.168.0.1
``` 
Ping your sister's computer.
```
$ ping -c 3 192.168.0.104
``` 
Ping [www.google.com](www.google.com) by IP address 64.233.161.99
```
$ ping -c 3 64.233.161.99
```
You can try to ping ping a web site by its name ([www.yahoo.com)](www.yahoo.com)).  If this doesn't seem to be working, we probably need to put your DNS servers in the file "/etc/resolv.conf".

If you can't successfully do the ping tests, or if you get any errors, let me know and I will try to figure out what happened.

---

### Post by lyam_kaskade on 2005-08-22
umm...errors:

ifdown eth0

[INDENT]ifdown: interface eth0 not configured[/INDENT]



$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 192.168.0.1:

[INDENT]SIOCADDRT: No such device[/INDENT]

and ping 192.168.0.1 and ping 192.168.0.17:

[INDENT]Destination Host Unreachable[/INDENT]


I should mention that I can connect to the router on the Gentoo Live/Install CD, so it definitely isn't a cable/hardware problem (well, i don't think...).

---

### Post by cwaldbieser on 2005-08-23
[QUOTE=lyam_kaskade]umm...errors:

ifdown eth0

[INDENT]ifdown: interface eth0 not configured[/INDENT]



$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 192.168.0.1:

[INDENT]SIOCADDRT: No such device[/INDENT]

and ping 192.168.0.1 and ping 192.168.0.17:

[INDENT]Destination Host Unreachable[/INDENT]


I should mention that I can connect to the router on the Gentoo Live/Install CD, so it definitely isn't a cable/hardware problem (well, i don't think...).[/QUOTE]
Well, that is pretty strange.  Back when you posted the output of "ifconfig -a", it showed an eth0 device, but when you try to bring it down or route to it, it gives you an error.  Maybe the driver for that NIC isn't getting loaded?  You could search the boot log for something related:
```
$ dmesg | grep -i eth0
``` 
I'm not sure what to do in that case, though...

Well, the last thing I can suggest is that you try to just run dhclient manually and see if that works at all.
```
$ sudo dhclient > dhcp.txt 2>&1 
``` 
All the output, errors, etc. will be recorded in the file dhcp.txt.  Copy that file over to your XP box and post it if it doesn't start your Internet working.

---

### Post by lyam_kaskade on 2005-08-23
[INDENT]tony@ubuntu:~$ dmesg | grep -i eth0
eth0: Yukon Gigabit Ethernet 10/100/1000Base-T Adapter
eth0: no IPv6 routers present[/INDENT]


dhcp.txt:
[INDENT]Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth1/00:0e:35:ca:a0:b5
Sending on   LPF/eth1/00:0e:35:ca:a0:b5
Listening on LPF/lo/
Sending on   LPF/lo/
Listening on LPF/eth0/00:11:d8:ea:8e:29
Sending on   LPF/eth0/00:11:d8:ea:8e:29
Sending on   Socket/fallback
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14[/INDENT]

---

### Post by cwaldbieser on 2005-08-23
Well, it looks like your dhclient just kinda listens but doesn't get any response.  Here is my "/etc/dhcp3/dhclient.conf":
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```
Does yours look similar?  Post if it's different.

I went back over the previous posts, and something doesn't quite make sense to me.  Could you try this for me and post the output?
```

$ sudo ifconfig eth0 192.168.0.17
$ ifconfig

```
I don't know how familiar you are with the command line, but if you get tired of copying this stuff manually from one PC to the next, you can always save the output to a file like you did for the dhclient command:
```

$ sudo ifconfig eth0 192.168.0.17
$ ifconfig > log.txt 2>&1

``` 
The "> log.txt" part means, "send all the normal output to the file 'log.txt'."  The "2>&1" part means, "send the errors to the same file as the normal output."

What I want to see here is if trying to set the IP address of the interface is having any effect at all.

Thanks.

---

### Post by lyam_kaskade on 2005-08-24
My /etc/dhcp3/dhclient.conf file looks exactly the same as yours, with the only uncommented lines being:

```
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
```

output from 
$ sudo ifconfig eth0 192.168.0.17
$ ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:11:D8:EA:8E:29  
          inet addr:192.168.0.17  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Memory:feafc000-0 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7031 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7031 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:398158 (388.8 KiB)  TX bytes:398158 (388.8 KiB)
```

Thanks for all your help so far.

---

### Post by cwaldbieser on 2005-08-24
[QUOTE=lyam_kaskade]
Thanks for all your help so far.
[/QUOTE]
No problem!

OK-- the ifconfig command seemed to work.  Now we just need to set up your route correctly.

Assuming you have not rebooted since doing the ifconfig command, try doing this:
```
$ route
```
I am expecting that you should have automatically gotten an entry that looks like this:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

```
If you don't have this entry-- stop here and let me know that the routing table was empty.  I will have to figure out what that means.

What we want to do is to add a default route, sometimes called the default gateway.  It will make your routing table look like this:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    0      0        0 eth0

```
The following command should do it (I think I had the syntax slightly off before):
```

$ sudo route add -net 0.0.0.0 netmask 0.0.0.0 gw 192.168.0.1

``` 
If that works, you should be able to ping your router, the Internet, etc.

---

### Post by lyam_kaskade on 2005-08-25
It worked in that the  entry was added to the route list. Unfortunately, I still can't ping the router (or google.com, etc.).
 Some other things I tried today:

reset the router to factory defaults and go through the setup again. The desktop computer works still, but my laptop still doesn't see the router. 

reinstalling Windows. It tells me that a network cable is unplugged (when it clearly isn't).

---

### Post by cwaldbieser on 2005-08-25
[QUOTE=lyam_kaskade]It worked in that the  entry was added to the route list. Unfortunately, I still can't ping the router (or google.com, etc.).
 Some other things I tried today:

reset the router to factory defaults and go through the setup again. The desktop computer works still, but my laptop still doesn't see the router. 

reinstalling Windows. It tells me that a network cable is unplugged (when it clearly isn't).[/QUOTE]
Do you think the cable could just be bad?  Or possibly the NIC?  Are there lights or something on the NIC that flash when it is working?

---

### Post by lyam_kaskade on 2005-08-25
> Do you think the cable could just be bad? Or possibly the NIC? Are there lights or something on the NIC that flash when it is working?

Well, I can still get the laptop to connect using the Gentoo Install CD (and browse the web using links) so I'm almost positive the hardware is fine. And it was working before, and I haven't physically done anything to the cable (and I tried another cable). This leads me to believe it may have something to do with Gentoo. After probing the Gentoo forums for several hours I thought it might be worthwhile to try using dhcpcd (because that's what Gentoo uses) but I can't seem to get it to work on the Gentoo CD. Is there any way to install it in Ubuntu without internet access? I have a USB pen as long as the files aren't too big. I tried checking packages.ubuntu.com, but dhcpcd seems to have an endless trail of files it depends on, so I was hoping there was an easier way. If not, I'll have to go through them all.
Unless you still have another idea?

---

### Post by cwaldbieser on 2005-08-25
[QUOTE=lyam_kaskade]Well, I can still get the laptop to connect using the Gentoo Install CD (and browse the web using links) so I'm almost positive the hardware is fine. And it was working before, and I haven't physically done anything to the cable (and I tried another cable). This leads me to believe it may have something to do with Gentoo. After probing the Gentoo forums for several hours I thought it might be worthwhile to try using dhcpcd (because that's what Gentoo uses) but I can't seem to get it to work on the Gentoo CD. Is there any way to install it in Ubuntu without internet access? I have a USB pen as long as the files aren't too big. I tried checking packages.ubuntu.com, but dhcpcd seems to have an endless trail of files it depends on, so I was hoping there was an easier way. If not, I'll have to go through them all.
Unless you still have another idea?[/QUOTE]

OK, this is just a shot in the dark, but I once heard from a guy who swore that the distro he was using somehow "turned off" his NIC when he shut down the system, and Windows couldn't even bring it back up after a reboot.

If that is the case, it means there must be some sort of storage or battery backup on the card.  If you are using a Gentoo LiveCD, here is what I would do:

1) Boot up in Gentoo.  Verify the card is working.
2) If any real filesystems besides the ramdrive were mounted, unmount them.
3) Switch the power off without shutting down cleanly.
4) Try to access the NIC with some other OS.

What I would be hoping to accomplish is to prevent whatever the OS is doing to disable the card from happening.  As long as you don't have to worry about filesystems becoming corrupted, this seems like a reasonable method.

I'd probably first try some different LiveCDs out (Knoppix, DSL, etc.) and see if any of those can use the network.  If so, maybe they are loading a module that the others don't-- use "lsmod" and look for differences.  It is tedious, but a proven empirical technique.

---

### Post by lyam_kaskade on 2005-08-26
> OK, this is just a shot in the dark, but I once heard from a guy who swore that the distro he was using somehow "turned off" his NIC when he shut down the system, and Windows couldn't even bring it back up after a reboot.

If that is the case, it means there must be some sort of storage or battery backup on the card. If you are using a Gentoo LiveCD, here is what I would do:

1) Boot up in Gentoo. Verify the card is working.
2) If any real filesystems besides the ramdrive were mounted, unmount them.
3) Switch the power off without shutting down cleanly.
4) Try to access the NIC with some other OS.

What I would be hoping to accomplish is to prevent whatever the OS is doing to disable the card from happening. As long as you don't have to worry about filesystems becoming corrupted, this seems like a reasonable method.

I'd probably first try some different LiveCDs out (Knoppix, DSL, etc.) and see if any of those can use the network. If so, maybe they are loading a module that the others don't-- use "lsmod" and look for differences. It is tedious, but a proven empirical technique.


Aaaahh!!  :grin: it worked! Ubuntu certainly didn't like it; did some wierd stuff during boot ("/ not properly unmounted, force check" and then saying "fail" after the check. Had me worried (still does a bit, i might do a clean reinstall just to be safe)). Definitely no more messing around with Gentoo for a looong time (at least not on a computer I have to *use*.) Ahh...today is a good day. 
Thanks for your help cwaldbieser, I'm not sure if there's anything I can do to repay you...

Hooray for shots in the dark!  =D>    \\:D/

---

### Post by cwaldbieser on 2005-08-26
[QUOTE=lyam_kaskade]Aaaahh!!  :grin: it worked! Ubuntu certainly didn't like it; did some wierd stuff during boot ("/ not properly unmounted, force check" and then saying "fail" after the check. Had me worried (still does a bit, i might do a clean reinstall just to be safe)). Definitely no more messing around with Gentoo for a looong time (at least not on a computer I have to *use*.) Ahh...today is a good day. 
Thanks for your help cwaldbieser, I'm not sure if there's anything I can do to repay you...

Hooray for shots in the dark!  =D>    \\:D/[/QUOTE]
Yay!  Glad to see you up and running.
What would be good to do now is to find out the type of NIC you have in that machine and the version of Gentoo (distro version scheme and the kernel version if you know it).  I am not sure if the information should go to the Gentoo folks or the NIC manufacterer or to the kernel mailing list.  If you post the info, though, I will try to see that it gets into the proper hands.

---

### Post by lyam_kaskade on 2005-08-27
would the NIC be "Marvell Yukon Gigabit Ethernet 10/100/1000Base-T Adapter"? or is there some other way to check?

And I was using the "Gentoo 2005.1 Universal install CD". I didn't actually get through configuring my kernel, so I'm not sure if that's important. The CD gave the option of the 2.4 or the 2.6 though...
Unless you meant something else.
Thanks again.

---

### Post by macmasterxiv on 2005-08-29
Well, I somehow happened to have stumbled onto this same problem and I have the same network chipset (marvell yukon gigabit) except that it was from forcing a shutdown while network activity that happened to be stalled was going on. I tried this forcing method and...it worked! Thanks a ton!

---

