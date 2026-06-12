---
title: "Network Discovery"
date: 2022-01-13
forum: Networking &amp; Wireless
---

### Post by dureal99d on 2022-01-13
Ok so we've seen time and time again about windows machines not recognizing Linux machines, but what about Linux machines not seeing windows based machines?
I daily drive ubuntu with gnome 41 installed and i love it and yes after installing WSDD all windows machines can easily discover my Linux machines, but non of my Linux machines discover windows machines unless done manually. is there a fix to this?

---

### Post by TheFu on 2022-01-13
> **dureal99d said:**
> Ok so we've seen time and time again about windows machines not recognizing Linux machines, but what about Linux machines not seeing windows based machines?
I daily drive ubuntu with gnome 41 installed and i love it and yes after installing WSDD all windows machines can easily discover my Linux machines, but non of my Linux machines discover windows machines unless done manually. is there a fix to this?

Just a though, have Windows use standard protocols like DNS?
For home networks, mDNS lets systems announce their services and network location, but I'd be afraid to have that on a corporate LAN with a 255.255.240.0 netmask. The broadcasts would make the network slow.

---

### Post by Morbius1 on 2022-01-14
There actually is a fix for this ... just not for you.

In Kubuntu I can go to Dolphin > Network > SMB Shares 

I will see the Win10 host and can list it's shares:

[ATTACH=CONFIG]289799[/ATTACH]
Notice it not only shows you the host name but how it discovered it. KDE has created a wsdd client.

Gnome was asked to incorporate this in it's gvfs-backends utility but they clearly did not understand the question since they pointed to the WSD mechanism that you enabled on the Linux server which as you pointed out works great Win10 to Linux. Not so much the other way around. Gnome really needs a samba subject matter expert so I'm not sure when or if they will duplicate what KDE has done.

WIn10 can use the other multicast mechanism ( wsdd is multicast ) that Linux / MacOS uses but because of a bug in gvfs you need to specify not only the mDNS host name of the server but also it's share:
[ATTACH=CONFIG]289800[/ATTACH]

Outside of enabling SMB1 on everything in your network which is not considered secure your only options are to bypass a gvfs bug and connect to the server and it's share as you have done or use a mount.cifs mount.

---

### Post by dureal99d on 2022-01-15
Well dang, that sucks.

I was sure hoping for a fix of sorts

---

