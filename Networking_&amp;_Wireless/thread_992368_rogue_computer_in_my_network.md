---
title: "rogue computer in my network?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by jon.reeve on 2008-11-24
This is going to sound pretty strange, but when I try to log into my university's network, it won't work, and I noticed I get about a million of these messages in the syslogs: 

Nov 24 17:55:41 pia kernel: [  479.714073] wlan0: associate with AP 00:0f:24:70:ed:e0
Nov 24 17:55:41 pia kernel: [  479.912175] wlan0: associate with AP 00:0f:24:70:ed:e0
Nov 24 17:55:41 pia kernel: [  479.913914] wlan0: deauthenticated
Nov 24 17:55:42 pia kernel: [  480.912187] wlan0: authenticate with AP 00:0f:24:70:ed:e0
Nov 24 17:55:42 pia kernel: [  480.914338] wlan0: authenticated
Nov 24 17:55:42 pia kernel: [  480.914359] wlan0: associate with AP 00:0f:24:70:ed:e0
Nov 24 17:55:42 pia kernel: [  481.112110] wlan0: associate with AP 00:0f:24:70:ed:e0
Nov 24 17:55:42 pia kernel: [  481.113803] wlan0: deauthenticated

but if I go to another room in the library I can connect there and then bring my laptop back to the original room once it's already connected and I won't be getting these messages anymore. So I'm wondering, what's with this? Is another computer in this room trying to connect to mine, or is there something else going on here? This isn't that big of a problem but it has happened a few times and I'd like to know what's causing it or what might fix it.

---

### Post by spd106 on 2008-11-25
It doesn't look like anything unusual to me. Your NIC is just trying to connect to an Access Point and it's not quite working. It's usually due to interference or contention for that particular AP.

I wouldn't worry about it.

---

### Post by jon.reeve on 2008-12-08
I still can't get around this problem. I can't connect to the network from the room I'm in, but I can walk all the way down the hall, connect to the network there, and then come back to this room and everything's OK. But then after awhile I'll have a complete freeze, where the display still works but everything is frozen and I have to hard-reset my entire machine. I've never had my entire computer freeze in all the years I've been running Linux, so this concerns me. It can't be good for the drive, either, to keep hard rebooting it like this. Nothing shows up in the system logs about the freeze, and this only happens in this one particular room of the library. Weird.

---

