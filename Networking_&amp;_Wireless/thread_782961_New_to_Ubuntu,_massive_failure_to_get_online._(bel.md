---
title: "New to Ubuntu, massive failure to get online. (belkin FSD7000, ubuntu 8.04)"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by Flaphal on 2008-05-05
Hi, I'm brand new to ubuntu and trying to get my wireless card working. (no networks are listed)

Also, I cant even manage to follow the first step in the [troubleshooting]("https://help.ubuntu.com/8.04/internet/C/troubleshooting.html") guide. (System/Preferences doesn't contain anything marked "hardware information" or "device manager")


I have checked [this list]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin") but don't know which of the FSD7000's listed there I have.

So as you can see: I'm totally lost!

Some more info about my system:
Ubuntu: 8.04 desktop, 64bit (wubi)
CPU: Core2 2.4ghz quad Q6600
Network card: Belkin FSD7000
Network: region-Europe, channel-11, mode-g and b, security-WPA-PSK [TKIP] + WPA2-PSK [AES]  (can be changed)

Troubleshooting:
"sudo lshw -C network" returns:
```
*-network UNCLAIMED
 [INDENT]description: Ethernet controller
 product: Belkin
 vendor: Belkin
 physical id: 4
 bus info: pci@0000:04:04.0
 version: 20
 width: 32 bits
 clock 33MHz
 capabilities: pm bus_master cap_list
 configuration: latency=64 maxlatency=64 mingnt=32[/INDENT]
```

"iwconfig" returns:
```
lo no wireless extensions.
```


Thanks in advance!


(updated thread: [http://ubuntuforums.org/showthread.php?p=5335818](http://ubuntuforums.org/showthread.php?p=5335818), as my situation has changed considerably)

---

### Post by Flaphal on 2008-05-06
no ideas guys?

---

### Post by superprash2003 on 2008-05-06
go to sytem->administration->restricted drivers and enabled any WLAN drivers if listed

---

### Post by Aearenda on 2008-05-06
I don't think gnome-device-manager is installed by default. On my system it's in the 'System tools' menu.

What does ```
lspci -nn
```show for the Belkin card? I have some of these, I will see if it matches any.

---

### Post by Flaphal on 2008-05-07
superprash, "sytem->administration->restricted drivers" doesnt exist, i guess you mean hardware drivers? It only shows my graphics card.

Aearenda, "lspci -nn" shows:
```
04:04.0 Ethernet Controller [0200]: Belkin Unknown device [1799:700f] (rev 20)
```


thanks

---

### Post by Aearenda on 2008-05-07
Ok, it's different from all of mine. See if this thread helps: 
[http://ubuntuforums.org/showpost.php?p=3539832](http://ubuntuforums.org/showpost.php?p=3539832) especially post 26
If you run into the issue of it only working on the second attempt, there are ways to automate that.

Others of interest:
[http://ubuntuforums.org/showthread.php?t=713058](http://ubuntuforums.org/showthread.php?t=713058)
[http://tennessee.ubuntuforums.com/showthread.php?p=4328866](http://tennessee.ubuntuforums.com/showthread.php?p=4328866)
[http://www.uluga.ubuntuforums.org/showthread.php?t=381878&page=3](http://www.uluga.ubuntuforums.org/showthread.php?t=381878&page=3)

Good luck!

---

