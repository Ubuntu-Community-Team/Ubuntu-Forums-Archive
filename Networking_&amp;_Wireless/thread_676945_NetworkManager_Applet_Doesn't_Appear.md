---
title: "NetworkManager Applet Doesn't Appear"
date: 2008-01-24
forum: Networking &amp; Wireless
---

### Post by JasonMU on 2008-01-24
Hi All,

My NetworkManager applet does not show up in the panel when I login even though it is scheduled to start in System->Preferences->Sessions.  The actual network manager daemon seems to be working fine (e.g. the applet appears and functions normally when I run nm-applet in the terminal). Any thoughts about why this might be?

thanks in advance!
Jason

PS: I'm running ubuntu 7.10

---

### Post by Lord Illidan on 2008-01-24
Wierd, check the command in Sessions window, check if it's correct.

---

### Post by tomjennings on 2008-04-08
metoo

In my case, there was no nm-applet executable, nor in gnome sessions. apt-get- told me it was in network-manager-gnome, installed that. Now in sessions, ps shows nm-applet --sm-disable running. Still not in the panel, nor in list from right-click panel -> Add to Panel.

I kill nm-applet and run in terminal window. Now I can see a problem:

** (nm-applet:11861): WARNING **: <WARN>  nma_dbus_init(): could not acquire its service.  dbus_bus_acquire_service() says: 'Connection ":1.1044" is not allowed to own the service "org.freedesktop.NetworkManagerInfo" due to security policies in the configuration file'


dbus running and no other known dbus problems:


tomj@zx:~$ ps ax | egrep dbus
 4889 ?        Ss     0:02 /usr/bin/dbus-daemon --system
 6103 ?        Ss     0:00 dbus-daemon --fork --print-address 25 --print-pid 27 --session
11477 ?        Ss     0:00 dbus-daemon --fork --print-address 25 --print-pid 27 --session

I installed 8.04 from DVD iso two weeks back, have done upgrades since then, maybe something slipped through the cracks.

All networking configures manually just fine (ifup for eth0, or iwlist iwconfig etc for wlan0).


Boo hoo, oh woe is me; any hints?

---

### Post by tomjennings on 2008-04-08
Oh my, don't you hate it when you find the fix after posting?


I fixed the dbus policy issue manually with the info from this post

[http://lists.freedesktop.org/archives/dbus/2007-January/006877.html](http://lists.freedesktop.org/archives/dbus/2007-January/006877.html)

Specifically I added to /etc/dbus-1/system.d/nm-applet.conf

	<policy group="netdev">
		<allow own="org.freedesktop.NetworkManagerInfo"/>

		<allow send_destination="org.freedesktop.NetworkManagerInfo"/>
                <allow send_interface="org.freedesktop.NetworkManagerInfo"/>
	</policy>


and myself to group netdev. Reboot and it's all there and working.

---

