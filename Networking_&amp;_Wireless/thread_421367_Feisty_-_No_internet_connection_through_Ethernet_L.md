---
title: "Feisty - No internet connection through Ethernet LAN"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by RC211V on 2007-04-24
Hi ppl. I am currently posting through Edgy. My university Ethernet LAN connection works like a charm. I installed Feisty recently and i couldn't connect at all. 
I run ifconfig in Edgy and in the live cd of Feisty and got defferent results. Feisty finds more ethx
devices.
Here is the result of ifconfig in Feisty:

ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          inet6 addr: fe80::212:f0ff:fe83:7020/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xa000 Memory:b000b000-b000bfff 

eth0:avah Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          inet addr:169.254.7.45  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          inet addr:169.254.5.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xa000 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2764 (2.6 KiB)  TX bytes:2764 (2.6 KiB)

 Hope you can help.

---

### Post by bnuytten on 2007-04-24
Probably one wired and one wireless interface you never used on Edgy and is now automatically discovered by Feisty. In either cases you did not receive a DHCP lease. To see which hardware you have use
```
lspci
```
and look for "Ethernet Controller" and/or "Network Controller"

Configure you fixed interface to use DHCP or set it to manual depending on how your network administrator arganised things... If you keep having problems post ifconfig and /etc/network/interfaces from Edgy and the same commands on Feisty so we can compare...

---

### Post by RC211V on 2007-04-26
Guys I put in the live cd of Feisty to try your suggestion and the network manager connected out of the blue. I took advantage of the situation and installed Feisty immediately and now my internet works like a charm. It is the 2nd installation that did the trick.

---

### Post by RC211V on 2007-04-27
Well I seams I still have a problem. Feisty internet connection has a life of its own. It decided not to connect at all again. Here are the results from some commands. Please help as it gets so frustrating. 

-------------------------------------------------------------------------------------------------
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          inet6 addr: 2002:c096:b491:4:2a0:d1ff:fe20:c14e/64 Scope:Global
          inet6 addr: fec0::4:2a0:d1ff:fe20:c14e/64 Scope:Site
          inet6 addr: fe80::2a0:d1ff:fe20:c14e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45023350 (42.9 MiB)  TX bytes:146206 (142.7 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 Memory:b000b000-b000bfff 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          inet addr:169.254.5.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xc000 Memory:b000b000-b000bfff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1076 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:106365 (103.8 KiB)  TX bytes:106365 (103.8 KiB)
-------------------------------------------------------------------------------------------------
/etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
-------------------------------------------------------------------------------------------------
 sudo dhclient ls eth0
Password:
There is already a pid file /var/run/dhclient.pid with pid 134993544
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ls: ERROR while getting interface flags: No such device
ls: ERROR while getting interface flags: No such device
Listening on LPF/eth0/00:a0:d1:20:c1:4e
Sending on   LPF/eth0/00:a0:d1:20:c1:4e
Bind socket to interface: No such device
-------------------------------------------------------------------------------------------------
 lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Radeon Mobility M300]
**02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 15)**
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Generic system peripheral [0805]: Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller
-------------------------------------------------------------------------------------------------
 nslookup [www.google.com](www.google.com)
;; connection timed out; no servers could be reached
-------------------------------------------------------------------------------------------------
 ping 66.102.7.147
PING 66.102.7.147 (66.102.7.147) 56(84) bytes of data.
From 169.254.5.220 icmp_seq=1 Destination Host Unreachable
From 169.254.5.220 icmp_seq=2 Destination Host Unreachable
From 169.254.5.220 icmp_seq=3 Destination Host Unreachable
From 169.254.5.220 icmp_seq=4 Destination Host Unreachable
From 169.254.5.220 icmp_seq=5 Destination Host Unreachable
From 169.254.5.220 icmp_seq=6 Destination Host Unreachable
From 169.254.5.220 icmp_seq=7 Destination Host Unreachable
From 169.254.5.220 icmp_seq=8 Destination Host Unreachable
From 169.254.5.220 icmp_seq=9 Destination Host Unreachable
From 169.254.5.220 icmp_seq=10 Destination Host Unreachable
From 169.254.5.220 icmp_seq=11 Destination Host Unreachable
From 169.254.5.220 icmp_seq=12 Destination Host Unreachable
-------------------------------------------------------------------------------------------------
The funny thing is that the manager shows that it is connected. And all addresses are correct. See picture attached.

---

### Post by bnuytten on 2007-04-28
> **RC211V said:**
> 
-------------------------------------------------------------------------------------------------
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:A0:D1:20:C1:4E  
          inet6 addr: 2002:c096:b491:4:2a0:d1ff:fe20:c14e/64 Scope:Global
          inet6 addr: fec0::4:2a0:d1ff:fe20:c14e/64 Scope:Site
          inet6 addr: fe80::2a0:d1ff:fe20:c14e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:384870 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1985 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45023350 (42.9 MiB)  TX bytes:146206 (142.7 KiB)
          Interrupt:11 

eth1      Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0xc000 Memory:b000b000-b000bfff 

eth1:avah Link encap:Ethernet  HWaddr 00:12:F0:83:70:20  
          inet addr:169.254.5.220  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:11 Base address:0xc000 Memory:b000b000-b000bfff 


Ok what is clear from this output: eth1, your wireless network is set to DHCP but does not receive an IP address. Probably because it is not connected. I suggest you remove "auto eth1" from /etc/network/interfaces for the time being. That way Ubuntu will not attempt to bring up the wireless interfaces automatically.

Second, your wired card did not receive an IP address - altough the GUI tool says it has. I'd rather believe the command tools than the GUI app in this case.

You start the dhcp client "dhclient eth0" for interface "ls" and "eth0". ls does not exist off course so that's probably just a typo. And if you would mean lo, that one has a static IP assigned, so no dynamic one. You get some kind of strange error anyway that I cannot explain at the moment.

Anyway, what happens next. You try to reach Internet, you cannot of course resolve hostname since the DNS servers are not reachable. And you cannot ping or do something else because the Internet is not reachable. Why? Interface eth0 has no IP address so that one can't be used. Interface eth1 has an IP address BUT it is invalid for browsing the Internet. When DHCP fails, it uses a known black hole in the IP space and chooses an IP address out of that range. That range being 169.254.x.x. That's just DHCP behaviour.

So it wil be clear to you by now that you do not have a valid IP address for browsing the net on either interface. By disabling interface eth1 (wireless) you will avoid the 169.254.x.x address which will simplify things a little. You can later re-enable the wifi interface anyway. The main problem here is that you do not get an IP address of your provider's DHCP server.

We can troubleshoot furher using tcpdump and alike but that really requires in depth networking knowledge. I suggest you
[LIST=1]
[*]disable eth1 as described above
[*]restart network to have the changes in effect
[*]if it does not have an IP: execute "dhclient eth0" and post the output here
[/LIST]

---

### Post by RC211V on 2007-04-28
Ok deleted auto eth1
Restarted linux but nothing.

sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5778
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:a0:d1:20:c1:4e
Sending on   LPF/eth0/00:a0:d1:20:c1:4e
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by ayllu on 2007-04-28
i justed installed  ubuntu 7.04 in may toshiba a60 notebook and having the same problem, with de wifi and ethernet card, with ubunu 6.06 worked fine

i will keep following this thread.
thanks

---

### Post by bnuytten on 2007-04-28
> **RC211V said:**
> sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5778
killed old client process, removed PID file

When you startup your Ubuntu box, it starts dhclient for that interface already because you have specified a dynamic IP address in /etc/network/interfaces. So if you manually start dhclient (so you can see the output) it kills the other process first. Completely normal.

> **RC211V said:**
> No DHCPOFFERS received.
No working leases in persistent database - sleeping.
I already mentioned this in a a previous post but now we have "proof". You simple do not get an answer from the DHCP server. That's the source of your problem. It probably has nothing to do with linux anyway. If you manage the DHCP server you can start looking there if the requests do arrive there. This is the case when you use some kind of router and have a private subnet configured. This is not the case here based on the IP addresses in your previous post.

You cannot have a look at your provider's DHCP server, can you? Well not legally that is ;-) We will use a packet sniffer to discover what happen exactly on your machine. Execute the command below, start dhclient while it is running and when dhclient completes (or goes to sleep) you can stop it with ctrl+c.
```
tcpdump -vvn -i eth1 -s1500 udp port 67 or port 68
```

---

### Post by bnuytten on 2007-04-28
Oh yes, when posting output or something alike: please wrap [CODE] tags around it for readability. Select your text and choose the hash # button.

---

### Post by RC211V on 2007-04-28
ok here is the result 

```
sudo tcpdump -vvn -i eth1 -s1500 udp port 67 or port 68
tcpdump: bind: Network is down
```

Thanks a lot for your support btw.

---

### Post by bnuytten on 2007-04-28
> **RC211V said:**
> ok here is the result 

```
sudo tcpdump -vvn -i eth1 -s1500 udp port 67 or port 68
tcpdump: bind: Network is down
```

Thanks a lot for your support btw.

My mistake. I tested it here on an interface directly connected to the provider and it is called eth1. Yours should be off course eth0 since the wifi interface is eth1. So:
```
sudo tcpdump -vvn -i eth0 -s1500 udp port 67 or port 68
```

---

### Post by RC211V on 2007-04-29
```
sudo tcpdump -vvn -i eth0 -s1500 udp port 67 or port 68
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 1500 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel


```

I used ctr+c because it was taking ages

---

### Post by bnuytten on 2007-04-29
> **RC211V said:**
> ```
sudo tcpdump -vvn -i eth0 -s1500 udp port 67 or port 68
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 1500 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel


```

I used ctr+c because it was taking ages

Tough one... I would at least have expected something to show up... The whole test should not take any longer than 1 minute. Maybe you have a firewall (iptables) running on your Ubuntu box?

You may try ```
tcpdump -vvn -i eth0
``` which will capture ALL packets on interface eth0... You should at least capture something... Try browsing or so when the tcpdump command is running to create some traffic.

---

### Post by RC211V on 2007-04-29
```
tcpdump -vvn -i eth0


 sudo tcpdump -vvn -i eth0
tcpdump: WARNING: eth0: no IPv4 address assigned
tcpdump: listening on eth0, link-type EN10MB (Ethernet), capture size 96 bytes

0 packets captured
0 packets received by filter
0 packets dropped by kernel

```

Had to ctr+c again.
I think i should go back to Edgy. It doesn't seem to work. Even though it worked with Feisty in the beginning.
Thanks anyway.

---

### Post by bnuytten on 2007-04-29
I would say gimme root access and I'll fix it, but without an IP address that's a little difficult ;-) It has nothing to do we Feisty alltogether, just the dhclient or the way it is executed that is not right.

I had the same problem here when I added an Interface (on Edgy) and it took my network provider over a day to assign me an (extra) IP address. Now working with Feisty and immediatly got an IP. So the problem was clearly on the provider's side. However I could kinda prove that by using tcpdump...

---

### Post by RC211V on 2007-04-29
No worries. I installed Edgy and its ok anyway. Thanks a lot for your support

---

### Post by BobW on 2007-04-29
Just wanted you aren't the only person with this problem. My ethernet connection works in Edgy but won't work with Fiesty. Didn't have time to figure out what was wrong so I ended up reinstalling Edgy.

---

### Post by bnuytten on 2007-04-30
For all those guys watching this thread that may have the same problem (or have problems with DHCP in general): is your computer directrly connected to the Internet or is there a router in between your Ubuntu box and Cable/DSL/whatever modem?

You can also tell the difference by the IP you normally get. If you get something like 10.x.x.x or 192.168.x.x chances are high that you have a router (acting as DHCP server) in between.

---

### Post by Alex&amp;Linux on 2007-04-30
Hey!

Ive just installed Ubuntu 6.06 on my Vista PC, internet was working in Ubuntu until I booted up in Vista again!
Network utility, showing Eth0 has only IPv6 and localhost connectivity!

Could this be caused by vista drivers ( I noticed upon booting into Vista that it had successfully "reinstalled drivers")?

Any help much appreciated!

---

### Post by bnuytten on 2007-04-30
> **Alex&Linux said:**
> Hey!

Ive just installed Ubuntu 6.06 on my Vista PC, internet was working in Ubuntu until I booted up in Vista again!
Network utility, showing Eth0 has only IPv6 and localhost connectivity!

Could this be caused by vista drivers ( I noticed upon booting into Vista that it had successfully "reinstalled drivers")?

Any help much appreciated!

I am not using Vista. But it reminds me of a nasty Windows XP habit. It does not properly release it's IP address (obtained via DHCP) when it is shut down or restarted. So subsequently when you start another OS, the DHCP first refuses to grant you another IP address since it has already granted one. I remember having that problem with some older Red Hat release and Windows XP. Uninstalling Windows :evil: or waiting a few hours did the trick.

A less drastic measure is to manually release the IP address before shutting down or restarting windows. If I remember well, this should do the trick:
```
ipconfig /release
```

---

### Post by Alex&amp;Linux on 2007-04-30
Man, I plan to get rid of Vista as soon as I can get this going with Beryl, and Wine!
I really appreciate the suggestion!
I have powercycled, and later logged into my router to stop/start DHCP server, no success, but im up for trying anything at this point!
I will give this a try and let you know if that was it.
If you have any more information at all, please reply!
Alternatively, youre welcome to mail me at  [email]ajn@onlinesupport.com[/email]

---

### Post by gmertr on 2007-04-30
Hi, I have trouble connecting with Fiesty, had no trouble with Edgy. Found that I am not getting an IP Address from DHCP Server. This is a wireless connection, with the broadcast ESSID shut off. If I turn on the broadcast ID, and reboot, it all works fine.
Is there a configuration setting I can set to allow it to connect without the Broadcast on? I always ran Edgy that way.
I also noticed, that the "iwlist ra0 scan" did not show my router.
Thanks for any help.
Steve

---

### Post by eiapoce on 2007-04-30
Hello there. If look for my previous post, there is a solution: [http://ubuntuforums.org/showthread.php?t=423766](http://ubuntuforums.org/showthread.php?t=423766)

In brief try just this while connected with the cable:

```
sudo ifconfig eth0 down
sudo ifconfig eth0 up 
```

When you do this with the dreaded connection manager running usually you get DHCP working... A good reason to be still skeptical about this tool.

---

### Post by gmertr on 2007-04-30
Hi, I don't have a wired connection. I had tried the
ifconfig ra0 down
ifconfig ra0 up
but it did not work.

---

### Post by notarikon on 2007-04-30
Hi, I'm having the same issue here as well. Things I've discovered so far though are:

1. This seems to happen a lot to people who use Automatix

2. If I call sudo /etc/init.d/dbus stop I can use my internet access again
```

 * Stopping System Tools Backends system-tools-backends                  [ OK ] 
 * Stopping network events dispatcher NetworkManagerDispatcher           [ OK ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [ OK ] 
 * Stopping network connection manager NetworkManager                    [ OK ] 
 * Stopping DHCP D-Bus daemon dhcdbd                                     [ OK ] 
 * Stopping Hardware abstraction layer hald                              [ OK ] 
 * Stopping system message bus dbus                                      [ OK ] 

```

I've tried removing the NetworkManager and NetworkManagerDispatcher events from the dbus events folder, but that made things worse.

I've also reinstalled the system-tools-backends and dbus to no avail.

3. I used to have the network manager icon in the system tray and if I disabled eth0 I got internet again via my USB connector to the router, but if it was active nothing worked

4. I also get the "The configuration could not be loaded - You are not allowed to access the system configuration" message when I try to access the Network option (among others) in the Control Panel. This also seems to be related to Automatix *grr*

If I call tcpdump after killing dbus I get a lot of info coming through with all packets received and none dropped.  If I call it before I get nothing at all.

Anyone else have any ideas?

---

### Post by bnuytten on 2007-05-01
> **Alex&Linux said:**
> I have powercycled, and later logged into my router to stop/start DHCP server, no success, but im up for trying anything at this point!


Aha! You're behind a router. This means you are in control and you can "work around" DHCP by manually assigning an IP address. If the problem really is in the dhclient of Ubuntu, manually configuring an IP address will solve your problem. If you have any success, please post your story here since it can help other people too :-)

---

### Post by bnuytten on 2007-05-01
> **notarikon said:**
> If I call tcpdump after killing dbus I get a lot of info coming through with all packets received and none dropped.  If I call it before I get nothing at all.

Anyone else have any ideas?

We already had a try with tcpdump and indeed there was no output at all. Simply 0 packets captured etc. D-Bus is actually some inter-process communication thing and as far as I know it shouldn't be normally stopped because it is an important process. But if it solves the tcpdump mystery it's worth the try :-)

D-Bus is running here, tcpdump works like it should and dhclient works fine. I have two interfaces, one on a router that receives it's private IP from my router and one directly connected to my provider which receives a public IP address from the provider's DHCP server.

---

### Post by gmertr on 2007-05-01
I tried manually assigning a valid IP Address, but it did not work. I used:
ifconfig ra0 up 192.168.1.10
(an open, valid address on my router).
The most telling thing, it seems, is that for me, it works if the Beacon is on. 
I like to leave it off to hide myself from casual observers. I ran it this way under Edgy without issue.
I one other computer that works (running other OS) with the Beacon off, and also my son's Nintendo DS works too.

---

### Post by gmertr on 2007-05-01
I tried the dhclient with the beacon on and off.  With Beacon off, it fails to obtain IP address. Gets it fine with beacon on. Seems to be the issue. Here is some output:
```

user@Cpu:~$ sudo dhclient ra0
Password:
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/<mac address hidden>
Sending on   LPF/ra0/<mac address hidden>
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
user@Cpu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30348 (29.6 KiB)  TX bytes:30348 (29.6 KiB)

ra0       Link encap:Ethernet  HWaddr <mac address hidden>
          inet6 addr: fe80::20c:41ff:fe6d:ac32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33539 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:1341560 (1.2 MiB)
          Interrupt:10 Base address:0x4000 

ra0:avahi Link encap:Ethernet  HWaddr <mac address hidden>
          inet addr:169.254.5.128  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:10 Base address:0x4000 

```

At this point, I go to another computer, turn on the beacon:

```

user@Cpu:~$ sudo dhclient ra0
There is already a pid file /var/run/dhclient.pid with pid 5859
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/ra0/<mac address hidden>
Sending on   LPF/ra0/<mac address hidden>
Sending on   Socket/fallback
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 5
DHCPOFFER from 192.168.1.1
DHCPREQUEST on ra0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.10 -- renewal in 40000 seconds.
user@Cpu:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:310 errors:0 dropped:0 overruns:0 frame:0
          TX packets:310 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:30348 (29.6 KiB)  TX bytes:30348 (29.6 KiB)

ra0       Link encap:Ethernet  HWaddr <mac address hidden>  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:41ff:fe6d:ac32/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:87 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46973 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1 txqueuelen:1000 
          RX bytes:28680 (28.0 KiB)  TX bytes:1879417 (1.7 MiB)
          Interrupt:10 Base address:0x4000 

```

Seems like a bug, in that dhcp fails when wireless Beacon is off. Thoughts?

---

### Post by kh4nh on 2007-05-01
> **bnuytten said:**
> Aha! You're behind a router. This means you are in control and you can "work around" DHCP by manually assigning an IP address. If the problem really is in the dhclient of Ubuntu, manually configuring an IP address will solve your problem. If you have any success, please post your story here since it can help other people too :-)


Manually configure your ip by editing this file: /etc/network/interfaces
I made the assumption that your network is 192.168.0.0, replace it if needed) 
```
auto eth0
iface eth0 inet static
        address   192.168.0.#          (replace # with your prefered number here 2 to 254)
        netmask   255.255.255.0
        network   192.168.0.0          
        broadcast 192.168.0.255
        gateway    192.168.0.1

```

2) Check your /etc/resolv.conf file:
Add ```
nameserver 192.168.0.1
``` if it is missing

---

### Post by bnuytten on 2007-05-02
> **gmertr said:**
> I tried the dhclient with the beacon on and off.  With Beacon off, it fails to obtain IP address. Gets it fine with beacon on. Seems to be the issue. Here is some output:

Seems like a bug, in that dhcp fails when wireless Beacon is off. Thoughts?

To my knowledge this will have nothing to do with dhclient. Have a look at this list and decide for yourself:
- dhcp on, beacon on: works
- dhcp on, beacon off: error
- dhcp off, beacon off: error

Let me predict the next result:
- dhcp off, beacon on: works

So according to me, as long as the beacon is on it will work. So what steps to take to determine the cause of your problem for 100% sure:
leave the beacon on, dhcp works ok
now configure your interface manually but leave the beacon on
now turn off the beacon, it will no longer work (doesn't matter if you use dhcp or manual assigned IP)

---

