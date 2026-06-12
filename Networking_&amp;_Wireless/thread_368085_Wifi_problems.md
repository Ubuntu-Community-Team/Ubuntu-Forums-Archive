---
title: "Wifi problems"
date: 2007-02-22
forum: Networking &amp; Wireless
---

### Post by mmmforbiddendonut on 2007-02-22
I'm running a Dell Inspiron 6000, and I've got an issue with the wireless networking.  The list in the basic network config for wireless comes up with nothing in the list (wireless-config gui).  This happens no matter where I am or how many networks are nearby.  My solution thus far has been to use wifi-radar, which gives me mixed success.  Most of the time wifi-radar works, however about 1/3rd of the time it will not connect on the boot, and then when i enter into the wifi radar program, it will say it's connected to no IP address.  If i attempt to reconnect any of the nearby hotspots, it takes 30sec-1min to attempt a connection, then the 'active' window disappears and it returns to connected w/no IP.  When it does this, i have used iwlist scanning to see if there are networks around and it will come up.  I was unsuccessful in attempting to connect anything using the terminal commands with iwconfig.  I removed wifi-radar to see if that was blocking the basic networking, but that did not bring up the network list, and i could not connect anything.  I reinstalled wireless-tools, nothing changed.  The network card in this laptop is a Intel 2200BG, and the software is installed (ipw2200 comes up on lsmod).  I have reverted back to the wifi-radar but still have the issue of having it fail around 1/3rd of the time.  Does anyone have suggestions on how I could get the normal networking to again detect networks, any ideas on what packages i can reinstall to make it work again, or a program that fails less than wifi-radar with its connections?

Notes: Running Ubuntu Edgy, intel 2200BG wireless card, 1.6GHz pentium M, single core, 512MB ram etc.  I am not having any issues with the wired ethernet connection.

-mmm forbidden donut

---

### Post by zanglang on 2007-02-22
Does manually browsing networks and connecting via console work for you? ('iwlist', 'iwconfig' and so forth)
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?#head-048d15623c21984e52f4d8e4efa067549bb43910-2](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?#head-048d15623c21984e52f4d8e4efa067549bb43910-2)

You can also try using NetworkManager, it ought to be more intuitive than wifi-radar or the default Gnome configuration tool.
[https://help.ubuntu.com/community/WifiDocs/NetworkManager](https://help.ubuntu.com/community/WifiDocs/NetworkManager)

---

### Post by mmmforbiddendonut on 2007-02-23
I am now able to operate networking through command-line (i am somewhat of a newbie in the commands in linux) and mainly knowing dhclient was enough to get things to work.  Network Manager appears to be failing, telling me that no network devices have been found.  I did check on the Network Manager site and it lists my wireless card to be compatible.  I'm not quite sure why neither it nor the GNOME network client will work, however the command-line and wifi-radar do.  This is weird, and I think I have a configuration off somewhere.  Thanks for pointing me to the command-line guide.


mmmforbiddendonut

---

