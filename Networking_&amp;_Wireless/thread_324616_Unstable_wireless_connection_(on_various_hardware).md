---
title: "Unstable wireless connection (on various hardware)"
date: 2006-12-24
forum: Networking &amp; Wireless
---

### Post by c.dric on 2006-12-24
hey, 

i've been testing xubuntu on two of my computers lately and i really like IF it wasn't for the unstable wireless connection.

until 10 days ago, my wireless network looked like this : 
- Airport Express as router (DHCP & WPA)
- iMac with OSX
- Centrino with Gentoo (ipw2100 with wpa_supplicant)
- AMD K7 with Gentoo (smc2802v2 with ndiswrapper and wpa_supplicant)
i had a hard time getting the 2 gentoo box connected but once i got it, it worked fine for the following 2 years.

**1/** i've started installing xubuntu on the amd desktop and it all went well plus i'm tired of gentoo needing more than 30+ minutes for an emerge sync (the equivalent of apt-get update) so i really wish i could keep ubuntu ... if only i could get the wireless connection to stay connected.

once every few minutes i lose the connection for a minute or so ... now that's only annoying when listening to a web radio otherwise i wouldn't notice ... but ...
once every few hours i lose the connection completely ... the only solution i found was to unload/reload the ndiswrapper module then restart networking.

any ideas where that could come from ? 

**2/** Then i tried installing xubuntu on my laptop with centrino & ipw2100 ... it also went perfectly ... widescreen detected etc ... i managed to get wpa_supplicant working using wext as driver but i do get disconnected quite often and sometimes i even get an ip address already used by the amd desktop cited above ...


i don't think those problems are caused by the hardware because they worked fine with gentoo ... 

it could be the network but the only thing that changed is that the 2 xubuntu computers are now on the same desk. could that be part of the problem ? 

any help would be greatly appreciated ... let me know if you need the output of some command.

---

### Post by c.dric on 2006-12-24
[Small update]

i've set-up the two xubuntus with static ips so they don't end up with the same ip.

the disconnections are still there ... 

the smc2802wv2/ndis/wpa disconnects every few hours or so (plus the hiccups)
the ipw2100/wpa disconnects every few minutes even while pinging -i 5 the router.


i've noticed the same error message when i restart networking on both machines :

```
 * Reconfiguring network interfaces...
bind(PF_UNIX): Address already in use
ctrl_iface exists and seems to be in use - cannot override it
Delete '/var/run/wpa_supplicant/wlan0' manually if it is not used anymore
Failed to initialize control interface '/var/run/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

```

i'm still able to connect ... but could it cause the disconnections ?

---

### Post by c.dric on 2006-12-24
well, i've tried putting all the setting from /etc/wpa_supplicant.conf into /etc/network/interfaces as advocated by wieman01 in this thread [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) and the error messages i had when restarting networking disappeared. 

also i didn't get disconnected in the last 2-3 hours. 

*crossing fin

---

### Post by c.dric on 2006-12-24
ger*


jk

---

