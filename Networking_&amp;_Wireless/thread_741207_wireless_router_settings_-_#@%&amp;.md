---
title: "wireless router settings - #@%&amp;"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by Th3Professor on 2008-03-31
iwconfig --> my wireless card is up and running.
iwlist scanning --> shows that my wireless router is also up and running.

Wireless card settings are default.
Wireless router settings are default.

Why am I not connecting to my wireless router?

EDIT:
Update. I can connect to my router, wired, though not wireless. On attempts connecting to other local wireless connections (aka, neighbors who do not have WEP/WPA/etc. enabled, for testing purposes only) I am unable to connect wireless to them.

This leads me to believe that something needs to change with my computer's settings. However, the iwlist scanning successfully recognizes multiple wireless services, including my own. So my wireless card is working, there just seems to be some (probably small) step that I am missing. Any ideas? Troubleshooting steps maybe?

EDIT 2:
I forgot these forums have a category on networking/wireless. Could an 'ubuntu forum staff' please move this thread there? Thank you.

I tried the steps provided in this thread:
[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)
Including this...
```

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

```
...and it didn't work. This was the output:
```

(After following the 1st 5 steps...)
# dhclient eth1
There is already a pid file /var/run/dhclient.pid with pid (# omitted)
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/xx:xx:xx:xx:xx:xx
Sending on   LPF/eth1/xx:xx:xx:xx:xx:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

---

### Post by cmnorton on 2008-03-31
One thing to try is this:

1) Save a copy of /etc/network/interfaces, so you have the original.

2) Edit the interfaces, so it just has these lines, not counting any comments that are there

auto lo
iface lo inet loopback

3) Stop and re-start your network.

---

### Post by Th3Professor on 2008-03-31
> **cmnorton said:**
> One thing to try is this:

1) Save a copy of /etc/network/interfaces, so you have the original.

2) Edit the interfaces, so it just has these lines, not counting any comments that are there

auto lo
iface lo inet loopback

3) Stop and re-start your network.

No luck there.

By stop/restart, is ifdown -a and ifup -a fine? This is what happened with step 3:

```

# ifdown -a
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-down.d/50firestarter exited with return code 2
# ifup -a
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2

```

Should I disable Firestarter? I didn't think that'd make a difference.

EDIT:
I took Firestarter completely out of the equation. No changes.

---

### Post by chilinski on 2008-03-31
Okay, I'm getting old and feeble and maybe I'm missing something here. However, eth1 would generally not be a wireless adapter. You might have a wifi0 or an ath0, but generally ethx is used for wired cards. 

Also Gutsy will always give connection preference to a wired connection if it's available. So if you have a wired connection, nm-applet won't let you also have a wireless one...it will always pick the wired connection.

---

### Post by ugm6hr on 2008-04-01
Let's start at the beginning:

1.Show us your *lshw -C network* ouput
2. What encryption do you use?
3. How close did you get to connecting with Network Manager?

---

### Post by Th3Professor on 2008-04-03
> **chilinski said:**
> Okay, I'm getting old and feeble and maybe I'm missing something here. However, eth1 would generally not be a wireless adapter. You might have a wifi0 or an ath0, but generally ethx is used for wired cards. 

Also Gutsy will always give connection preference to a wired connection if it's available. So if you have a wired connection, nm-applet won't let you also have a wireless one...it will always pick the wired connection.

I didn't know that... re: eth1... thx :) good to know.
(Check out my lshw below, it has eth1 = wireless, so now I'm confused.) ;)
Same with gutsy preferring wired over wireless. good to know. thanks :)

> **ugm6hr said:**
> Let's start at the beginning:

1.Show us your *lshw -C network* ouput
2. What encryption do you use?
3. How close did you get to connecting with Network Manager?

Okay, good idea... here's some info...
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       logical name: eth0
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=x.x.x.x
       latency=32 module=b44 multicast=yes
  *-network:1
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       logical name: eth1
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic
       latency=32 module=bcm43xx multicast=yes wireless=IEEE 802.11b/g

EDIT: eth0 showed a mac address, I just removed it from the output listed above. eth1 did not show a mac address.

Encryption?
Currently none - for wireless, that is - though I had tried using WPA. To simplify matters I tried no wep/wpa/etc. to try to make connecting easier, with intentions of incorporating something like wpa later (after knowing I can actually connect wirelessly).

Here's an odd thing... I think my cat5 came unplugged earlier, as it was showing the "meter" - appearing online wirelessly - though it was defaulting to a neighbor's linksys instead of my personal wireless router. I tried swapping it out to my own and it disconnected. However, it still seems to recognize - even recognize the strength (a single horizontal bar) of multiple area wireless services.

How close to connecting with network manager?
Zilch.
The "Network Settings" and "Network Tools"...
Network Settings: it doesn't let me put a check in the box next to wireless (roaming mode enabled), although it appears to be picking up local wireless services. I just have wired set to dhcp.
Network Tools: I went through the 3 provided netstat features and everything appears to be working fine... though that's wired... I'm not even sure it'd make any difference bothering with those features at this point.

---

### Post by ugm6hr on 2008-04-03
OK. BCM4306 wifi card (eth1 is correct).

Have you enabled Restricted Drivers for it?

Is your router a 54MBps (i.e. 802.11g) or 11MBps (i.e. 802.11b)?

The most likely answer is that your router is 802.11g, and broadcasting in "g mode only" rather than "mixed b/g mode".

Unfortunately, BCM cards do not work with g speeds unless you use ndiswrapper.

Try checking the router settings, and change to mixed b/g.

Then try again.

---

### Post by kevdog on 2008-04-03
Also did you bring down the wired connection first and turn off firestarter (for now):

Turn off firestarter

Then bring down wired connection, then bring up the wireless connection and try to connect

sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_IN_QUOTES"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

---

### Post by Th3Professor on 2008-04-04
> **ugm6hr said:**
> OK. BCM4306 wifi card (eth1 is correct).

Have you enabled Restricted Drivers for it?

Is your router a 54MBps (i.e. 802.11g) or 11MBps (i.e. 802.11b)?

The most likely answer is that your router is 802.11g, and broadcasting in "g mode only" rather than "mixed b/g mode".

Unfortunately, BCM cards do not work with g speeds unless you use ndiswrapper.

Try checking the router settings, and change to mixed b/g.

Then try again.

Restricted drivers are enabled.
My wireless router is set to b/g.

> **kevdog said:**
> Also did you bring down the wired connection first and turn off firestarter (for now):

Turn off firestarter

Then bring down wired connection, then bring up the wireless connection and try to connect

sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "ESSID_IN_QUOTES"
sudo iwconfig eth1 mode Managed
sudo dhclient eth1

Did all of the things mentioned above, still no luck. :(

On dhclient eth1 it said there is already a pid file.
It stated itself as listening and sending, though ended up with:
"No DHCPOFFERS received." and:
"No working leases in persistent database - sleeping.

Odd is that I didn't see the leases message on my last attempt.

I went back to wired, via the same router, and it almost immediately reconnected.

My card in my computer is using the broadcom firmware, not an ndis wrapper. I'm not sure if that matters though, it still seems to be recognizing various wireless connections, showing different strengths. Maybe it's the router, not sure. <shrugs>

---

### Post by kevdog on 2008-04-04
Can you just for kicks give ndiswrapper a try??

And if there is already a process id for eth1 then put a couple of things together like sudo dhclient -r eth1

---

### Post by Th3Professor on 2008-04-04
> **kevdog said:**
> Can you just for kicks give ndiswrapper a try??

And if there is already a process id for eth1 then put a couple of things together like sudo dhclient -r eth1

Okay, tried ndiswrapper, though to no avail. I tried various arrangements - disabling the proprietary driver & installing ndiswrapper (common & utils), re-enabling the proprietary driver + ndis wrapper. (With a eth0 down & release and eth1 up and dhclient (renewing eth1 on each attempt).

Before all that I went ahead tried releasing eth1, it helped at least in the regard of not bringing up that message again (about the lease).

<sigh> ...getting bummed out about this... </sigh>

---

### Post by kevdog on 2008-04-04
you need to post some output..telling me things are not working does not help me to help you!

---

### Post by Th3Professor on 2008-04-04
After installing (ndiswrapper), I read the manpages, and checked out the "--help" and it didn't seem to have much I could do. Perhaps I didn't correctly incorporate the ndis wrapper.

How do I directly apply the ndiswrapper (other than a simple install) to my card?

---

### Post by kevdog on 2008-04-05
Ive tried to explain and be the most thorough I could be in this thread:
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

