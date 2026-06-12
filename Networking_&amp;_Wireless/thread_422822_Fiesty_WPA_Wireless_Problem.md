---
title: "Fiesty WPA Wireless Problem"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by Scipio_Publius on 2007-04-25
Hi, I have been using Ubuntu for about 5 months after listening to Linux Reality pod cast and installing Dapper Drake on my IBM t42 laptop.  So far this seems like a good alternative to Microsoft Vista.  I used Edgy for a while and everything worked just fine wireless wise however, I recently upgraded to Feisty and I have not been able to connect to any WPA encrypted access points.  I have reinstalled wpasupplicant but that had no effect.  

Looking at the syslogs of the access point it tells me 
STATION xxxx.xxxxx.xxx.xx.xx Associated KEY_MANAGEMENT(NONE)
of course the setting on the access point requires "mandatory" key management.  

With Edgy and Dapper after downloading wpasupplicant everything worked fine with the same access point.  What changed and how can I fix it to work again with WPA encryption.  I have the same problem at home with a Lynksys access point that uses WPA.

---

### Post by ruletrak on 2007-04-25
I'm a newbie with Linux but appear to have the same problem.  I'm unable to get either of two wireless adapters to work with wpa on my laptop here.  I've tried quite a few things including the articles for wpc54g version two that are listed in other areas.  I can get it to recognize the card at times but then there is no option to enter wpa codes.  I'm also using a hidden ssid but have tried disabling that and no change with the problem.  

Hoping there's an easy fix to this--don't have time to mess with lots of tech stuff--would be willing to buy another card if I knew it would plug in and go with wpa.

Have a great day,
Rusty

---

### Post by Scipio_Publius on 2007-04-25
Actually, I have the option to enter in the WPA password and user name under WPA-enterprise and even the shared key with my home network.  It just won't join the network.

When I first downloaded and ran Ubuntu WPA would not show up until I installed WPAsupplicant with Synaptic.  Maybe you should try that.

---

### Post by ruletrak on 2007-04-25
I've been able to see the wpa settings a couple times but they disappeared quickly.  I've run several of the routines suggested in the forums to install wpasupplicant and work with my wirless adapters and it comes back and says it is already installed.  Hopefully someone will give us a hand here.......

---

### Post by Scipio_Publius on 2007-04-26
Any insights into this problem?

---

### Post by ruletrak on 2007-04-26
> **Scipio_Publius said:**
> Any insights into this problem?

I've scoured the forums and have gone back and forth on several threads.  Seems it's related to the new network manager (that's just my opinion) because lots of folks say it worked before they upgraded to the new version and many of the threads say to disable it and enter things manually.  I'm functional with my windows machines and was just working on an old laptop to use for generic surfing around the house.  I think I'll try to go back to 6.10 and see if I can get the wireless working that way.  Several of the people in other threads have said they'll do that rather than wait for a fix.

Sounds like it needs some programming work and I'm not sure how long that will take.  Haven't had any experience with changes and how fast they happen or if the problem has been officially recognized at Ubuntu.  Do you know how that works with Ubuntu??

Have a great day,
Rusty

---

### Post by bobbymack on 2007-05-01
I have been trying to configure the wpa_supplicant manually... been dealing with wpa_cli...

Now hopefully I am not far off in my findings, but when I try to run wpa_cli in interactive mode it cannot connect to wpa_supplicant... so I started looking at /etc/wpa_supplicant/functions.sh

It appears there are file referenced in there that are not really there... they may be hidden, but I tried to unhide them... (probably not successfully).

Here is an excerpt from my /etc/wpa_supplicant/functions.sh:

[INDENT]#!/bin/sh

# Copyright (C) 2006 Debian/Ubuntu wpasupplicant Maintainers 
# <pkg-wpa-devel@lists.alioth.debian.org>


## This program is free software; you can redistribute it and/or

# modify it under the terms of the GNU General Public License

# as published by the Free Software Foundation; either version 2

# of the License, or (at your option) any later version.


## This program is distributed in the hope that it will be useful,

# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the

# GNU General Public License for more details.

#
# On Debian GNU/Linux systems, the text of the GPL license can be

# found in /usr/share/common-licenses/GPL.


#####################################################################
#

# global variables

# wpa_supplicant variables


WPA_SUP_BIN="/sbin/wpa_supplicant"

WPA_SUP_PNAME="wpa_supplicant"

WPA_SUP_PIDFILE="/var/run/wpa_supplicant.$WPA_IFACE.pid" <-NOT THERE!!!




# wpa_cli variables


WPA_CLI_BIN="/sbin/wpa_cli"

WPA_CLI_PNAME="wpa_cli"

WPA_CLI_PIDFILE="/var/run/wpa_action.$WPA_IFACE.pid" <-NOT THERE!!!

WPA_CLI_LOGFILE="/var/log/wpa_action.log" <-Not there

WPA_CLI_TIMESTAMP="/var/run/wpa_action.$WPA_IFACE.timestamp" <-NOT THERE!!!


# default ctrl_interface socket directory


if [ -z "$WPA_CTRL_DIR" ]; 
	then
	
		WPA_CTRL_DIR="/var/run/wpa_supplicant" <-NOT THERE!!!
fi



# verbosity variables


if [ -n "$IF_WPA_VERBOSITY" ] || [ "$VERBOSITY" = "1" ]; 
	then
	
		TO_NULL="/dev/stdout"

		DAEMON_VERBOSITY="--verbose"
else

		TO_NULL="/dev/null"
	
		DAEMON_VERBOSITY="--quiet"

fi



#####################################################################
#


[/INDENT]

There are four files I cannot locate (indicated by <-NOT THERE!!) ;) 

I wish I was smarter so I could figure this out as I want to make this work....

Cheers.

---

### Post by sdide on 2007-05-01
Hey, 

for those who had thier network working, Networkmanager and Feisty has been pretty much a pain ... unfortunately.

I personally dislike networkmanger, but the idea is good, if you do not want to bother and it just worked.

for wpa_supplicant users do not despair.

for IBM t42, 

you should be able to connect easily - as root or with sudo, do: 

~# wpa_supplicant -ieth1 -Dwext -c/etc/wpa_supplicant.conf -B

~# dhclient eth1

now for the /etc/wpa_supplicant.conf or whatever you call your favorite configfile (replace above accordingly)

you should have something like : 

ctrl_interface=/var/run/wpa_supplicant

network {
        ssid="your_ap_essid"
        key_mgmt=WPA-PSK
        pairwise=TKIP
        group=TKIP
        psk="your_secret_key"
}

if you had itr working before, it should still work.

---

### Post by patrickfromspain on 2007-05-01
maybe wifi radar will help?

---

