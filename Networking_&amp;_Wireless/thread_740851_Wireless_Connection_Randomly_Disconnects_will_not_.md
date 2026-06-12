---
title: "Wireless Connection Randomly Disconnects will not Reconnect"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by captain_bogus on 2008-03-31
Hi,

I recently got an Asus G1 laptop with a Realtek RTL8168/811 Family PCI-E Gigabit Ethernet NIC (NIDS 6.0).  It came with Vista.  I right away set it up to dual boot with Ubuntu 7.10.  I use Ubuntu for websurfing and playing World of Warcraft.  Not sure why I keep the Vista partition.

Anyway, when I am websurfing, sometimes, randomly, the wireless internet connections cuts off.  I'll try to reconnect by clicking on the network icon at the top right of the screen but it refuses to reconnect and eventually times out giving up.  The only way I've found to reestablish a network connection is to reboot.

Thankfully, it doesn't happen while playing WoW.  Only when websurfing.  Also, it does not happen when I'm on my Vista partition.

After I first installed Ubuntu, I just clicked on the network icon, told it what kind of encryption my network uses, typed in my network shared key, and it worked.  No problems.

I run a simple out-of-the-box Ubuntu 7.10.  The only thing I had to do was install the Nvidia driver.  For that I used Envy.  I keep up with updates whenever they come out.  Not sure what I'm doing wrong.

I have a Linksys wireless router.  When I discovered this problem I updated it's firmware, but that didn't help.

This probem did not occur with my old Toshiba laptop which I also dual booted (XP/Ubuntu) using the same wireless router.

I hope I've given enough information to get some help.

Thanks,
bogus

---

### Post by captain_bogus on 2008-04-01
Ok, I suppose I didn't give enough information, much less the correct information.  How about this:

```

~$lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:59:6a:14
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:3c:25:d5
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl4965 ip=192.168.1.107 latency=0 module=iwl4965 multicast=yes wireless=IEEE 802.11g

~$sudo dhclient wlan0
[sudo] password for XXXXXXXX:
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wlan0/00:13:e8:3c:25:d5
Sending on   LPF/wlan0/00:13:e8:3c:25:d5
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.107 -- renewal in 34203 seconds.

~$ sudo dhclient wmaster0
There is already a pid file /var/run/dhclient.pid with pid 6705
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Sending on   Socket/fallback
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```


I read in one post here that sometimes installing Ndisrapper just makes things worse, and in another one post I read that installing Ndiswrapper fixes everything.  Should I try NDISwrapper?

Please help.

---

### Post by captain_bogus on 2008-04-02
Wow, two days and no reply.

I tried something on a lark, just to see what would happen.  I burned a Mandrake LiveCD and ran it.  I've been websurfing on it for over 2 hours and no disconnect.  What's the difference?  I don't want to switch away from Ubuntu, heck I've been using it happiliy on my Toshiba laptop since May of 2006.  See my join date. ^^^^

Someone please reply.

---

### Post by captain_bogus on 2008-04-04
Ok, well Mandriva does the same thing.  Last night I was surfing and the connection dropped out  No big surprise there.  That's fine with me because I didn't really like Mandriva, I like Ubuntu better.  I guess I'm just out of luck.  I'll try Ndiswrapper and if that doesn't work I guess I'll just have to go back to Vista for a while.  Maybe in the future some programmer will figure it out and I can come back to Ubuntu.  I can't live with my internet randomly dropping out on me an having to reboot all the time to get it back.

---

### Post by jcr1 on 2008-04-07
Hi,

I have the same problem. It just stops working sometimes and I can't (read don't know how to) get it back. When I click on the network icon at the top, it drops a list of available networks, but obviously there's only one I want to connect to and it says its connected to it.

What I am thinking and looking for is the equivilent of "repair" on XP...i.e. if something is iffy with the network connection you can right click on the icon in the taskbar and press 'repair' and it seems to disconnect, disable...enable, reconnect, etc"...a nice feeling of just turning it off and back on.

How would I do this in Ubuntu? 

Also..any ideas what would make it drop off? It would be nice to find out why it is happening in the first place...router problem, telephone line problem, computer problem (hardware / software)...

Cheers,

Jon

---

### Post by captain_bogus on 2008-04-07
Since I don't have this problem on the same computer and same router while running Vista, I *think* it's a Linux driver issue.  I also do not have the problem on my Toshiba laptop using the same router.  Everything else being eliminated, it must be the Linux driver for my Asus's wireless hardware.

I also think running the commands:

```
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up

```

will reset the wireless connection without having to reboot.

I went ahead and installed Ndiswrapper and the problem seems to have gone away. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I wanted to wait a few more days before I tagged this post with [SOLVED].

---

### Post by captain_bogus on 2008-04-08
Well, my fix didn't work.  Last night while surfing it disconnected.  I didn't have to reboot though.  The code above, ifconfig wlan0 up/down then then click on Network Manager icon, then click on my wireless network's name did the trick.  There is a good chance I did not install the ndiswrapper correctly.  I'm not sure how to trouble shoot that part yet.  I guess I'll get back to researching it.

---

### Post by jcr1 on 2008-04-09
is it wlan on all computers? I am sure fiddling around, someone told me that my computer was recognising the wireless connection as eth1 (or eth0)

---

### Post by captain_bogus on 2008-04-09
If you type "ifconfig" in your terminal, you'll get some output like this.

```
user@compy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1D:60:59:6A:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:13:E8:3C:25:D5  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:e8ff:fe3c:25d5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10336 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6683 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10921406 (10.4 MB)  TX bytes:1144795 (1.0 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-3C-25-D5-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


```

See how my eth0 has nothing but zeros on it, but my wlan0 has an inet address, a Bcast number and stuff.  Well, that means my wlan0 is working (at the moment).  You can do the same thing and see which of your network devices is working.  If it's your eth0, then you would type "sudo ifconfig eth0 down" and "sudo ifconfig eth0 up" to reset it.  Good luck.

---

### Post by jcr1 on 2008-04-10
I do not get a wlan. I get eth0, eth1 and lo

eth1 appears to be my wlan connection. eth0 has nothing on it, so i guess thats my unused ethernet socket.

---

