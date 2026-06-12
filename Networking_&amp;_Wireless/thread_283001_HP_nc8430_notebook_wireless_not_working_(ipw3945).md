---
title: "HP nc8430 notebook wireless not working (ipw3945)"
date: 2006-10-23
forum: Networking &amp; Wireless
---

### Post by LoermansA on 2006-10-23
Hi all,

Just installed Edgy Eft on my HP nc8430 and most things seem to work fine. Except for wireless. The module is loaded and dmesg appears fine:

> 
[17179598.452000] ipw3945: Intel(R) PRO/Wireless 3945 Network Connection driver for Linux, 1.1.0mp
[17179598.452000] ipw3945: Copyright(c) 2003-2006 Intel Corporation
[17179599.680000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[17179601.596000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802.11a channels)


From what I've read it should work out of the box (I have the restricted-modules installed from the restricted repository). Problem is, I don't know what to do next. All posts seem to indicate that it should 'just work (tm)'. Network-manager-gnome is installed

Any help?

Arjan

---

### Post by Yako on 2006-10-23
It seems to be a problem that it doesn't create an eth1 interface for the card... I'm having the same problem with my HP dv1668ea with Intel/PRO Wireless card. Still figuring out a solution.

---

### Post by LoermansA on 2006-10-24
I actually did have an eth1 in my /etc/network/interfaces, but one of the advices I read was that I should remove this because only then network-manager will manage that connection.

Putting it back in doesn't do anything for me either.

Arjan

---

### Post by LoermansA on 2006-10-28
I seem to have resolved the issue, although I'm not exactly sure what I did. The only thing that has changed since I last tried wireless is that I added 'gnome-settings-daemon' to my session. Apparently this wasn't loaded by default (might have something to do with me toying with XGL and Beryl).

The reason I looked into the settings-daemon was that my gnome fonts were too big, no matter what I configured in the fonts settings (font size and screen DPI). After adding gnome-settings-daemon to my session, my font problems are gone and perhaps this resolved the wireless problem as well (would make sense if the setting-daemon is somehow responsible for network settings as well, although I doubt it).

Anyway, it works now. If anybody has the same problem I had, I'm willing to investigate further, but for now it 'just works (tm)'.

Arjan

---

