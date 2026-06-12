---
title: "Wireless broken, fixed...but why?"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by David Valentine on 2006-12-13
On the off chance this might be useful in sleuthing your wireless woes, I'm posting my recent wireless failure and success.

I'm running Kubuntu Edgy 6.10 on a laptop with a BCM4306 wireless PCI card identified as eth1.  I was able to access my Linksys WRT54G router just fine until one day, it just stopped.  I could still "see" my router using knetworkmanager, wifi assistant, iwconfig, etc, but no amount of attempting to connect would work--the connection failed every time with no DHCP offer and no IP address.

Then I noticed that my router's access point was one digit different from my router's MAC address (e.g., ap AB:CD:EF:GH:IJ:K**L**, vs. MAC AB:CD:EF:GH:IJ:K**K**).  So I ran the following:```
$ sudo iwconfig eth1 essid {routerSSID} ap {routerMAC} commit
```My next attempt at connecting worked immediately, but the access point's final digit is again incremented by one.  Thus it appears I have to run the above iwconfig command after each boot.  This seems like it might be a bug in the way Edgy is handling access points, but I'm too much of a noob to understand what really is going on.  Perhaps some wireless gurus could weigh in here?

Clarification:  I'm using fwcutter (not ndiswrapper).  And I'm now running "kdesu iwconfig..." etc. at each startup, with consistently excellent results.

---

### Post by maxamillion on 2006-12-13
It might be possible that upon establishing a connection to the access point, it doesn't negotiate an ip address. Try running "sudo dhclient" next time you boot and see if that works, if so there might just be an issue with the order the connection client is doing things (ie - trying to get an ip address before a connection to an access point is made) this happened to me with my iBookG4 under dapper flight 5 but was later fixed.

/me

---

### Post by David Valentine on 2006-12-13
During my earlier sleuthing, I ran ```
$ sudo dhclient eth1
```several times with little joy.  Out of perhaps a dozen attempts, I got a DHCP offer and IP address once, which almost instantly vanished.  Per the Ubuntu wiki [wireless troubleshooting guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide"), I also preceeded it with a network restart, i.e.,```
$ sudo invoke-rc.d networking restart
$ sudo dhclient eth1
```Still no joy.  But the "fix" I posted above is working so consistently that I've added it to my autostart until a more permanent, non-kludgy one is available.

---

