---
title: "Tearing my hair apart: how does XP connect?"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by sierra1bravo on 2008-09-19
Dear all
This is really driving me up the wall... 

I am currently staying at a motel near San Francisco. The motel has a wireless, which I can connect from my laptop (T61 running Gutsy) provided I sit in the lobby (this is as advertised by the motel). I am unable to connect from my room which is a few tens of feet away, even though the network is visible and of moderate strength (the rotating cursor keeps going without connecting).

However, when I boot up from XP sitting in my room (there is a rarely-used and unstable partition on my T61), it connects INSTANTANEOUSLY. In fact, XP boots up already connected. 

Apart from the utility angle, this is an embarassment for me as an Ubuntu advocate, as my friends staying in the next room and using Vista, have no problems either :-(

Can anyone throw light on this? Any parameters I can tweak? (if so, why aren't they tweaked in the first place?)

cheers

s1b

---

### Post by wolterh on 2008-09-19
Is your wireless connection in roaming mode?
If not, do so. Otherwise, uncheck the roaming mode box and set it to DHCP (Which will automatically assign an IP for you)

---

### Post by oilchangeguy on 2008-09-19
it seems that ubuntu, and linux in general don't handle wireless connections as good as windows does. i'm using a windows computer now, and it connects fine. however (i thought about dual booting it) i tried the 8.04 live cd, and it did connect, for about five minutes. then if i click on the icon, and click on the network, the icon just goes round and round, and never connects. also i had mandriva on a separate hard drive in a laptop. i'd switch it out with the windows hard drive. It's a gateway, with a broadcom adapter. and i'm not jumping thru hoops to get the internal wireless to work, when my usb wireless connection works. fine. however, some how when i ran the lappy from the windows hard drive i could not get it to connect to the internet. i had to uninstall and reinstall the internal wireless driver. and that makes no sense. so long story short, neither of my computers run linux at the present time.

---

### Post by sierra1bravo on 2008-09-20
> **woli said:**
> Is your wireless connection in roaming mode?
If not, do so. Otherwise, uncheck the roaming mode box and set it to DHCP (Which will automatically assign an IP for you)

Thanks, but did everything in the book. Ran the iw* set of commands where the network is detected in the scan. However, dhclient fails.

I am using the laptop on Gutsy in the lobby right now...and I know for sure it will fail in a few minutes when I go to my room, and also know for sure that XP will connect happily in room :-(

Are there any informed answers why this happens?

s1b

---

### Post by caljohnsmith on 2008-09-20
Instead of using roaming mode, have you tried to manually connect to their WLAN? Try System > Admin > Network, unlock, click you wireless interface, "properties", and then can you see their WLAN listed in the drop-down list under "network name"? If so, choose it, and set the "configuration" to DHCP, and try and connect. What happens when you try that?

---

### Post by lswb on 2008-09-20
> **sierra1bravo said:**
> 
Are there any informed answers why this happens?


It may be another fault of NetworkManager. It's likely a motel needs repeaters or more than one access point. I have trouble at a few places where repeaters or multiple access points with the same essid are being used, NM won't select the right one. I installed the rutilt connection tool to use in those cases; It lists all access points in range, even if they have identical essids, and distinguishes between them by listing their hardware addresses as well. You can see the same info by running 

sudo iwlist scanning eth1 

in a terminal, use your wireless interface name where I use eth1. The command line tools can also be used to connect of course but that can be kind of tedious. With rutilt you can just try the different APs until one connects.

There are other network connection tools you can use also. One of the more popular is wicd, do a forum search to find out how to install it. It is not in the standard ubuntu repositories but there is a ubuntu-compatible repository you can add so it can be installed via synaptic or apt-get. Installing wicd will force the uninstallation of NetworkManager. 

An older tool that I used quite successfully with 6.06 is wifi-radar. It is available in the ubuntu repositories. I used it briefly with hardy but currently don't have it installed. I don't recall offhand whether installing wifi-radar forces removal of NM or not. However, like rutilt, it only handles wireless interfaces. So if you do uninstall NM, you may need another way to manage your _wired_ connections. On my dapper system I used wifi-radar for wireless and the old reliable /etc/network/interfaces file and ifplugd for wired connections.

If you try to connect via command line or these other alternatives it may help  to temporarily stop Network Manager, which can be done by
```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

To restart nm replace "stop" with "start". I have this script in my path so I don't have to memorize those lines:

netman
```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@

```

Then just type "sudo netman stop" or "sudo netman start" 

I like some of the features of Network Manager but it IMHO it is not ready for prime time as shipped with hardy. Hopefully the problems will be corrected in an upgrade that will be made available for hardy.
 
HTH, good luck.

---

### Post by sierra1bravo on 2008-09-22
First of all, thanks very much, lswb, for that substantive response. It is experts like you who take time off to share that enriches Ubuntu and other open source communities.

It is good to know that improvements are in the offing. I downloaded rutilt, which showed me that there were three APs with the same name. Despite some effort, I was unable to connect to any of them. I will try again later.

best

s1b


> **lswb said:**
> It may be another fault of NetworkManager. It's likely a motel needs repeaters or more than one access point. I have trouble at a few places where repeaters or multiple access points with the same essid are being used, NM won't select the right one. I installed the rutilt connection tool to use in those cases; It lists all access points in range, even if they have identical essids, and distinguishes between them by listing their hardware addresses as well. You can see the same info by running 

sudo iwlist scanning eth1 

in a terminal, use your wireless interface name where I use eth1. The command line tools can also be used to connect of course but that can be kind of tedious. With rutilt you can just try the different APs until one connects.

There are other network connection tools you can use also. One of the more popular is wicd, do a forum search to find out how to install it. It is not in the standard ubuntu repositories but there is a ubuntu-compatible repository you can add so it can be installed via synaptic or apt-get. Installing wicd will force the uninstallation of NetworkManager. 

An older tool that I used quite successfully with 6.06 is wifi-radar. It is available in the ubuntu repositories. I used it briefly with hardy but currently don't have it installed. I don't recall offhand whether installing wifi-radar forces removal of NM or not. However, like rutilt, it only handles wireless interfaces. So if you do uninstall NM, you may need another way to manage your _wired_ connections. On my dapper system I used wifi-radar for wireless and the old reliable /etc/network/interfaces file and ifplugd for wired connections.

If you try to connect via command line or these other alternatives it may help  to temporarily stop Network Manager, which can be done by
```

sudo /etc/dbus-1/event.d/25NetworkManager stop
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop

```

To restart nm replace "stop" with "start". I have this script in my path so I don't have to memorize those lines:

netman
```

#!/bin/bash

[ "0" != "$UID" ] && ( echo "Must run as root!" ) && exit

/etc/dbus-1/event.d/25NetworkManager $@
/etc/dbus-1/event.d/26NetworkManagerDispatcher $@

```

Then just type "sudo netman stop" or "sudo netman start" 

I like some of the features of Network Manager but it IMHO it is not ready for prime time as shipped with hardy. Hopefully the problems will be corrected in an upgrade that will be made available for hardy.
 
HTH, good luck.

---

