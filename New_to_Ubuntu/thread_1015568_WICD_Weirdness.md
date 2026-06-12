---
title: "WICD Weirdness"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by E. Mark Mitchell on 2008-12-18
Got a strange happening with my wicd program.

I operate on a laptop, which as most of you know, means I have to jump through some hoops to get my wireless to work.  Well, the way I do it is through wicd.  And wicd has started to act up.

Every time I try and connect to my home network, it tries to connect for a little less than a second and then quits.  The difficulty is not that wicd can't connect; as a test, I connected to the neighbor's unsecured network just fine.  I double-checked the passcode, and it's correct.  My wife's laptop connects just fine, so I know it's not a general problem with the router.  I just can't get it to connect.

I have no idea how to approach this problem.  There appear to be settings, but I can't tell if they're wrong.  Does anyone know wicd enough to suggest a fix?

---

### Post by andrew.46 on 2008-12-18
Hi,

Good to see a fellow wicd user :-). With troubleshooting you might be best to have a look at the logfile. If you are running Intrepid Ibex as I am this log can be accessed by pressing Alt F2 and then:

```
gksudo gedit /var/log/wicd/wicd.log
```

Hopefully some hints there of the trouble.

All the best,

  Andrew

---

### Post by E. Mark Mitchell on 2008-12-21
> **andrew.46 said:**
> Hi,

Good to see a fellow wicd user :-). With troubleshooting you might be best to have a look at the logfile. If you are running Intrepid Ibex as I am this log can be accessed by pressing Alt F2 and then:

```
gksudo gedit /var/log/wicd/wicd.log
```

Hopefully some hints there of the trouble.

All the best,

  Andrew
Ha!  Well, I'm glad to be here.  I'm kind of a wicd user by default, because I've not found any other way to get the wireless chipset in my laptop to work.  Can be a pain, especially with kernel updates, but you do what you have to, right?

Okay, so I opened up a terminal and plugged in the code you suggested.  Please keep in mind, I'm a pretty good user, but my programmer skills are nascent at best; I follow step-by-step directions really well, but beyond that, it's iffy.  Sorry, just a warning up front.

Anyway, so I put in the code, and this is the logfile that got displayed:

```
2008/12/21 22:06:04 :: ---------------------------
2008/12/21 22:06:04 :: wicd initializing...
2008/12/21 22:06:04 :: ---------------------------
2008/12/21 22:06:05 :: Automatically detected wireless interface ath0
2008/12/21 22:06:05 :: found wireless_interface in configuration ath0
2008/12/21 22:06:05 :: setting wireless interface ath0
2008/12/21 22:06:05 :: automatically detected wired interface eth0
2008/12/21 22:06:05 :: found wired_interface in configuration eth0
2008/12/21 22:06:05 :: setting wired interface eth0
2008/12/21 22:06:05 :: found wpa_driver in configuration wext
2008/12/21 22:06:05 :: setting wpa driver wext
2008/12/21 22:06:05 :: found always_show_wired_interface in configuration False
2008/12/21 22:06:05 :: found use_global_dns in configuration False
2008/12/21 22:06:05 :: setting use global dns to False
2008/12/21 22:06:05 :: setting use global dns to boolean False
2008/12/21 22:06:05 :: found global_dns_1 in configuration None
2008/12/21 22:06:05 :: found global_dns_2 in configuration None
2008/12/21 22:06:05 :: found global_dns_3 in configuration None
2008/12/21 22:06:05 :: setting global dns
2008/12/21 22:06:05 :: global dns servers are None None None
2008/12/21 22:06:05 :: found auto_reconnect in configuration True
2008/12/21 22:06:05 :: setting automatically reconnect when connection drops
2008/12/21 22:06:05 :: found debug_mode in configuration 0
2008/12/21 22:06:05 :: found wired_connect_mode in configuration 1
2008/12/21 22:06:05 :: found signal_display_type in configuration 0
2008/12/21 22:06:05 :: found dhcp_client in configuration 0
2008/12/21 22:06:05 :: Setting dhcp client to 0
2008/12/21 22:06:05 :: found link_detect_tool in configuration 0
2008/12/21 22:06:05 :: found flush_tool in configuration 0
2008/12/21 22:06:05 :: Wireless configuration file found...
2008/12/21 22:06:05 :: Wired configuration file found...
2008/12/21 22:06:05 :: chmoding configuration files 0600...
2008/12/21 22:06:05 :: chowning configuration files root:root...
2008/12/21 22:06:05 :: Using wired interface...eth0
2008/12/21 22:06:05 :: Using wireless interface...ath0
2008/12/21 22:06:05 :: autoconnecting... ath0
2008/12/21 22:06:05 :: Couldn't find a default wired connection, wired autoconnect failed.
2008/12/21 22:06:05 :: No wired connection present, attempting to autoconnectto wireless network
2008/12/21 22:06:05 :: Unable to autoconnect, you'll have to manually connect
2008/12/21 22:06:53 :: GetWiredProperty: WiredNetwork does not exist
2008/12/21 22:20:00 :: Connecting to wireless network muerto
2008/12/21 22:20:00 :: Putting interface down
2008/12/21 22:20:00 :: Releasing DHCP leases...
2008/12/21 22:20:01 :: Setting false IP...
2008/12/21 22:20:01 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:20:01 :: Flushing the routing table...
2008/12/21 22:20:01 :: Putting interface up...
2008/12/21 22:20:01 :: Running DHCP
2008/12/21 22:20:01 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/12/21 22:20:01 :: Internet Systems Consortium DHCP Client V3.0.6
2008/12/21 22:20:01 :: Copyright 2004-2007 Internet Systems Consortium.
2008/12/21 22:20:01 :: All rights reserved.
2008/12/21 22:20:01 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/12/21 22:20:01 :: 
2008/12/21 22:20:01 :: wifi0: unknown hardware address type 801
2008/12/21 22:20:02 :: wifi0: unknown hardware address type 801
2008/12/21 22:20:02 :: Listening on LPF/ath0/00:1f:3a:26:8f:1f
2008/12/21 22:20:02 :: Sending on   LPF/ath0/00:1f:3a:26:8f:1f
2008/12/21 22:20:02 :: Sending on   Socket/fallback
2008/12/21 22:20:04 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
2008/12/21 22:20:08 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 4
2008/12/21 22:20:12 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
2008/12/21 22:20:20 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
2008/12/21 22:20:28 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
2008/12/21 22:20:35 :: No DHCPOFFERS received.
2008/12/21 22:20:35 :: No working leases in persistent database - sleeping.
2008/12/21 22:20:43 :: DHCP connection failed
2008/12/21 22:20:43 :: exiting connection thread
2008/12/21 22:20:46 :: Connecting to wireless network muerto
2008/12/21 22:20:46 :: Putting interface down
2008/12/21 22:20:46 :: Releasing DHCP leases...
2008/12/21 22:20:46 :: Setting false IP...
2008/12/21 22:20:46 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:20:46 :: Flushing the routing table...
2008/12/21 22:20:46 :: Putting interface up...
2008/12/21 22:20:46 :: Running DHCP
2008/12/21 22:20:46 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/12/21 22:20:46 :: Internet Systems Consortium DHCP Client V3.0.6
2008/12/21 22:20:46 :: Copyright 2004-2007 Internet Systems Consortium.
2008/12/21 22:20:46 :: All rights reserved.
2008/12/21 22:20:46 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/12/21 22:20:46 :: 
2008/12/21 22:20:46 :: wifi0: unknown hardware address type 801
2008/12/21 22:20:47 :: wifi0: unknown hardware address type 801
2008/12/21 22:20:48 :: Listening on LPF/ath0/00:1f:3a:26:8f:1f
2008/12/21 22:20:48 :: Sending on   LPF/ath0/00:1f:3a:26:8f:1f
2008/12/21 22:20:48 :: Sending on   Socket/fallback
2008/12/21 22:20:48 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 7
2008/12/21 22:20:55 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 15
2008/12/21 22:21:10 :: DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 9
2008/12/21 22:21:15 :: canceling connection attempt
2008/12/21 22:21:15 :: DHCP connection failed
2008/12/21 22:21:15 :: exiting connection thread
2008/12/21 22:21:17 :: Connecting to wireless network Lord Vader
2008/12/21 22:21:17 :: Putting interface down
2008/12/21 22:21:17 :: Releasing DHCP leases...
2008/12/21 22:21:17 :: Setting false IP...
2008/12/21 22:21:17 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:21:17 :: Flushing the routing table...
2008/12/21 22:21:17 :: Generating psk...
2008/12/21 22:21:17 :: WARNING: PSK generation failed!  Falling back to wireless key.
2008/12/21 22:21:17 :: Please report this error to the wicd developers!
2008/12/21 22:21:17 :: Attempting to authenticate...
2008/12/21 22:21:18 :: Putting interface up...
2008/12/21 22:21:18 :: exiting connection thread
2008/12/21 22:21:19 :: Couldn't find a default wired connection, wired autoconnect failed.
2008/12/21 22:21:19 :: No wired connection present, attempting to autoconnectto wireless network
2008/12/21 22:21:19 :: Unable to autoconnect, you'll have to manually connect
2008/12/21 22:21:19 :: Connecting to wireless network Lord Vader
2008/12/21 22:21:19 :: Putting interface down
2008/12/21 22:21:19 :: Releasing DHCP leases...
2008/12/21 22:21:19 :: Setting false IP...
2008/12/21 22:21:19 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:21:19 :: Flushing the routing table...
2008/12/21 22:21:19 :: Generating psk...
2008/12/21 22:21:19 :: WARNING: PSK generation failed!  Falling back to wireless key.
2008/12/21 22:21:19 :: Please report this error to the wicd developers!
2008/12/21 22:21:19 :: Attempting to authenticate...
2008/12/21 22:21:19 :: Putting interface up...
2008/12/21 22:21:19 :: exiting connection thread
2008/12/21 22:21:23 :: Couldn't find a default wired connection, wired autoconnect failed.
2008/12/21 22:21:23 :: No wired connection present, attempting to autoconnectto wireless network
2008/12/21 22:21:23 :: Unable to autoconnect, you'll have to manually connect
2008/12/21 22:21:23 :: Connecting to wireless network Lord Vader
2008/12/21 22:21:23 :: Putting interface down
2008/12/21 22:21:23 :: Releasing DHCP leases...
2008/12/21 22:21:23 :: Setting false IP...
2008/12/21 22:21:23 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:21:23 :: Flushing the routing table...
2008/12/21 22:21:23 :: Generating psk...
2008/12/21 22:21:23 :: WARNING: PSK generation failed!  Falling back to wireless key.
2008/12/21 22:21:23 :: Please report this error to the wicd developers!
2008/12/21 22:21:23 :: Attempting to authenticate...
2008/12/21 22:21:23 :: Putting interface up...
2008/12/21 22:21:23 :: exiting connection thread
2008/12/21 22:21:27 :: Couldn't find a default wired connection, wired autoconnect failed.
2008/12/21 22:21:27 :: No wired connection present, attempting to autoconnectto wireless network
2008/12/21 22:21:27 :: Unable to autoconnect, you'll have to manually connect
2008/12/21 22:21:30 :: Putting interface down
2008/12/21 22:21:30 :: Releasing DHCP leases...
2008/12/21 22:21:30 :: Setting false IP...
2008/12/21 22:21:30 :: Stopping wpa_supplicant and any DHCP clients
2008/12/21 22:21:30 :: Flushing the routing table...
2008/12/21 22:21:30 :: Putting interface up...
2008/12/21 22:21:30 :: Running DHCP
2008/12/21 22:21:30 :: There is already a pid file /var/run/dhclient.pid with pid 134519072
2008/12/21 22:21:30 :: Internet Systems Consortium DHCP Client V3.0.6
2008/12/21 22:21:30 :: Copyright 2004-2007 Internet Systems Consortium.
2008/12/21 22:21:30 :: All rights reserved.
2008/12/21 22:21:30 :: For info, please visit http://www.isc.org/sw/dhcp/
2008/12/21 22:21:30 :: 
2008/12/21 22:21:30 :: wifi0: unknown hardware address type 801
2008/12/21 22:21:31 :: wifi0: unknown hardware address type 801
2008/12/21 22:21:31 :: Listening on LPF/eth0/00:1b:38:ff:2f:e3
2008/12/21 22:21:31 :: Sending on   LPF/eth0/00:1b:38:ff:2f:e3
2008/12/21 22:21:31 :: Sending on   Socket/fallback
2008/12/21 22:21:31 :: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
2008/12/21 22:21:32 :: DHCPOFFER of 192.168.1.101 from 192.168.1.1
2008/12/21 22:21:32 :: DHCPREQUEST of 192.168.1.101 on eth0 to 255.255.255.255 port 67
2008/12/21 22:21:32 :: DHCPACK of 192.168.1.101 from 192.168.1.1
2008/12/21 22:21:32 :: bound to 192.168.1.101 -- renewal in 36509 seconds.
2008/12/21 22:21:32 :: DHCP connection successful
2008/12/21 22:21:32 :: Connecting thread exiting.
```
...which details my linkup, my disconnecting from the wired link, my attempts to log into the unsecured network downstairs, "muerto" (unsuccessfully this time, but at least it tried), and then several attempts at logging into my home network, "Lord Vader" (hey, the computer tower is black, I'm a geek, it's a natural impulse to come up with that name), before heading back to the wired connection.

Having never looked at a logfile like this before, one of the things I'm noting is the connection attempts to Lord Vader keep coming back with "WARNING: PSK Generation failed!"  I have no idea what that means, but as it doesn't hapen with muerto, I suspect it might be part of the problem, yes?  Thoughts?

---

### Post by imdano on 2008-12-21
Did you recently upgrade to 1.5.6?  I think you're seeing a bug with networks having a space in the essid.  You can try using the wpa (psk) template instead of the wpa (passphrase) template, which works around the issue for some people.  If that doesn't work you can checkout the [latest trunk version](https://code.launchpad.net/~wicd-devel/wicd/trunk), which has the fix for the bug.

---

### Post by andrew.46 on 2008-12-21
Hi,

This seems to be a fairly widespread problem. I have seen solutions here:

[http://bbs.archlinux.org/viewtopic.php?id=59563](http://bbs.archlinux.org/viewtopic.php?id=59563)

and here:

[https://bugs.launchpad.net/wicd/+bug/264447](https://bugs.launchpad.net/wicd/+bug/264447)

as well as some discussions of this issue on the forums:

[http://ubuntuforums.org/showthread.php?t=1009651](http://ubuntuforums.org/showthread.php?t=1009651)

But this would only help perhaps with Lord Vader. Can I suggest working through the solutions proposed for the "WARNING: PSK Generation failed!" message that is troubling Lord Vader and after this have a look at the dead (sic) muerto connection?

All the best,

  Andrew

---

### Post by E. Mark Mitchell on 2008-12-22
Seems like a lot of the solutions talk about reverting back to a previous version.  I'd be all up for that, no problem.  How would I go about reverting?  I can't find a menu option, and the synaptic package manager doesn't seem to have an option.  Is there a procedure?

---

### Post by imdano on 2008-12-23
> **E. Mark Mitchell said:**
> Seems like a lot of the solutions talk about reverting back to a previous version.  I'd be all up for that, no problem.  How would I go about reverting?  I can't find a menu option, and the synaptic package manager doesn't seem to have an option.  Is there a procedure?I would just upgrade to [1.5.7](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460), which was released last night.  It should fix this issue.

---

### Post by lothar_m on 2008-12-23
> **imdano said:**
> I would just upgrade to [1.5.7](https://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460), which was released last night.  It should fix this issue.

yep. I had the exact same problem. the upgrade solve it. thanks for the tip.

---

### Post by E. Mark Mitchell on 2009-11-09
Criminy, this is still open?  I managed to work out this particular problem, but there's a more recent one that's double troublesome.  I'll close this out, but I really do need help on my other; my wicd stopped working for me entirely!

---

