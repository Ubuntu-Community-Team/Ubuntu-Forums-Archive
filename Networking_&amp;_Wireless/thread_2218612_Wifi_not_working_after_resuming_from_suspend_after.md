---
title: "Wifi not working after resuming from suspend after upgrading from 12.04 to 14.04"
date: 2014-04-21
forum: Networking &amp; Wireless
---

### Post by ubifree on 2014-04-21
Since upgrading from ubuntu 12.04 LTS to 14.04 LTS on my Dell Studio 1737 laptop the wifi has not been reconnecting after waking the laptop from suspend. I did not have this problem in 12.04.  I tried the fix at [http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html](http://www.webupd8.org/2013/01/fix-wireless-or-wired-network-not.html) but that made no difference (I used [COLOR=#000000][FONT=UbuntuBeta Mono]SUSPEND_MODULES="$SUSPEND_MODULES [/FONT][/COLOR]iwlwifi[COLOR=#000000][FONT=UbuntuBeta Mono]"). For my wireless connection, [/FONT][/COLOR]*sudo lshw -C network* reports:

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
  *-network               
       description: Wireless interface
       product: Ultimate N WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 00
       serial: 00:16:ea:e3:90:76
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.13.0-24-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:49 memory:f8000000-f8001fff

```

Anyone know how to fix this please?

---

### Post by mih-com on 2014-04-21
not working = not connecting to wifi APs?

---

### Post by ubifree on 2014-04-21
Yes, that's right. The various SSIDs of local wifi networks are listed as normal in the dropdown of connections. But it fails to connect to any of them.

Actually, somewhat embarrassingly, it HAS just reconnected to wifi by itself after waking from suspend. Maybe it has to be suspended for more than a certain amount of time before it will reconnect successfully?  When I tested it previously I was only suspending it for less than a minute before wakening it, whereas it has just been suspended for at least half an hour. Either way I didn't have this problem with 12.04. I don't know what's going on here...

---

### Post by mih-com on 2014-04-21
where is many topics in forum 2 pages, for example: [http://ubuntuforums.org/showthread.php?t=2218526](http://ubuntuforums.org/showthread.php?t=2218526)
but all not solved

---

### Post by ubifree on 2014-04-21
Thanks. I did look at various forum posts before posting this thread but didn't find anything that looked relevant to my situation. I also came across [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552) which may be what I have.  BTW The only way I can get networking back after suspending the laptop is by restarting the laptop.  Logging back out and in again isn't sufficient.

---

### Post by 2TallSwede on 2014-04-24
I have the exact same problem, also with a Dell. After suspending it for the day, it won't reconnect to any existing network unless I restart the laptop.

---

### Post by ubifree on 2014-04-25
I still have this issue. I've just posted some comments on [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1286552) to help them debug it. I thought I'd 'fixed' it for a while by pruning the list of wireless connections under Network Connections and making sure only **one** of the currently available access points had 'Automatically connect to this network when it is available' checked. This worked beautifully for a whole day, reconnecting to wifi automatically after suspending.  But the next day it didn't work:(.  Just posting this in case it works for someone else.

---

### Post by ubifree on 2014-06-08
Finally found a fix that works: [[COLOR=#1155CC][FONT=Arial]_[http://askubuntu.com/a/368836](http://askubuntu.com/a/368836)_[/FONT][/COLOR]]("http://askubuntu.com/a/368836")

---

