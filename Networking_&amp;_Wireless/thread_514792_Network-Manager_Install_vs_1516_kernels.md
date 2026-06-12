---
title: "Network-Manager Install vs 15/16 kernels"
date: 2007-08-01
forum: Networking &amp; Wireless
---

### Post by BC7333 on 2007-08-01
Newbie, so bear with me.

Following setup

Flybook V5

Realtek RTL8111/8168B Express Gigabit Ethernet controller
Intel pro wireless 3945ABG WLAN

Installed Feisty with .15 kernel that upgraded to .16 after install.  No install issues.

Have been dickering for days and days unsuccessfully trying to set up Network manager to work with wireless or wired.

Tried WICD and was able to use wireless but not wired so thought I would try from scratch.

Dumped all network managers, WICD, NDIS etc and reinstalled gnetwork-manager via synaptec.

Rebooted, tried to configure wired/wireless and just would not work.

Then decided to try the .15 kernel...  - that's when the fun started...

When configuring I could now see the 'attempting to connect' thingie in the task tray working..
I could see my router SSID in config..  and finally COULD CONNECT AND SURF WIRELESS!!

Then rebooted with the .16 kernel and wireless worked!

Somehow configuring with .15 'sticks'.. but .16 does not.

Strange strange...

Am still trying to get wired working..  anyone have any tricks up their sleeve?

Thanks all.

Cheers!

---

### Post by BC7333 on 2007-08-01
Did a couple more kernel switching and finally wired network and wireless seem to work ok.

Don't ask me how.. would have needed a keylogger for that..

Only condition seems to be that when I want to use wireless I have to boot with wireless turned on.  When I need wired, boot with wireless turned off.

Before I start messing around again, is there any way I can save the current configuration? Which files/configs should I *_backup ?

Will add some ls's to this post in a bit.

Another quirky thing I found is that if I turn wireless on **after** booting, until a solid connection exists the mouse gets really really jumpy.. going all over the place and opening programs etc whenever I move it.. could this possibly have to do with this network card somehow using mouse memory space while searching for networks?  Read something about this network card trying to use 16k stacks and ubuntu allowing only 8k..  Related maybe? [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

Will try to add some config info below in a little while for those that are interested.

---

### Post by BC7333 on 2007-08-03
Still don't know how I did it, but both Wireless and Wired work great now.  Do need to completely shutdown to change though.

What configs / ls* can I post here to help me backup this configuration and maybe identify what is really going on inside and what other improvements can be made?

---

### Post by BC7333 on 2007-08-03
**Wired**

> brian@brian-flybook:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:09:5D:15:60:23  
          inet addr:192.168.1.116  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2156 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1787 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1367667 (1.3 MiB)  TX bytes:299890 (292.8 KiB)
          Interrupt:16 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:200 (200.0 b)  TX bytes:200 (200.0 b)


> brian@brian-flybook:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

> 
brian@brian-flybook:~$ sudo lshw -C network
Password:
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:09:5d:15:60:23
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.116 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: ioport:3000-30ff iomemory:f4000000-f4000fff irq:16
  *-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945 latency=0
       resources: iomemory:f4100000-f4100fff irq:18

---

### Post by BC7333 on 2007-08-03
**Wireless**

> brian@brian-flybook:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:D2:BB:50:59  
          inet addr:192.168.1.119  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1207 errors:4 dropped:78 overruns:0 frame:0
          TX packets:1119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:920223 (898.6 KiB)  TX bytes:188230 (183.8 KiB)
          Interrupt:18 Base address:0xe000 Memory:f4100000-f4100fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3468 (3.3 KiB)  TX bytes:3468 (3.3 KiB)

> brian@brian-flybook:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1

> brian@brian-flybook:~$ sudo lshw -C network
Password:
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:09:5d:15:60:23
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.1.116 latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:3000-30ff iomemory:f4000000-f4000fff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: eth1
       version: 02
       serial: 00:19:d2:bb:50:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f4100000-f4100fff irq:18

---

### Post by BC7333 on 2007-08-03
Each time I want to switch from wired to wireless I have to completely shut down, goto manual config and select the named network profile in network manager.

Can anyone detect any misconfiguration with the above?

Am using static ip's with gateway at 192.168.1.1

No security, just using MAC address restrictions on the router.

Maybe I should be using the same static IP address for both wired / wireless modes?

Any other printouts I can post that would help me finalize configuration so that it works seamlessly?

Thanks!

---

### Post by walkerk on 2007-08-03
not sure what your issue is but does this work in place of rebooting?
```
sudo /etc/init.d/networking restart
```

---

### Post by BC7333 on 2007-08-03
Walkerk,
Thanks for the reply.

The command you gave seemed to have no effect.  Running wireless at the time invoked.

The issue is that I would first like to backup the current configuration in case I fiddle around too much and loose it. Second I am interested in understanding more about how network manager works (or should work) so I can debug when travelling and have difficulty connecting at hotels and other offices.   IThird I will likely have to set up a few more of these laptops so need to know how I can replicate when I really don't know how I even got this one setup and working :)  Last, I want to be able to switch without having to fiddle.

Kinda afraid at the moment to try dhcp until I know more.

Again thanks for the assist.

Brian

BTW Gruesse!  Deutsch geht auch aber vielleicht besser englisch hier!  War in TR / KL / LB 17 jahren oder so.







> 
brian@brian-flybook:~$ sudo /etc/init.d/networking restart
Password:
 * Reconfiguring network interfaces...                                          eth2: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth2.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth2: ERROR while getting interface flags: No such device
eth2: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth2.
ath0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.ath0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
ath0: ERROR while getting interface flags: No such device
ath0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up ath0.
wlan0: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0.

---

### Post by walkerk on 2007-08-03
I see that your wireless is assigned the name 'eth1'.. does it always do that? you can assign names using iftab..

```
gksudo gedit /etc/iftab
```

this is mine. eth0 is wired and wlan0 is obviously wireless..
```
eth0 mac 00:15:c5:ba:f2:2c arp 1
wlan0 mac 00:16:cf:80:c5:c0 arp 1
```

are you using Network Manager or Wicd?

The reason I asked is because mine used to jump back and forth from eth1 to wlan0. I had WICD looking for eth1 so when my nic registered as wlan0 I didn't have wireless. (I had to change it in WICD).. just an idea..

---

### Post by BC7333 on 2007-08-03
> **walkerk said:**
> I see that your wireless is assigned the name 'eth1'.. does it always do that? you can assign names using iftab..

Yes, seems wireless is eth1 and wired eth0

> are you using Network Manager or Wicd?

The reason I asked is because mine used to jump back and forth from eth1 to wlan0. I had WICD looking for eth1 so when my nic registered as wlan0 I didn't have wireless. (I had to change it in WICD).. just an idea..

Before I  did what I did as described in the original post, I used WICD for wireless but could not get wired to work. Now using a clean Network-manager.


> # This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:09:5d:15:60:23 arp 1

This was what I got with gedit.  This mac address looks like the wired.  Associated wireless shows up as another in my router. Should I try to follow your example and get both cards listed?

BTW I did uninstall WICD, and reinstalled Network-manager.  Maybe this left some config artifacts..

---

### Post by BC7333 on 2007-08-03
Edited, rebooted and no big change.  uninstalled, rebooted, installed network manager with synaptic.  deleted previous configurations with the gui and reconfigured.
> 
brian@brian-flybook:~$ sudo lshw -C network
Password:
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@04:00.0
       logical name: eth0
       version: 01
       serial: 00:09:5d:15:60:23
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.1.116 latency=0 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: ioport:3000-30ff iomemory:f4000000-f4000fff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@06:00.0
       logical name: wlan0
       version: 02
       serial: 00:19:d2:bb:50:59
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.1.119 latency=0 link=yes multicast=yes wireless=IEEE 802.11g
       resources: iomemory:f4100000-f4100fff irq:18


Wireless seems to work ok but haven't been able to get connected wired yet. More later after some testing, but it seems you were onto something with setting the logical names.

---

### Post by walkerk on 2007-08-03
> **BC7333 said:**
> 

BTW I did uninstall WICD, and reinstalled Network-manager.  Maybe this left some config artifacts..

What I did was set both names accordingly with the nic's mac address. Then within the WICD preferences you have to set the wired and wireless interfaces..

Oh and English is better for myself.. Mein Deutsch ist nicht gut.. I'm American living in Germany.. I was in the Military and made a bunch of German friends.. Got a good job here so my family and I stayed.. :)

My wife is actually getting on my case about my declining Duetsch speaking abilities.. Ah well.. Alle ist klar

---

### Post by BC7333 on 2007-08-03
Besides your tips above, I upgraded the kernel using your instructions and seems this also brought some good effects.. Where wireless before was taking quite some time to establish a connection it only takes a few seconds now!

Will keep testing to see what develops..  Might just try WICD again.  A boatload of thanks for all the help so far.

Off topic..

Well well... what a small world... Was stationed at Spangdahlem back in the early 80's and also stayed.  Moved to southern IT 10 years ago to see some sunshine.

If you want, drop me a pm here and we can trade contact info.. after all we are just one Ryanair hop away!

Cost of this new laptop -$3000.. - a new ubuntu friend, priceless!

---

### Post by walkerk on 2007-08-03
> **BC7333 said:**
> Besides your tips above, I upgraded the kernel using your instructions and seems this also brought some good effects.. Where wireless before was taking quite some time to establish a connection it only takes a few seconds now!

Will keep testing to see what develops..  Might just try WICD again.  A boatload of thanks for all the help so far.

Off topic..

Well well... what a small world... Was stationed at Spangdahlem back in the early 80's and also stayed.  Moved to southern IT 10 years ago to see some sunshine.

If you want, drop me a pm here and we can trade contact info.. after all we are just one Ryanair hop away!

Cost of this new laptop -$3000.. - a new ubuntu friend, priceless!

Right on. Small world.

I'm glad the new kernel helps.. :)

---

### Post by BC7333 on 2007-08-03
WICD works just fine.. Can even switch to/from wireless!!!!

Simply WOW!!

I spent exactly one week trying to resolve this.

THANKS! (again and again) LOL!

---

