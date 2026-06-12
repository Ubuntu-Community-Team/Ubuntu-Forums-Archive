---
title: "Strange Hardy wireless problem"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by michael1234 on 2008-07-28
I have an Intel 2200BG internal card. Flawless in XP. Using Ubuntu Hardy (Studio edition), however, has been quite an adventure; I can get on, but only after going through some hoops:

*I power on and log in. Wireless never works at first.
*I get an unencrypted signal from nearby. I used to be able to use that. I saved this configuration as ¨Piggyback.¨ It no longer works.
*I have my WPA-PSK settings saved also. However, switching to the saved configuration doesn´t work for some reason, even though the settings are correct.
*I can always get on by switching to my ¨Piggyback¨ configuration (which doesn´t work any longer and then *manually* changing the wireless signal to my own and *manually* typing in the WPA key. This *always* works.

Weird, huh? I guess I can live with it, but it is annoying. Any suggestions? Here are some details:

I copied the terminal output of the dhclient to gedit to paste here since I was disconnected:

```
michael@ubuntustudio:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 18226
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:74:e6:7c
Sending on   LPF/eth1/00:0e:35:74:e6:7c
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on eth1 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.101 on eth1 to 255.255.255.255 port 67
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.101
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.
```

Now that I changed the configuration manually in Network Settings I am fine: 
```
michael@ubuntustudio:~$ sudo dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid 18205
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:0e:35:74:e6:7c
Sending on   LPF/eth1/00:0e:35:74:e6:7c
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.101 on eth1 to 255.255.255.255 port 67
DHCPACK of 192.168.1.101 from 192.168.1.1
bound to 192.168.1.101 -- renewal in 36370 seconds.

```

Any ideas? (It seems I am not the only Hardy user having this kind of problem) I would greatly appreciate it!

---

### Post by michael1234 on 2008-07-28
Oh yeah, one more thing. Network info:

```
michael@ubuntustudio:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 10
       serial: 00:03:25:18:be:3a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:74:e6:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.104 latency=32 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

```

Never had a problem with wired connection. I just about always wireless though.

---

### Post by michael1234 on 2008-07-30
It seems to have gotten worse: network-admin sometimes refuses to recognize my router´s signal, though it´s always there. I have wicd as well, and it seems to get it, but wicd feels a bit buggy.

Part of me just wants to get ndiswrapper and try again, but there shouldn't be any problem with iwconfig alone, because as I mentioned before I can get on, it just takes some jogging of the network-admin settings. Even when my router's signal is not recognized right away, if I revert to saved settings that name my signal it recognizes it!

This is a joy-killer because it's so hard to troubleshoot by looking online, because I'm not online when I have the problem! Any ideas? I'll keep tweaking...

---

### Post by michael1234 on 2008-07-31
I opened network-admin with a watch command and got this:```
michael@ubuntustudio:~$ watch --interval=5 network-admin

(network-admin:5652): Gtk-WARNING **: Unknown property: GtkComboBox.items

(network-admin:5652): GLib-CRITICAL **: g_hash_table_lookup: assertion `hash_table != NULL' failed

```
Perhaps this GLib-CRITICAL failure has something to do with why my wireless is so fritzy?

---

### Post by michael1234 on 2008-08-10
There are even times when I can't get on no matter what, strangely because the network-admin refuses to see my router's signal! At this point, the ipw2200 driver eats up the whole processor looking for it. Reboot and I'm okay (with the manual steps explained previously). Weird.

RELATED: My HDD filesystem mount point is unrecognizable. Currently running Puppy Linux LiveCD to try to fix it. Puppy is great at detecting EVERYTHING -- but for whatever reason, though it always sees my router's signal, it won't connect when I put in the WPA key! Perhaps this is a router firmware problem?

Because of the bad mount point, I am thinking about backing up my stuff and doing a nice, clean format-and-reinstall. I wonder then if the wireless can finally work as it did in Win!

---

### Post by monikersupreme on 2008-08-10
I'm having this same issue with two separate workstations. The first is an HP NC8000 Laptop (PM765, 2GB DDR, 100GB drive) has the same wireless card (Intel 2200BG) and the second is a desktop (Celeron 1.3GHz, 512MB RAM, 80GB drive) with a Gigabyte PCI 802.11b/g wireless card. 

In summary, if I manually configure the card (re-enter in my WPA key) I can connect but I cannot get either workstation to load it's configurations automatically...

After about a week of this issue I'm starting to get a bit jaded w/ Hardy (I'd hate to have to go back to XP but like the OP it seems this issue is getting worse and if I can't resolve it I might have no choice)... there haven't been many charitable responses on the support forum side either...

Any advice would be much appreciated!

---

### Post by monikersupreme on 2008-08-18
Update: I've been able to remedy some of the issues on the desktop by restarting the /etc/init.d/networking script (and creating a script that does the same on boot) but I am still having issues with my laptop saving profiles and, in particular, connecting to unencrypted wireless.

It seems odd that I can connect to my own WPA protected router at home but I cannot get an unencrypted connection while I'm at a coffee shop.

I see there hasn't been much activity on this thread... if anyone out there has a solution or workaround for this it would be much appreciated!

---

### Post by zooterkin on 2008-08-24
I'm getting what looks like the same problem.  Compaq nw8000, with Hardy Heron installed from scratch.

After booting, wifi doesn't work.  Giving the WPA key again through the Network app sometimes gets it running the first time, sometimes it takes several goes.  Haven't managed to get this working after hibernation.

I've just tried running the networking script as suggested above, and the worked the second time after a reboot.

Here's the output from the two runs, in case it's helpful:
```

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 5824
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:85:1b:1b:8c
Sending on   LPF/ath0/00:11:85:1b:1b:8c
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:85:1b:1b:8c
Sending on   LPF/ath0/00:11:85:1b:1b:8c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
                                                                         [ OK ]

```

```

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.ath0.pid with pid 6040
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:85:1b:1b:8c
Sending on   LPF/ath0/00:11:85:1b:1b:8c
Sending on   Socket/fallback
DHCPRELEASE on ath0 to 192.168.0.1 port 67
There is already a pid file /var/run/dhclient.ath0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/ath0/00:11:85:1b:1b:8c
Sending on   LPF/ath0/00:11:85:1b:1b:8c
Sending on   Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 3
DHCPOFFER of 192.168.0.18 from 192.168.0.1
DHCPREQUEST of 192.168.0.18 on ath0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.18 from 192.168.0.1
bound to 192.168.0.18 -- renewal in 126459 seconds.
                                                                         [ OK ]

```

---

### Post by michael1234 on 2008-08-26
Hey guys, cool responses! I'll try this next time I have a sec.

---

### Post by monikersupreme on 2008-08-28
> **zooterkin said:**
> I'm getting what looks like the same problem.  Compaq nw8000, with Hardy Heron installed from scratch.

After booting, wifi doesn't work.  Giving the WPA key again through the Network app sometimes gets it running the first time, sometimes it takes several goes.  Haven't managed to get this working after hibernation.

I've just tried running the networking script as suggested above, and the worked the second time after a reboot.



You can setup a script in /etc/init.d that will automatically restart networking on boot - at least this is the hack I've been using and thus far it seems to work okay...
[B]
Has anyone here figured out how to connect to unencrypted wireless? [/B]

I cannot connect to any open networks... I've no problem connecting to a WPA signal but for some reason unencrypted networks can be "seen" but not connected to... setting my wireless configuration controls to "Roaming" does not work either...

---

