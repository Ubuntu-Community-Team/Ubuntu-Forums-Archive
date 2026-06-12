---
title: "New Linux user and no net connection?"
date: 2007-06-09
forum: Networking &amp; Wireless
---

### Post by delichef on 2007-06-09
Hi: I am a new Linux user (1 week),  and have just installed Xubuntu on a 10 year
old Toshiba Tecra 8000, with a 20GB hard drive and 128MB or memory.

This laptop is wired to a Linksys WRT54G router, but does not get an
Internet connection. The cable is OK as I tested it on my other new laptop.

I have gone into Network Settings and selected automatic configuration.

I can supply screen shots, if required?

Can anyone suggest what I may have to do to connect to the net?

Thank you for any assistance you may provide.

The Deli Chef.

---

### Post by chili555 on 2007-06-09
Please open up a terminal and let us see:```
ifconfig eth0
sudo dhclient eth0
```Thanks, and could I please get a nice thick Reuben?

---

### Post by delichef on 2007-06-09
Hi chili555:

Here is the link to a screen shot of the command output:

[http://tinyurl.com/2nrxnn](http://tinyurl.com/2nrxnn)

If you can help me get it working, I'll supply the sauerkraut free ;)

Thanks 

The Deli Chef

---

### Post by chili555 on 2007-06-09
Let's see **ifconfig** please; not ipconfig. Thanks. Also, while we're at it:```
sudo ethtool eth0
```

---

### Post by delichef on 2007-06-09
Sorry about that:

Here are the new screen shots

[http://tinyurl.com/2nrxnn](http://tinyurl.com/2nrxnn)

The Deli Chef

---

### Post by boomdiddy on 2007-06-09
instead of taking pics on your camera phone, maybe you should see if you have the screen shot app installed under applications -> accessories, or better yet, just copy and paste the output of the commands into your post. :)

---

### Post by delichef on 2007-06-09
I'm not using a camera phone, I'm using a digital camera.

I did say I am a new user to Linux (1 week). I would love to copy and paste the output into my posts, bu I can't get on the net with my old Tecra 8000. I'm using my other computer to seek advise.

Thanks for your comments.

The Deli Chef

---

### Post by chili555 on 2007-06-09
Ahh! The old *avahi *and 169.xx IP address. This may be related to this bug: [https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/78078](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/78078)

The fix that seems like it fixes the problem most often is to reinstall avahi-autoipd . Avahi is on your install CD, so we can do this without internet access. Here are the steps. Pop the install CD in the drive and issue the following terminal commands:```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get --purge install avahi-autoipd --reinstall
```Reboot and see if eth0 has a proper IP address with *ifconfig.* On your Linksys router, it should be 192.168.x.x.

---

### Post by delichef on 2007-06-09
I'm not sure what of the screen shot below I should be showing on this forum, but this is the output of cfconfig after installing CD and doing as previously requested.

 Interrupt:11 Base address:0x1800 
eth0:avah Link encap:Ethernet  HWaddr 00:4C:69:6E:75:79  

          inet addr:169.254.6.154  Bcast:169.254.255.255  
Mask:255.255.0.0
          
UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          
Interrupt:11 Base address:0x1800 

lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0
          
          inet6 addr: ::1/128 Scope:Host
          
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          
          collisions:0 txqueuelen:0 
          
          RX bytes:592 (592.0 b)  TX bytes:592 (592.0 b)

Thanks
The Deli Chef

---

### Post by chili555 on 2007-06-10
Please go to System -> Administration -> Network and make sure your ethernet interface, eth0, is enabled and that 'Roaming' is *not* selected.

Also, please let me see the eth0 portion of the following terminal command:```
cat /etc/network/interfaces
```Thanks.

---

### Post by delichef on 2007-06-10
Hi chili555
Been out golfing all day and just got back home.

Please go to System -> Administration -> Network and make sure your ethernet interface, eth0, is enabled and that 'Roaming' is not selected.

My settings in xubuntu have been: 
[LIST]
[*]Wired Connection Address: dhcp
[*]Properties: Automatic configuration (DHCP)
[*]Enable This Connection checkbox is checked
[*]Automatic Service Discover checkbox left unchecked
[/LIST]

Also, please let me see the eth0 portion of the following terminal command:
Code:

cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface

auto lo

iface lo inet loopback


iface eth0 inet dhcp

auto eth0

---

### Post by chili555 on 2007-06-13
Sorry to be delayed answering, but this is a toughie! If I get my Reuben, I will have earned it! Please try these commands:```
sudo /etc/init.d/avahi-daemon stop
sudo dhclient eth0
```Does *dhclient* time out or grab an IP address? Also, please let me see the output of:```
cat /etc/default/avahi-daemon
```Thanks.

---

### Post by delichef on 2007-06-13
Hi chili555:
If you get me up and on the net, give me the phone number of your favorite deli, and I will ensure you have your Rueben(s) with whatever topping you desire...
 
Here is the output of your requested commands:
Note it did not seem to "time out", as it did not take but a couple of seconds.
The Deli Chef

sudo /etc/init.d/avahi-daemon stop

* Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                                           [ OK ] 

allan@ubuntu:/$ sudo dhclient eth0

Internet Systems Consortium DHCP Client V3.0.4

Copyright 2004-2006 Internet Systems Consortium.

All rights reserved.

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
--------------------------------------------------------------------------------------------------------

Listening on LPF/eth0/00:4c:69:6e:75:79

Sending on   LPF/eth0/00:4c:69:6e:75:79

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1

No DHCPOFFERS received.

No working leases in persistent database - sleeping.

allan@ubuntu:/$ 



cat /etc/default/avahi-daemon

# 0 = don't start, 1 = start

AVAHI_DAEMON_START=1

allan@ubuntu:/$

---

### Post by delichef on 2007-06-13
chili555
I had the wrong configuration. Someone had me change to Static IP address to try something. I am sending another output of your request.
The deli Chef

---

### Post by delichef on 2007-06-13
chili555:
Adjusted output after changing back to Wired Connection Address dhcp:

sudo /etc/init.d/avahi-daemon stop
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                                           [fail] 
allan@ubuntu:/$ sudo dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 5192
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


cat /etc/default/avahi-daemon
# 0 = don't start, 1 = start
AVAHI_DAEMON_START=1
allan@ubuntu:/$ 

The Deli Chef

---

### Post by chili555 on 2007-06-14
> your favorite deliWell, that's the problem. It's nice and quiet out by the lake, but, so far, we lack a decent deli, butcher or wine shop and I haven't seen a bialy in a year! 

What we are trying to do here is get Avahi out of the way, perhaps temporarily, so we can get your ethernet working.

Your *sudo ethtool eth0* screenshot has gone away. All I want to know is Link detected. If it is No, then we need to look at the cable or router.

We haven't looked at the actual hardware and driver. Can you let me see:```
sudo lshw -C network
```You may get two sections, one for the ethernet and one for wireless, if you have it. All we need to see is ethernet.

---

### Post by delichef on 2007-06-14
Hi chili555
Sounds like me you may be retired? You may have to open your own deli. Could be an opportunity at the lake? Trust me thought, it's hard work.

I put the page back up at for sudo ethtool eth0  at: [http://www3.telus.net/public/ascahill/Linux.htm](http://www3.telus.net/public/ascahill/Linux.htm) 

Here is the output of your request:

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: DECchip 21142/43
       vendor: Digital Equipment Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 30
       serial: 00:4c:69:6e:75:79
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical
       configuration: broadcast=yes driver=tulip driverversion=1.1.14 latency=64 maxlatency=40 mingnt=20 multicast=yes
       resources: ioport:1800-187f iomemory:2c000000-2c00007f irq:11

I have no wireless in this old Toshiba, it's hard wired to my router. The cable is OK as I tried it on my new laptop.
Thanks
The Deli Chef

---

### Post by chili555 on 2007-06-14
Retired is one word for it....I guess I could drive to Charlotte, but it seems a waste of precious fossil fuels to drive 45 minutes for lunch!> it's hard work.And this ethernet card isn't?

Let's take a look at:```
lsmod | grep tulip
sudo cat /var/log/messages | grep eth0
sudo cat /var/log/messages | grep tulip
```By the way, if you have a USB key, you can transfer the files to your other computer that way. Just *lsmod | grep tulip > tulip.txt* and you will create a text file you can drag-n-drop to your USB key for reading, and pasting to this forum.

---

### Post by delichef on 2007-06-14
Hi:
Pretty long list, but I wasn't sure if you needed everything?
I have been copying the outputs to my usb, but did not know about the tulip command. I have been using Abiword.

lsmod | grep eth0
allan@ubuntu:/$ sudo cat /var/log/messages | grep eth0
Password:
Jun 11 15:27:40 ubuntu kernel: [  725.887617] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:27:40 ubuntu kernel: [  725.887676] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 11 15:27:48 ubuntu kernel: [  733.886505] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:27:48 ubuntu kernel: [  733.886558] eth0: 21140 transmit timed out, status f0260000, SIA 000020c6 ffff0001 fff8ffbf 8ff1c008, resetting...
Jun 11 15:27:56 ubuntu kernel: [  741.885396] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:27:56 ubuntu kernel: [  741.885451] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 11 15:30:00 ubuntu kernel: [  865.868192] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:30:00 ubuntu kernel: [  865.868250] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fffbff7f 8ff0c008, resetting...
Jun 11 15:30:08 ubuntu kernel: [  873.867081] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:30:08 ubuntu kernel: [  873.867139] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fff8ffbf 8ff2c008, resetting...
Jun 11 15:30:20 ubuntu kernel: [  885.865409] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 15:30:20 ubuntu kernel: [  885.865467] eth0: 21140 transmit timed out, status f0260000, SIA 000020c6 ffff0001 fff8ffbf 8ff1c008, resetting...
Jun 11 16:12:04 ubuntu kernel: [ 3389.517870] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:12:04 ubuntu kernel: [ 3389.517926] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:12:44 ubuntu kernel: [ 3429.512318] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:12:44 ubuntu kernel: [ 3429.512372] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:13:28 ubuntu kernel: [ 3473.506212] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:13:28 ubuntu kernel: [ 3473.506267] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:14:12 ubuntu kernel: [ 3517.500106] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:14:12 ubuntu kernel: [ 3517.500162] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:14:52 ubuntu kernel: [ 3557.494554] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:14:52 ubuntu kernel: [ 3557.494612] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:15:32 ubuntu kernel: [ 3597.489002] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:15:32 ubuntu kernel: [ 3597.489060] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:16:12 ubuntu kernel: [ 3637.483451] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:16:12 ubuntu kernel: [ 3637.483508] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:16:44 ubuntu kernel: [ 3669.479019] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:16:44 ubuntu kernel: [ 3669.479081] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:17:16 ubuntu kernel: [ 3701.474567] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:17:16 ubuntu kernel: [ 3701.474621] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:17:48 ubuntu kernel: [ 3733.470127] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:17:48 ubuntu kernel: [ 3733.470182] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:18:20 ubuntu kernel: [ 3765.465684] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:18:20 ubuntu kernel: [ 3765.465738] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:18:52 ubuntu kernel: [ 3797.461243] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:18:52 ubuntu kernel: [ 3797.461299] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:19:24 ubuntu kernel: [ 3829.456802] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:19:24 ubuntu kernel: [ 3829.456858] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:19:56 ubuntu kernel: [ 3861.452360] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:19:56 ubuntu kernel: [ 3861.452415] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:20:24 ubuntu kernel: [ 3889.448476] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:20:24 ubuntu kernel: [ 3889.448531] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:20:56 ubuntu kernel: [ 3921.444032] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:20:56 ubuntu kernel: [ 3921.444085] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:21:28 ubuntu kernel: [ 3953.439592] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:21:28 ubuntu kernel: [ 3953.439648] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:22:08 ubuntu kernel: [ 3993.434045] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:22:08 ubuntu kernel: [ 3993.434107] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:22:44 ubuntu kernel: [ 4029.429048] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:22:44 ubuntu kernel: [ 4029.429115] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:23:24 ubuntu kernel: [ 4069.423493] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:23:24 ubuntu kernel: [ 4069.423549] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:23:56 ubuntu kernel: [ 4101.419056] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:23:56 ubuntu kernel: [ 4101.419125] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:24:36 ubuntu kernel: [ 4141.413518] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:24:36 ubuntu kernel: [ 4141.413587] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:25:16 ubuntu kernel: [ 4181.407968] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:25:16 ubuntu kernel: [ 4181.408040] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:25:56 ubuntu kernel: [ 4221.402421] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:25:56 ubuntu kernel: [ 4221.402482] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:26:36 ubuntu kernel: [ 4261.396868] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:26:36 ubuntu kernel: [ 4261.396923] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:27:12 ubuntu kernel: [ 4297.391853] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:27:12 ubuntu kernel: [ 4297.391915] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:27:56 ubuntu kernel: [ 4341.385741] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:27:56 ubuntu kernel: [ 4341.385800] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:28:36 ubuntu kernel: [ 4381.380192] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:28:36 ubuntu kernel: [ 4381.380252] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:29:16 ubuntu kernel: [ 4421.374638] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:29:16 ubuntu kernel: [ 4421.374697] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:29:56 ubuntu kernel: [ 4461.369086] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:29:56 ubuntu kernel: [ 4461.369146] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:30:40 ubuntu kernel: [ 4505.362979] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:30:40 ubuntu kernel: [ 4505.363040] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:31:24 ubuntu kernel: [ 4549.356874] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:31:24 ubuntu kernel: [ 4549.356934] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:32:04 ubuntu kernel: [ 4589.351321] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:32:04 ubuntu kernel: [ 4589.351382] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:32:48 ubuntu kernel: [ 4633.345214] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:32:48 ubuntu kernel: [ 4633.345275] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:33:32 ubuntu kernel: [ 4677.339108] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:33:32 ubuntu kernel: [ 4677.339168] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:34:12 ubuntu kernel: [ 4717.333556] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:34:12 ubuntu kernel: [ 4717.333616] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:34:56 ubuntu kernel: [ 4761.327448] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:34:56 ubuntu kernel: [ 4761.327507] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:35:32 ubuntu kernel: [ 4797.322452] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:35:32 ubuntu kernel: [ 4797.322513] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:36:16 ubuntu kernel: [ 4841.316344] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:36:16 ubuntu kernel: [ 4841.316404] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:36:56 ubuntu kernel: [ 4881.310793] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:36:56 ubuntu kernel: [ 4881.310852] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:37:40 ubuntu kernel: [ 4925.304686] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:37:40 ubuntu kernel: [ 4925.304745] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:38:24 ubuntu kernel: [ 4969.298579] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:38:24 ubuntu kernel: [ 4969.298640] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:39:04 ubuntu kernel: [ 5009.293028] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:39:04 ubuntu kernel: [ 5009.293089] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:39:48 ubuntu kernel: [ 5053.286922] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:39:48 ubuntu kernel: [ 5053.286982] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:40:24 ubuntu kernel: [ 5089.281925] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:40:24 ubuntu kernel: [ 5089.281985] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:41:08 ubuntu kernel: [ 5133.275818] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:41:08 ubuntu kernel: [ 5133.275878] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:41:52 ubuntu kernel: [ 5177.269710] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:41:52 ubuntu kernel: [ 5177.269770] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:42:32 ubuntu kernel: [ 5217.264159] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:42:32 ubuntu kernel: [ 5217.264219] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:43:16 ubuntu kernel: [ 5261.258053] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:43:16 ubuntu kernel: [ 5261.258112] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:44:00 ubuntu kernel: [ 5305.251945] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:44:00 ubuntu kernel: [ 5305.252005] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:44:40 ubuntu kernel: [ 5345.246393] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:44:40 ubuntu kernel: [ 5345.246452] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:45:20 ubuntu kernel: [ 5385.240841] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:45:20 ubuntu kernel: [ 5385.240900] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:46:00 ubuntu kernel: [ 5425.235290] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:46:00 ubuntu kernel: [ 5425.235350] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:46:44 ubuntu kernel: [ 5469.229183] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:46:44 ubuntu kernel: [ 5469.229242] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:47:28 ubuntu kernel: [ 5513.223076] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:47:28 ubuntu kernel: [ 5513.223137] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:48:08 ubuntu kernel: [ 5553.217524] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:48:08 ubuntu kernel: [ 5553.217584] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:48:52 ubuntu kernel: [ 5597.211418] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:48:52 ubuntu kernel: [ 5597.211479] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:49:32 ubuntu kernel: [ 5637.205866] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:49:32 ubuntu kernel: [ 5637.205926] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:50:12 ubuntu kernel: [ 5677.200315] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:50:12 ubuntu kernel: [ 5677.200375] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:50:56 ubuntu kernel: [ 5721.194206] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:50:56 ubuntu kernel: [ 5721.194266] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:51:40 ubuntu kernel: [ 5765.188100] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:51:40 ubuntu kernel: [ 5765.188159] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:52:20 ubuntu kernel: [ 5805.182549] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:52:20 ubuntu kernel: [ 5805.182608] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:53:04 ubuntu kernel: [ 5849.176442] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:53:04 ubuntu kernel: [ 5849.176502] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:53:48 ubuntu kernel: [ 5893.170336] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:53:48 ubuntu kernel: [ 5893.170396] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:54:24 ubuntu kernel: [ 5929.165338] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:54:24 ubuntu kernel: [ 5929.165398] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:55:08 ubuntu kernel: [ 5973.159232] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:55:08 ubuntu kernel: [ 5973.159292] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:55:48 ubuntu kernel: [ 6013.153680] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:55:48 ubuntu kernel: [ 6013.153740] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:56:32 ubuntu kernel: [ 6057.147573] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:56:32 ubuntu kernel: [ 6057.147633] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:57:16 ubuntu kernel: [ 6101.141466] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:57:16 ubuntu kernel: [ 6101.141525] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:57:56 ubuntu kernel: [ 6141.135914] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:57:56 ubuntu kernel: [ 6141.135974] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:58:40 ubuntu kernel: [ 6185.129807] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:58:40 ubuntu kernel: [ 6185.129868] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 16:59:24 ubuntu kernel: [ 6229.123702] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 16:59:24 ubuntu kernel: [ 6229.123762] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:00:04 ubuntu kernel: [ 6269.118149] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:00:04 ubuntu kernel: [ 6269.118209] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:00:48 ubuntu kernel: [ 6313.112043] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:00:48 ubuntu kernel: [ 6313.112103] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:01:32 ubuntu kernel: [ 6357.105934] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:01:32 ubuntu kernel: [ 6357.105994] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:02:08 ubuntu kernel: [ 6393.100938] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:02:08 ubuntu kernel: [ 6393.100998] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:02:52 ubuntu kernel: [ 6437.094832] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:02:52 ubuntu kernel: [ 6437.094891] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:03:32 ubuntu kernel: [ 6477.089280] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:03:32 ubuntu kernel: [ 6477.089340] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:04:16 ubuntu kernel: [ 6521.083172] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:04:16 ubuntu kernel: [ 6521.083232] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:05:00 ubuntu kernel: [ 6565.077070] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:05:00 ubuntu kernel: [ 6565.077127] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:05:40 ubuntu kernel: [ 6605.071513] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:05:40 ubuntu kernel: [ 6605.071572] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:06:24 ubuntu kernel: [ 6649.065408] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:06:24 ubuntu kernel: [ 6649.065468] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:12:16 ubuntu kernel: [ 7001.016550] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:12:16 ubuntu kernel: [ 7001.016604] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 17:24:04 ubuntu kernel: [ 7708.918297] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 17:24:04 ubuntu kernel: [ 7708.918355] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 18:06:28 ubuntu kernel: [10252.565195] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 18:06:28 ubuntu kernel: [10252.565252] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 18:48:08 ubuntu kernel: [12752.218212] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 18:48:08 ubuntu kernel: [12752.218269] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 19:41:08 ubuntu kernel: [15931.776858] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 19:41:08 ubuntu kernel: [15931.776912] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 20:23:52 ubuntu kernel: [18495.420984] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 20:23:52 ubuntu kernel: [18495.421039] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 21:17:44 ubuntu kernel: [21726.972406] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 21:17:44 ubuntu kernel: [21726.972461] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 22:03:24 ubuntu kernel: [24466.592112] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 22:03:24 ubuntu kernel: [24466.592169] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 22:48:12 ubuntu kernel: [27154.219060] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 22:48:12 ubuntu kernel: [27154.219115] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 11 23:14:48 ubuntu kernel: [28749.997524] NETDEV WATCHDOG: eth0: transmit timed out
Jun 11 23:14:48 ubuntu kernel: [28749.997584] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 12 15:23:29 ubuntu kernel: [   80.886618] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
Jun 13 08:45:02 ubuntu kernel: [   87.933254] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
Jun 13 08:51:45 ubuntu kernel: [  490.911615] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
Jun 13 14:36:50 ubuntu kernel: [   79.683902] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
Jun 13 20:43:18 ubuntu kernel: [22072.548927] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:43:18 ubuntu kernel: [22072.548986] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:43:26 ubuntu kernel: [22080.547815] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:43:26 ubuntu kernel: [22080.547873] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:43:34 ubuntu kernel: [22088.546702] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:43:34 ubuntu kernel: [22088.546755] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fff8ffbf 8ff2c008, resetting...
Jun 13 20:43:42 ubuntu kernel: [22096.545593] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:43:42 ubuntu kernel: [22096.545644] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:43:54 ubuntu kernel: [22108.543927] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:43:54 ubuntu kernel: [22108.543979] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:44:02 ubuntu kernel: [22116.542819] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:44:02 ubuntu kernel: [22116.542876] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:44:10 ubuntu kernel: [22124.541709] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:44:10 ubuntu kernel: [22124.541760] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fffbff7f 8ff0c008, resetting...
Jun 13 20:44:18 ubuntu kernel: [22132.540599] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:44:18 ubuntu kernel: [22132.540656] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:44:26 ubuntu kernel: [22140.539488] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:44:26 ubuntu kernel: [22140.539544] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:44:34 ubuntu kernel: [22148.538375] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:44:34 ubuntu kernel: [22148.538428] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:47:38 ubuntu kernel: [22332.512858] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:47:38 ubuntu kernel: [22332.512921] eth0: 21140 transmit timed out, status f0260000, SIA 000010c6 ffff0001 fff8ffbf 8ff1c008, resetting...
Jun 13 20:47:46 ubuntu kernel: [22340.511729] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:47:46 ubuntu kernel: [22340.511787] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:47:54 ubuntu kernel: [22348.510618] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:47:54 ubuntu kernel: [22348.510672] eth0: 21140 transmit timed out, status f0260000, SIA 000020c6 ffff0001 fff8ffbf 8ff1c008, resetting...
Jun 13 20:48:02 ubuntu kernel: [22356.509519] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:48:02 ubuntu kernel: [22356.509576] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:50:46 ubuntu kernel: [22520.486745] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:50:46 ubuntu kernel: [22520.486799] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:50:54 ubuntu kernel: [22528.485634] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:50:54 ubuntu kernel: [22528.485685] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:51:02 ubuntu kernel: [22536.484526] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:51:02 ubuntu kernel: [22536.484583] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fff8ffbf 8ff2c008, resetting...
Jun 13 20:53:54 ubuntu kernel: [22708.460653] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:53:54 ubuntu kernel: [22708.460706] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fff8ffbf 8ff2c008, resetting...
Jun 13 20:54:02 ubuntu kernel: [22716.459542] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:54:02 ubuntu kernel: [22716.459599] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0000 fffbff7f 8ff0c008, resetting...
Jun 13 20:54:14 ubuntu kernel: [22728.457875] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 20:54:14 ubuntu kernel: [22728.457928] eth0: 21140 transmit timed out, status f0260000, SIA 000000c6 ffff0001 fffbff7f 8ff0c008, resetting...
Jun 13 21:16:14 ubuntu kernel: [24048.274670] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 21:16:14 ubuntu kernel: [24048.274727] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 13 21:38:14 ubuntu kernel: [25368.091470] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 21:38:14 ubuntu kernel: [25368.091524] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 13 22:02:22 ubuntu kernel: [26815.890490] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 22:02:22 ubuntu kernel: [26815.890546] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 13 22:29:14 ubuntu kernel: [28427.666757] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 22:29:14 ubuntu kernel: [28427.666813] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 13 22:49:10 ubuntu kernel: [29623.500772] NETDEV WATCHDOG: eth0: transmit timed out
Jun 13 22:49:10 ubuntu kernel: [29623.500829] eth0: 21140 transmit timed out, status f0660000, SIA 000000c5 ffff0001 fffbff7f 8ff1c008, resetting...
Jun 14 09:29:24 ubuntu kernel: [   80.617499] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
Jun 14 11:31:54 ubuntu kernel: [   92.879230] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.
allan@ubuntu:/$ sudo cat /var/log/messages | grep tulip

The Deli Chef

---

### Post by ajlewis2 on 2007-06-14
Mostly I see tulip for this chip, but I found one guy back in 2003 who got his ethernet going with de4x5 instead of tulip. He has version 30 of this chipset too. Maybe since this is an old machine, the de4x5 will work on it.  

Here is where he states it is working where the tulip wasn't:
[http://archives.neohapsis.com/archives/linux/axp/2003-q2/0085.html](http://archives.neohapsis.com/archives/linux/axp/2003-q2/0085.html)

In here you see that he has the same chip as delichef:

[http://archives.neohapsis.com/archives/linux/axp/2003-q2/0083.html](http://archives.neohapsis.com/archives/linux/axp/2003-q2/0083.html)

I'm guessing that tulip would need to be blacklisted and de4x5 put into /etc/modules.  chili555, if you think that makes sense, I think you can lead the way through it better than I can.  If not, I'll take a stab at it.

Anita

---

### Post by chili555 on 2007-06-14
Gang-
I think this is our problem:> EEPROM not present,Also, I should have asked for:```
sudo cat /var/log/messages | grep **-i** tulip
```-i means 'case-insensitive' meaning we will get Tulip, tulip, TULIP, etc. Would you please run that?

Notice the entries are sorted by date? You only need post the last day, unless you see something remarkable.

I am going back to Google/Linux and wanted to give you a progress report.

---

### Post by ajlewis2 on 2007-06-14
> **ajlewis2 said:**
> 
I'm guessing that tulip would need to be blacklisted and de4x5 put into /etc/modules.  chili555, if you think that makes sense, I think you can lead the way through it better than I can.  If not, I'll take a stab at it.

Anita

I see that /etc/modprobe.d/blacklist has de4x5 blacklisted with a comment that tulip replaces it.  I wonder why the driver is still available in the kernel modules.  Oh, well, I don't have that chipset; so no way to try it out.  The guy who found it worked when tulip did not was posting in 2003.  I don't find anything recent.  Would it be worth a try to test it with something like?:

```
sudo modprobe -r tulip
sudo modprobe -i de4x5
sudo /etc/init.d/networking restart
```

Anita

---

### Post by chili555 on 2007-06-14
It would, except you might need ```
sudo rmmod -f tulip
```Best way to find out is to try it.

---

### Post by delichef on 2007-06-15
Hi:
Output of both your commands, but trust me. it's getting complicated for my tiny brain...:)

allan@ubuntu:/$ sudo cat /var/log/messages | grep -i tulip
Jun 14 11:31:54 ubuntu kernel: [   92.879230] eth0: Digital DS21142/DS21143 Tulip rev 48 at Port 0x1800, EEPROM not present, 00:4C:69:6E:75:79, IRQ 11.

--------------------------------------------------------------------------------
 sudo modprobe -r tulip
allan@ubuntu:/$ sudo modprobe -i de4x5

allan@ubuntu:/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              Cannot find device "eth0"
There is already a pid file /var/run/dhclient.eth0.pid with pid 4326
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Bind socket to interface: No such device
eth0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
--------------------------------------------------------                                                                                             [ OK ]
allan@ubuntu:/$ sudo rmmod -f tulip
ERROR: Removing 'tulip': No such file or directory

---

### Post by ajlewis2 on 2007-06-15
I can only imagine how this looks to a newbie!  You are doing well in doing the commands and giving the output.

Ok, the first modprobe -r removed the tulip module as we can see in the command 'rmmod -f tulip' which shows it isn't there.

'modprobe -i de4x5' installed the other module which we can tell because there was no output complaining about it. :-)

However, the restart of the networking shows that the module is not working, because eth0 doesn't exist, unless for some reason it would have given it a different name. To find out do:

```
ifconfig
```

But I really don't see why it would not be eth0 like with the tulip if it was working.  Check just to see for sure.  If there is a 'eth1' then that is a good sign.  If there is no 'eth' at all, then you need to put tulip back.  Do those same modprobe commands again, but reverse the drivers removing the de4x5 and putting back the tulip.  Then restart the network as before.  

The de4x5 isn't working, it seems.  

Anita

---

### Post by ajlewis2 on 2007-06-15
chili555, I found a post where a guy couldn't get the network after a cold boot, but after a reboot, it worked.  The interesting part is that in the output from both, the 'EEPROM not present' message is present.  
[http://uwsg.indiana.edu/hypermail/linux/kernel/0409.0/0565.html](http://uwsg.indiana.edu/hypermail/linux/kernel/0409.0/0565.html)
-----
Before:
tulip1: ***WARNING***: No MII transceiver found!
eth1: Digital DS21143 Tulip rev 33 at 0xe2811f00, EEPROM not present, 00:00:D1:1B:EF:2F, IRQ 11.

After:
tulip1: MII transceiver #1 config 3100 status 7849 advertising 01e1.
eth1: Digital DS21143 Tulip rev 33 at 0xe2811f00, EEPROM not present, 00:00:D1:1B:EF:2F, IRQ 11.
-----

That would indicate to me that this part of the message is not the problem, right?

Anita

---

### Post by ajlewis2 on 2007-06-15
I made a mistake on the modprobe commands.

modprobe -r does remove the module, but the other command should not have the -i in it. 

So when you run the command to put tulip back in:

```

sudo modprobe -r de4x5
sudo modprobe tulip
sudo /etc/init.d/networking restart

```

Sorry for the mistake.  I don't think it really affected the installing of the de4x5 module, but I want to be sure it doesn't mess up the installing of the tulip.

Anita

---

### Post by delichef on 2007-06-15
Hi:
Just so I understand.
The only commands I should make are these and nothing else?

sudo modprobe -r de4x5
sudo modprobe tulip
sudo /etc/init.d/networking restart

The Deli Chef

---

### Post by ajlewis2 on 2007-06-15
> **delichef said:**
> Hi:
Just so I understand.
The only commands I should make are these and nothing else?

sudo modprobe -r de4x5
sudo modprobe tulip
sudo /etc/init.d/networking restart

The Deli Chef

Yes, that is it for now.  Those commands will remove the test driver and put the tulip driver back in.  Then it will attempt to restart the network.  I'm sorry that the other driver didn't work, but it was worth a try.

By the way, is this an internal ethernet card or is it one that you stick into the slot on your laptop?  If it goes into the slot, could you look at it to see what kind it is.  Maybe it will help our searching.

Anita

---

### Post by delichef on 2007-06-15
*Quote: By the way, is this an internal ethernet card or is it one that you stick into the slot on your laptop? If it goes into the slot, could you look at it to see what kind it is. Maybe it will help our searching.*

As regards my pcmcia card: The card is pcmcia and is a Xircom Cardbus Ethernet 10/100 Mbps 32bit

Additional information. My router has WPA security and also has a separate password to get
into the settings. I mention this, just in case it may have something to do with my
problem. So far I have not been able to see the password screen when
trying to access it with my old Toshiba.

Output of commands:

sudo modprobe -r de4x5
allan@ubuntu:/$ sudo modprobe tulip
allan@ubuntu:/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                              RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 4594
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                                             [ OK ]

For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
                                                                                             [ OK ]
allan@ubuntu:/$ sudo rmmod -f tulip
ERROR: Removing 'tulip': No such file or directory

The Deli Chef

---

### Post by chili555 on 2007-06-15
Deli-

Please try the following commands in order and you can summarize the results. 'I got an IP address' or 'timed out' is sufficient.```
sudo modprobe tulip
sudo modprobe xircom_cb
sudo dhclient eth0
```You have a Best Buy near the deli?

---

### Post by delichef on 2007-06-15
Hi:
Nearest Best Buy to me is 180 miles away.

sudo modprobe tulip

sudo modprobe xircom_cb
sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 16
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


The Deli Chef

---

### Post by ajlewis2 on 2007-06-15
maybe the xircom_tulip_cb

[http://www.tamacom.com/tour/kernel/linux/S/9161.html](http://www.tamacom.com/tour/kernel/linux/S/9161.html)

It says:
"This device driver was forked from the driver for the DECchip "Tulip",
 Digital's single-chip ethernet controllers for PCI.  It supports Xircom's
 almost-Tulip-compatible CBE-100 CardBus adapters."

I would like to see what all tulip type things are loaded; so I've stuck a lsmod command in there.  
I would try:

```

sudo modprobe xircom_tulip_cb
lsmod |grep tulip
sudo /etc/init.d/networking restart
```

---

### Post by chili555 on 2007-06-15
Anita-

Do you have a:```
/lib/modules/...../xircom_tulip_cb.ko
```Because I don't and I doubt DC does, either. I still think the problem is EEPROM, which I have been studying for hours...minus a trip to the local pizza joint.

---

### Post by ajlewis2 on 2007-06-15
Yes I do: 

/lib/modules/2.6.20-16-386/kernel/drivers/net/tulip/xircom_tulip_cb.ko

And I think DC has it too, because I am running Feisty Ubuntu and DC has the same thing in the Xubuntu flavor.

Anita

---

### Post by chili555 on 2007-06-15
Well, I will be very interested to know. Here is the output from my terminal:```
chili@LAPTOP60:~$ locate xircom
/lib/modules/2.6.17-11-generic/kernel/drivers/net/tulip/xircom_cb.ko
/lib/modules/2.6.20-16-generic/kernel/drivers/net/tulip/xircom_cb.ko
/lib/modules/2.6.20-15-generic/kernel/drivers/net/tulip/xircom_cb.ko
/usr/src/linux-headers-2.6.20-16-generic/include/config/usb/serial/xircom.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/pcmcia/xircom.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/usb/serial/xircom.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/pcmcia/xircom.h
```As you can see, I run 2.6.20-16, Feisty, and xircom_tulip_cb.ko is AWOL.

Try it, DC, and let us know.

---

### Post by delichef on 2007-06-15
Output of Anita's request:

sudo modprobe xircom_tulip_cb
Password:
FATAL: Module xircom_tulip_cb not found.
allan@ubuntu:/$ lsmod |grep tulip
tulip                  53536  0 
allan@ubuntu:/$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                             
 RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 4581
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
There is already a pid file /var/run/dhclient.eth0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:4c:69:6e:75:79
Sending on   LPF/eth0/00:4c:69:6e:75:79
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

The Deli Chef

---

### Post by ajlewis2 on 2007-06-15
$ dpkg -S xircom_tulip_cb.ko

linux-image-2.6.20-16-386: /lib/modules/2.6.20-16-386/kernel/drivers/net/tulip/xircom_tulip_cb.ko

I guess both of you have the generic kernel and I have 386.  I'm not sure why that would be.  Probably the way I installed my system which was as I recall an upgrade from Dapper to Edgy and then to Feisty.  :-)  

I'm not sure what to recommend at this point. I can see that only the generic is on the install disk for Xubuntu, because I have the disk and don't see the 386 image in the Package list.  

I also have it for the 2.6.20-15-386.  It is a 23Kb file which I could send, but I have no idea if it would work with the generic kernel.

Anita

---

### Post by chili555 on 2007-06-16
I have been googling this subject so long now, I am finding my own posts!

> Listening on LPF/eth0/00:4c:69:6e:75:79This is a bogus MAC address that gets used when the card won't report it at all, or at least correctly. 

I have a few ideas. First, let's have a peek at:```
sudo cat /var/log/messages | grep irqpoll
```Second, does the card work correctly, that is get an IP address and connect to the internet if you withdraw the card before booting and then, after the computer is fully booted and you are logged in, insert the card with the cable plugged in?

Third, please drop your install CD in the tray and:```
sudo apt-get install nictools-pci
sudo tulip-diag -ev
```Please post back and let us know.

---

### Post by delichef on 2007-06-16
Hi:
I followed your commands in the following order:

sudo cat /var/log/messages | grep irqpoll
allan@ubuntu:/$ 

I then shutdown and plugged the pcmcia card and waited for it to fully boot. When I plugged it in, I could hear some churning inside the laptop. I tried to log onto Google and got "Server not found"
I then pinged the router and received:

ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.133 ms
--- 192.168.1.2 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7998ms
rtt min/avg/max/mdev = 0.111/0.115/0.133/0.015 ms

Lastly I inserted the install cd and followed your last request:

sudo apt-get install nictools-pci
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nictools-pci is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nictools-pci has no installation candidate
allan@ubuntu:/$ 

sudo tulip-diag -ev
sudo: tulip-diag: command not found
allan@ubuntu:/$ 

The Deli Chef

---

### Post by chili555 on 2007-06-16
> ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.133 msWell! Something is finally working! Are you sure 192.168.1.2 is your router? Routers usually like to first in line and so are generally x.x.1. May we see:```
ifconfig eth0
route -n
cat /etc/resolv.conf
```Thanks.

---

### Post by ajlewis2 on 2007-06-16
Previous information on our mailing list was that it was 192.168.1.1.  I had him use that 192.168.1.2 address as a static IP for the laptop.  I think that is why it is pinging so nicely. :-)

Anita

---

### Post by chili555 on 2007-06-16
Anita-
I sorta figured from the remarkably low ping times.

DC-
Could you add to the list of commands we'd like:```
ping -c3 192.168.1.1
ping -c3 216.239.51.104
```Thanks.

---

### Post by delichef on 2007-06-16
[I]Quote:
ifconfig eth0
route -n
cat /etc/resolv.conf[/I]

ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:4C:69:6E:75:79  
          inet6 addr: fe80::24c:69ff:fe6e:7579/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:11 dropped:0 overruns:0 frame:0
          TX packets:32 errors:4 dropped:0 overruns:0 carrier:10
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:5275 (5.1 KiB)
          Interrupt:11 Base address:0x1800 

route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
169.254.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     1000   0        0 eth0

cat /etc/resolv.conf
cat: /etc/resolv.conf: No such file or directory

The Deli Chef

---

### Post by delichef on 2007-06-16
[I]Quote:
ping -c3 192.168.1.1
ping -c3 216.239.51.104
[/I]
ping 192.168.1.2
PING 192.168.1.2 (192.168.1.2) 56(84) bytes of data.
64 bytes from 192.168.1.2: icmp_seq=1 ttl=64 time=0.133 ms
64 bytes from 192.168.1.2: icmp_seq=2 ttl=64 time=0.111 ms

--- 192.168.1.2 ping statistics ---
9 packets transmitted, 9 received, 0% packet loss, time 7998ms
rtt min/avg/max/mdev = 0.111/0.115/0.133/0.015 ms

The Deli Chef

---

### Post by ajlewis2 on 2007-06-23
Ok, the Ethernet HowTo ([http://tldp.org/HOWTO/Ethernet-HOWTO-4.html](http://tldp.org/HOWTO/Ethernet-HOWTO-4.html))  says:

"Xircom CBE-100
Status: Supported, Driver Name: xircom_tulip_cb
A tulip-like implementation on CardBus. "

The problem is that this driver is not included with the generic kernel in the xubuntu feisty alternate install.  

Since we have kernels from the same kernel source, we could try just dropping my module into your system and see if you can use it.  If it works, I would then suggest that you install the regular 386 kernel.  The reason for that is that when your system gets upgraded and a new kernel is installed, it will wipe out this little module.  If you get the regular 386 kernel, then that module will be in it.

The simplest solution is probably to get a pcmcia card that is supported with the generic kernel, and chili555 would be in a better position to recommend one, I think.

delichef, I think you have my email address if you want me to send the module to try.

---

### Post by ajlewis2 on 2007-06-27
On the chance that my xircom_tulip_cb module from 2.6.20-15-386 would work on delichef's 2.6.20-15-generic system, I sent the module to him.  He put it in the /lib/modules/2.6.20-15-generic/kernel/drivers/net/tulip/ directory and ran depmod.  He then removed the tulip module and ran:
 sudo modprobe xircom-tulip-cb

Unfortunately it did not load.  The error was:
---
 FATAL: Error inserting xircom_tulip_cb
 (/lib/modules/2.6.20-15-generic/kernel/drivers/net/tulip/xircom_tulip_cb.ko):
 
 Invalid module format
---

Apparently there is too much difference between the generic and the 386 kernels; so a module
compiled for the 386 kernel will not work with the generic one even though they are from the same source code.

The choices as I see it are:

1. Install the 2.6.20-15-386 kernel.
2. Find another distro that does have the module
3. Get a different pcmcia network card

I cannot guarantee that 1 or 2 will solve it, because I don't know forsure that this is the module although everything I read does say that it is.  

I don't know what new card to recommend, because I don't have one, but it would be easy enough to find out.

I realize that delichef cannot install the 386 kernel using synaptic over the internet, because he can't connect to the internet from that machine.  I think the package could be downloaded on another system and then installed using dpkg. 

As I recall, there are limitations on what distro can be installed and that the LiveCDs failed.  It seems to me that another pcmcia card would be the easiest solution if that is possible.  

Thoughts?

Anita

---

### Post by delichef on 2007-06-28
Hi Anita:
I copied the file to my desktop and then ran the command below, which
resulted in the following error message after your quote.

Quote:
> After you get this, you will need to transfer it over to the laptop and
> then run:
>
> sudo dpkg -i linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb

sudo dpkg -i linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb
Password:
dpkg: error processing linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb
(--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb

Something additional. I double clicked the "package?" on my desktop
and it started an install. Was this something I should/should not have
done? Anyway just out of curiosity I tried to get online and it still
did not work. So I guess I'm awaiting further instructions.
Thanks
The Deli Chef

---

### Post by ajlewis2 on 2007-06-28
Ok, as I wrote in my email reply, check in /boot to see if the new kernel is there.  If it is not, then use the 'cd' command to go to the directory where you put that package. For example if it is on your Desktop, do:

cd ~/Desktop

Then run the command again:

sudo dpkg -i linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb

Anita

---

### Post by ajlewis2 on 2007-06-28
For background information, I gave delichef instructions for installing the 386 kernel since it must be downloaded from another machine:
-------------------------
The download should begin if you go to this address, [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb)

It is 23Mb.  If it doesn't begin, then you will need to go to [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/) and
then locate linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb

You may have to right click and do "Save As" depending on how your browser works.

After you get this, you will need to transfer it over to the laptop and then run:

```
sudo dpkg -i linux-image-2.6.20-16-386_2.6.20-16.29_i386.deb
```

That should install it.  It would be nice if it also configures grub for you.  You will need to check that.

```

cd /boot
ls

```

You should see the new kernel there.  I had you get 2.6.20-16, because it is a security update and you would need to get it later anyway.  I'm sure that the install will put it there.  You can also do:

```
ls /lib/modules
```

And there you should see a new directory for the new kernel modules.

Ok, now to check grub:

```
cd grub
grep 2.6.20-16 menu.lst 
```

(that is an "ell" and not a "one".)

If you see a line with this in it, then grub is configured and you can reboot.  Let me know if it is there or not, because it will be good information for me when I suggest this to the next person.  :-)  If you do not, then you will need to add it.  The easiest way to do that is:

```
sudo update-grub
```

That will look for all your vmlinuz (kernels) and make a grub menu.lst for them.  I think it will put the newest kernel first in line.  If not, then when you see the list in the menu, you will have to choose the right one.  Don't remove the old kernel yet, because you have to be sure this one boots.

After you **reboot** do:

```
lsmod |grep tulip
```

If you have the plain tulip module and not the xircom_tulip_cb loaded, then you will need to remove the tulip first:

```
sudo modprobe -r tulip
```

And then load the other:

```
sudo modprobe xircom-tulip-cb
```

After you get this far, we can fix this so that it loads the right
module automatically.
------------------------
Anita

---

### Post by chili555 on 2007-06-28
Anita and DC-

I will be anxiously awaiting the outcome. Two of my split personalities thinks this will not fix the EEPROM; three of them do. We are looking forward to a favorable result.

---

### Post by delichef on 2007-06-29
Anita:
Here are the outputs of the commands you gave me

>cd /boot
> ls
abi-2.6.20-15-generic     grub                          System.map-2.6.20-15-generic
abi-2.6.20-16-386         initrd.img-2.6.20-15-generic  System.map-2.6.20-16-386
config-2.6.20-15-generic  initrd.img-2.6.20-16-386      vmlinuz-2.6.20-15-generic
config-2.6.20-16-386      memtest86+.bin                vmlinuz-2.6.20-16-386

>ls /lib/modules
2.6.20-15-generic  2.6.20-16-386

>cd grub
> grep 2.6.20-16 menu.lst
title           Ubuntu, kernel 2.6.20-16-386
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=2757faa0-39eb-4189-b875-d917177c3d08 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-386
title           Ubuntu, kernel 2.6.20-16-386 (recovery mode)
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=2757faa0-39eb-4189-b875-d917177c3d08 ro single
initrd          /boot/initrd.img-2.6.20-16-386

>sudo update-grub
Password:
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.20-16-386
Found kernel: /boot/vmlinuz-2.6.20-15-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

>lsmod |grep tulip
tulip                  52000  0 

>sudo modprobe xircom-tulip-cb
Password:

The only problem I noticed was that I missed one of your commands >sudo modprobe -r tulip

So I entered it and received no output other than allan@ubuntu:/$

I then re-entered sudo modprobe xircom-tulip-cb and got back
 allan@ubuntu:/$

Happy Canada Day for 1 July
The Deli Chef

---

### Post by ajlewis2 on 2007-06-29
Hi DeliChef.

This looks good.  The first few commands show you that the new kernel is in place.  The 'grep' command on menu.lst shows you that there are actually 2 entries for the new kernel in the grub menu.lst.  You ran 'update-grub' anyway, but it should still be ok.  (Notice that I said to run that command if you did not see any output from the command?)

Everything looks good as far as removing the tulip module and adding the xircom_tulip_cb.

To make this work each time you reboot you need to edit two files:

```
sudo nano /etc/modprobe.d/blacklist

```
That will open up the first file in the editor.  Add this line to it:

blacklist tulip

Then do Ctrl X and type Y for yes to save the file.

Then edit another file
```
sudo nano /etc/modules
```

Add a line at the bottom:

xircom-tulip-cb

Again do Ctrl X and type Y and hit ENTER to save. 

These two edits will make it so that tulip does not load and xircom-tulip-cb does load when you reboot.  So after the edits reboot.  Then do:

```
lsmod | grep tulip
```

You should see the xircom-tulip-cb module loaded.  If you do, then see if your network is working.

---

### Post by delichef on 2007-06-29
Hi Anita:
No net connection, received a "Server Not Found" when I looked for the Google page.

For your last command
>lsmod | grep tulip

I received:
tulip                  52000   0

Your command requests:

>blacklist tulip
Then do Ctrl X and type Y for yes to save the file.

and

xircom-tulip-cb
Again do Ctrl X and type Y and hit ENTER to save

Gave me a screen I was unsure of. I did enter the commands and saved.

Does this mean I should invest in a newer pcmcia card for this Tecra 8000?

The Deli Chef

---

### Post by ajlewis2 on 2007-06-29
> **delichef said:**
> Hi Anita:
For your last command
>lsmod | grep tulip

I received:
tulip                  52000   0

Your command requests:

>blacklist tulip
Then do Ctrl X and type Y for yes to save the file.

and

xircom-tulip-cb
Again do Ctrl X and type Y and hit ENTER to save

Gave me a screen I was unsure of. I did enter the commands and saved.

Does this mean I should invest in a newer pcmcia card for this Tecra 8000?

The Deli Chef

The module is not loaded.  You should have received "xircom-tulip-cb" instead of "tulip".

You *did* **reboot**, right?!

If you did reboot, then see if the files got the lines put in them:

```
grep tulip /etc/modprobe.d/blacklist
```

You should see:

**blacklist tulip**

Then try:
```
grep tulip /etc/modules
```

You should see:

**xircom-tulip-cb**

If you don't see those, then do the edit again.

When you edit those two files you need to first type in what I indicated.  Then do Ctrl X.  Then type a Y and then hit Enter.  You should not get a screen after that.  You should be back at a command prompt ready for your next command. I wonder if you actually got those two files edited. I am trying to figure out what the screen that you were unsure of looked like.  Both edits should have worked exactly the same way.

---

### Post by delichef on 2007-06-29
Hi:
Yes I did reboot after editing the files.

After entering your commands, I did receive the code you mentioned
The only line that has me wondering is "# replaced by tulip" Should I have received this line? If tulip is blacklisted, should it be replaced by tulip?

See:
grep tulip /etc/modprobe.d/blacklist
#blacklist tulip
# replaced by tulip
allan@ubuntu:/$ grep tulip /etc/modules
#xircom-tulip-cb 

Still no net connection. My settings are still:
Wired connection Address: dhcp 
Property Configuration: Automatic config (DHCP) and box is checked
Nothing in the fields for: IP address, Subnet Mask or Gateway address
Thanks
The Deli Chef

---

### Post by ajlewis2 on 2007-06-29
DeliChef, those "#" marks mean that those lines are commented out.  Did you put the "#" in there when you edited?  If not, then your edits did not get saved.

> grep tulip /etc/modprobe.d/blacklist
#blacklist tulip
# replaced by tulip
allan@ubuntu:/$ grep tulip /etc/modules
#xircom-tulip-cb


So, you need to edit those again.  

This time you will simply remove the "#" mark at the beginning of those lines.  The editor is called nano.  You must use sudo, because you have to do this as administrator.  The files are not in your user directory.  So the command is 'sudo' followed by 'nano' followed by the filename.  

The first file is in /etc/modprobe.d. It is called "blacklist"; so the command is:

**sudo nano /etc/modprobe.d/blacklist**

Now you must find the line.  At the bottom you will see the commands.  The one you want is "Where Is" which is "Ctrl-W".  Then type in "blacklist tulip" without the quotes and hit ENTER.  This will take you to that line.  Place the cursor on the "#" and press the Delete key.  Then do "Ctrl-X".  Then type "y". Then press the "ENTER" key.  

When you do "grep tulip /etc/modprobe.d/blacklist" again, the "#" should be missing from that line saying "blacklist tulip".  That means it is no longer commented out and it will now work. **Do not edit the line "# replaced by tulip", because that is supposed to be a comment**

Do the same process with the /etc/modules file and remove that "#" from before the "xircom-tulip-cb" line.  I think you wrote that in there, because that line would not have been there by itself.  So I'm pretty sure you did edit and save the file. Did you put that comment mark in those lines?  Otherwise the system did that on its own and I have never seen that done before.

The only reason I can think of that the system would have commented those out would be that it is not using the new kernel.  Do:

**uname -r**

You should see: 2.6.20-16-386

Anita

---

### Post by delichef on 2007-06-30
Hi:
I removed the comment mark from the suggested lines.

It was the nano screen that had me confused in my previous comments. Anyway I removed, saved and exited nano on both "blacklist tulip" and "xircom-tulip-cb"

When the command uname -r was entered I did receive 2.6.20-16-386

I then rebooted and tried my net connection. No joy.

I did not add the # to any lines that I'm aware of, so I'm not sure how it got there.

I know one thing though, your giving me a workout with these terminal commands :D

One other question. Every time I reboot the following programs always load.

My Name - File Manager
Terminal
Open Office

How to I prevent them from loading?
Thanks
The Deli Chef

---

### Post by ajlewis2 on 2007-06-30
Those programs may be open because you have left them open when you rebooted.  XFCE will open up whatever is left open when you shutdown.  If you are not leaving them open, then check in Settings in your Menu.  There is something about Autostarted Programs there.

Regarding the network do the following:

**lsmod |grep tulip**

That will tell you if the right module is now loaded.

**ifconfig**

That will show you if you have an interface for the network.

Then go to the Menu under System or wherever it was that you previously tried to set up the network.  There should be a Wired listing.  It should be checked.  Go to the Properties and tell us what you have in the blocks.  Try setting it to dhcp and save it to see if you connect.

If you do not connect to the internet now, do you know for sure what the IP address of your router is?  Please check on what it is, because just checking with a browser on the Internet doesn't tell the whole story.  We need to see if there is a simple connection to the router itself,

Anita

---

### Post by persistentstubborn on 2007-06-30
Dialup modem configuration problem PAP-CHAP scripts Festy Fawn 7.04

Hi,

Standalone computer uses 56 L SWEEX hardware external modem - no driver should be required, and I use none.

Modem is recognised on ttyS1, but can'd dial to the ISP.

I edited etc/ppp/options and #commented ABORT "NO DIALTONE" and "NO DIAL TONE" sometimes during various attempts. I also made verious other attempts, but yet no results. Below are plog results during the attempts.

Jun 30 11:56:38 lazar-desktop chat[10951]: SIGTERM
Jun 30 11:56:38 lazar-desktop pppd[10932]: Connect script failed
Jun 30 11:56:39 lazar-desktop pppd[10932]: Exit.
lazar@lazar-desktop:~$ pico /etc/chatscripts/pap
lazar@lazar-desktop:~$ sudo pico /etc/chatscripts/pap
Password:
lazar@lazar-desktop:~$ 
plog
Jun 30 12:05:04 lazar-desktop chat[11377]:  -- got it 
Jun 30 12:05:04 lazar-desktop chat[11377]: send (ATDP042500500^M)
Jun 30 12:05:04 lazar-desktop chat[11377]: timeout set to 75 seconds
Jun 30 12:05:04 lazar-desktop chat[11377]: expect (CONNECT)
Jun 30 12:05:04 lazar-desktop chat[11377]: ^M
Jun 30 12:05:05 lazar-desktop chat[11377]: SIGTERM
Jun 30 12:05:05 lazar-desktop pppd[11357]: Connect script failed
Jun 30 12:05:06 lazar-desktop pppd[11357]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:28:30 lazar-desktop chat[12293]:  -- got it 
Jun 30 12:28:30 lazar-desktop chat[12293]: send (ATDP042500500^M)
Jun 30 12:28:30 lazar-desktop chat[12293]: timeout set to 75 seconds
Jun 30 12:28:30 lazar-desktop chat[12293]: expect (CONNECT)
Jun 30 12:28:30 lazar-desktop chat[12293]: ^M
Jun 30 12:28:30 lazar-desktop chat[12293]: SIGTERM
Jun 30 12:28:30 lazar-desktop pppd[12273]: Connect script failed
Jun 30 12:28:31 lazar-desktop pppd[12273]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:35:16 lazar-desktop chat[12647]: timeout set to 75 seconds
Jun 30 12:35:16 lazar-desktop chat[12647]: expect (CONNECT)
Jun 30 12:35:16 lazar-desktop chat[12647]: ^M
Jun 30 12:35:16 lazar-desktop chat[12647]: ^MATX3^MA^M
Jun 30 12:35:16 lazar-desktop chat[12647]: OK^M
Jun 30 12:35:16 lazar-desktop chat[12647]: SIGTERM
Jun 30 12:35:16 lazar-desktop pppd[12627]: Connect script failed
Jun 30 12:35:17 lazar-desktop pppd[12627]: Exit.
lazar@lazar-desktop:~$ plog
Jun 30 12:37:41 lazar-desktop chat[12807]:  -- got it 
Jun 30 12:37:41 lazar-desktop chat[12807]: send (ATDP042500500^M)
Jun 30 12:37:41 lazar-desktop chat[12807]: timeout set to 75 seconds
Jun 30 12:37:41 lazar-desktop chat[12807]: expect (CONNECT)
Jun 30 12:37:41 lazar-desktop chat[12807]: ^M
Jun 30 12:37:42 lazar-desktop chat[12807]: SIGTERM
Jun 30 12:37:42 lazar-desktop pppd[12787]: Connect script failed
Jun 30 12:37:43 lazar-desktop pppd[12787]: Exit.
lazar@lazar-desktop:~$ plog
Jun 30 12:38:39 lazar-desktop chat[12985]:  -- got it 
Jun 30 12:38:39 lazar-desktop chat[12985]: send (ATDT042500500^M)
Jun 30 12:38:39 lazar-desktop chat[12985]: timeout set to 75 seconds
Jun 30 12:38:39 lazar-desktop chat[12985]: expect (CONNECT)
Jun 30 12:38:39 lazar-desktop chat[12985]: ^M
Jun 30 12:38:40 lazar-desktop chat[12985]: SIGTERM
Jun 30 12:38:40 lazar-desktop pppd[12965]: Connect script failed
Jun 30 12:38:41 lazar-desktop pppd[12965]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:40:03 lazar-desktop chat[13156]: timeout set to 75 seconds
Jun 30 12:40:03 lazar-desktop chat[13156]: expect (CONNECT)
Jun 30 12:40:03 lazar-desktop chat[13156]: ^M
Jun 30 12:40:03 lazar-desktop chat[13156]: ^MATX3^MA^M
Jun 30 12:40:03 lazar-desktop chat[13156]: OK^M
Jun 30 12:40:03 lazar-desktop chat[13156]: SIGTERM
Jun 30 12:40:03 lazar-desktop pppd[13136]: Connect script failed
Jun 30 12:40:04 lazar-desktop pppd[13136]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:40:03 lazar-desktop chat[13156]: timeout set to 75 seconds
Jun 30 12:40:03 lazar-desktop chat[13156]: expect (CONNECT)
Jun 30 12:40:03 lazar-desktop chat[13156]: ^M
Jun 30 12:40:03 lazar-desktop chat[13156]: ^MATX3^MA^M
Jun 30 12:40:03 lazar-desktop chat[13156]: OK^M
Jun 30 12:40:03 lazar-desktop chat[13156]: SIGTERM
Jun 30 12:40:03 lazar-desktop pppd[13136]: Connect script failed
Jun 30 12:40:04 lazar-desktop pppd[13136]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:45:29 lazar-desktop chat[13441]:  -- got it 
Jun 30 12:45:29 lazar-desktop chat[13441]: send (ATDT042500500^M)
Jun 30 12:45:29 lazar-desktop chat[13441]: timeout set to 75 seconds
Jun 30 12:45:29 lazar-desktop chat[13441]: expect (CONNECT)
Jun 30 12:45:29 lazar-desktop chat[13441]: ^M
Jun 30 12:45:30 lazar-desktop chat[13441]: SIGTERM
Jun 30 12:45:30 lazar-desktop pppd[13421]: Connect script failed
Jun 30 12:45:31 lazar-desktop pppd[13421]: Exit.
lazar@lazar-desktop:~$ 
plog
Jun 30 12:50:33 lazar-desktop chat[13680]:  -- got it 
Jun 30 12:50:33 lazar-desktop chat[13680]: send (ATDT042500500^M)
Jun 30 12:50:33 lazar-desktop chat[13680]: timeout set to 75 seconds
Jun 30 12:50:33 lazar-desktop chat[13680]: expect (CONNECT)
Jun 30 12:50:33 lazar-desktop chat[13680]: ^M
Jun 30 12:50:34 lazar-desktop chat[13680]: SIGTERM
Jun 30 12:50:34 lazar-desktop pppd[13658]: Connect script failed
Jun 30 12:50:35 lazar-desktop pppd[13658]: Exit.
lazar@lazar-desktop:~$ 


Any suggestion is appreciated.

Regards

---

### Post by chili555 on 2007-06-30
persistant-

I suggest starting a new thread and better describe your issue. I'd title it: *Dialup modem configuration problem PAP-CHAP scripts Festy Fawn 7.04*. I think you will have a much better chance of finding help.

---

### Post by delichef on 2007-06-30
I'm not sure what is going here, but I no longer have a selection for "Wired and DHCP" The only choice I now have is "Modem Connection" Everything was OK when I shut down last night. I have no idea why this happened?

Output of command requests.

lsmod |grep tulip
xircom_tulip_cb        18608  0 


 ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

>Those programs may be open because you have left them open when you rebooted. XFCE will open up whatever is left open when you shutdown. If you are not leaving them open, then check in Settings in your Menu. There is something about Autostarted Programs there.

No items in Autostarted Programs other than Restricted Drivers and Print Queue, and I keep closing OpenOffice. But this is minor compared to not getting on the net.

Thanks
The Deli Chef

---

### Post by ajlewis2 on 2007-06-30
What that means is that the xircom_tulip_cb module is not working. I think we are not going to get this card going.  Since you have a new kernel, you might as well try setting things back and reboot.  I doubt things will be better than they were with the previous kernel, but this is definitely not working. Basically you will need to take out those two lines that you added and then reboot.  Then run iwconfig:

**sudo nano /etc/modprobe.d/blacklist**

Remove the line with 'blacklist tulip' and save the file.

**sudo nano /etc/modules**

Remove the line with 'xircom-tulip-cb' and save the file.

The easy way to remove the line is to use the arrows to go to the line and with the cursor on the line, do Ctrl-k.  That will cut the line.  Then save the file with Ctrl-X as you did before.

Then reboot and check your network configuration again to see if the Wired is back. If it is, you can try to configure it again with dhcp, but I have run out of ideas.  Maybe chili555 can recommend a pcmcia adapter for network. 

Anita

---

### Post by delichef on 2007-06-30
Hi Anita:
Yes. Wired Connection is back, but no connection.

BTW what did you mean by:

>*If you do not connect to the internet now, do you know for sure what the IP address of your router is? Please >check on what it is, because just checking with a browser on the Internet doesn't tell the whole story. **>We need to see if there is a simple connection to the router itself,***

What other way do I check my router other than via a web browser?

Thanks
The Deli Chef

---

### Post by ajlewis2 on 2007-07-01
When you set up a router, it gets an IP address. That is a series of 4 sections of numbers separated by dots.  The router then can be connected to other computers.  It can also be connected to the Internet and through that to other computers.

When you say that you are checking with the browser, I assume you are putting in a name like google.com and seeing if you connect. That connection involves several connections.  When you connect directly to the router, you actually can do that with a browser as well.  That is usually the way you go to the router to make changes etc.  Is that what you are doing? 

What we were trying to do in the beginning was to ping the router.  That is about the most direct test to see if the computer is connected.  It just checks if the two are connected.  When you were doing the ping, I noticed that the number you used was the number that I had asked you to give the computer itself and so I knew it was not the router's IP address.  So I wondered if you actually knew the IP address of the router.  It is possible that you simply put a cd in and set up the router when you got it without ever really knowing what IP address the router has.  In that case, pinging won't work.  You have to ping the actual IP address that the router has.

Your instruction manual for the router should tell you how to find out what its IP address is.

BTW, have you used that card with any other machine or operating system?  I forget if you told us already.

Anita

---

