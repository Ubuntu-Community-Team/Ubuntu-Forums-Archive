---
title: "Wireless working but randomly disconnect (Atheros"
date: 2007-09-01
forum: Networking &amp; Wireless
---

### Post by tranalbert on 2007-09-01
I recently bought a Compaq nc6000 laptop with an Atheros AR5212 802.11abg in built wireless card. There were no problems during setup and Ubuntu recognized my card without much hassle. Connecting to my wireless router has also been successful and I have been able to use the internet and access my network from my laptop. Now, the problem lies in the fact that my wireless disconnects seemingly randomly, which means that i have to reenter my WEPPSK. After reconnecting, everything works fine until the next disconnect.

I've done a 'dmesg' and this is what I get:

[   40.988000] NET: Registered protocol family 10
[   40.988000] lo: Disabled Privacy Extensions
[   40.988000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   51.228000] ath0: no IPv6 routers present
[  127.732000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  137.896000] ath0: no IPv6 routers present
[  141.004000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  152.972000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  171.536000] ath0: no IPv6 routers present
[  184.972000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  228.704000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  247.012000] ath0: no IPv6 routers present
[  436.752000] ADDRCONF(NETDEV_UP): ath0: link is not ready
[  448.732000] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[  466.880000] ath0: no IPv6 routers present

Does anyone have any ideas how I can fix this? May thanks to those who can help me!

---

### Post by WMG_Perth on 2007-09-01
Have you tried using ndiswrapper with the windows drivers? I'm not sure whether it will solve you problem, but I noticed that I have better results with ndiswrapper and the windows drivers for my Atheros wireless card.

---

### Post by tranalbert on 2007-09-02
Found out what my problem was: Network Manager. It was a tad unstable in maintaining the connection

For everyone out there, my advice is to uninstall Network Manager and install Wicd.... It's so much better and less the hassle. I don't know why it isn't the default connection manager in Ubuntu because it should be.

Guide to installation:
[http://www.ossgeeks.co.uk/?p=166#comments](http://www.ossgeeks.co.uk/?p=166#comments)

---

### Post by robnz on 2007-09-24
I had this same problem on an HP/Compaq TC-1100 tablet running KDE and Fiesty. Knetworkmanager would connect fine at first but would then keep dropping the connection. It would usually reconnect for a while but eventually it would stop working altogether.

After a lot of Googling I think I've finally tracked down the issue as explained in these posts.
[http://thpinfo.com/2007/macbook-madwifi-networkmanager]("http://thpinfo.com/2007/macbook-madwifi-networkmanager")
[http://madwifi.org/ticket/1030]("http://madwifi.org/ticket/1030")

Basically the driver is getting confused while background scanning. In my home setup the Access Point is configured for both 802.11 modes B and G with the same essid for each. 

The fix is simple. By locking the adapter to one mode only (in my case G) the confusion is gone. Only one change is required to /etc/rc.local. Mine now looks like this (new bits in blue).

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

[COLOR="Blue"]# fix madwifi (http://madwifi.org/ticket/1030)
modprobe ath_pci
(sleep 10 && /sbin/iwpriv ath0 mode 3) &[/COLOR]

exit 0
```

This sort of change would inevitably require a reboot on that other OS. But since we're using Linux so we simply execute /etc/rc.local from a shell and then reconnect to our favorite access point.

Now my wireless is rock solid. This may have also been a problem under XP Tablet Edition because my wife was always complaining about poor wifi response before she gifted it to me. 

I hope this is useful to others,
Rob

---

### Post by rookshop on 2007-09-26
Thanks Robnz, this really helped me out...

---

### Post by robnz on 2007-09-29
Great to hear. Rob

---

### Post by WolfJay_83 on 2007-11-04
Worked like a charm Rob, thanks.

---

### Post by rach_lobster on 2008-04-03
Hello, 
I have a Thinkpad T40 with a Intel Pro/Wireless Lan 2100 3B Mini PCI Adapter, but have the same problem with it dropping.  I am new to linux but think this would solve my problem.  Could you explain the steps for a noob like me but to set mine to B instead of G and how to even edit the file.

Thanks!

---

### Post by kcallis on 2008-04-14
Well, I have tried all the tricks under 7.10, but still no go... I can connect to the router just fine, but when I connect off site, then the wireless issues kick in!!! If I attempt to do an apt-get update, it starts connecting to repositories, but eventually it will hang. If I connect to a given website, initially, I am able to reach the site, but then if I change pages, the connection hangs.
Help me Obi Wan, you're my only hope!

---

