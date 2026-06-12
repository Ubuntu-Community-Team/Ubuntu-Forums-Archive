---
title: "BitTorrent Error - Address already in use"
date: 2007-05-12
forum: Networking &amp; Wireless
---

### Post by cajunaggie on 2007-05-12
For some reason I can't download more than one torrent at a time. Whenever I try to open a second torrent, GnomeTorrent gives me an error:
```
"Couldn't listen - (98, 'Address already in use')
```
I'm assuming this means that the first torrent isn't letting any others through. It's nothing major, a minor annoyance really, but I was wondering if anyone knew a work-around for this. I've never run into this problem before and I'm wondering if it's specific to Feisty.

---

### Post by stoian on 2007-05-13
I found the cause and the solution on the net somewhere:
[https://bugs.launchpad.net/ubuntu/+source/gnome-btdownload/+bug/57039](https://bugs.launchpad.net/ubuntu/+source/gnome-btdownload/+bug/57039)

If using gnome-btdownload, this happens because the min port is equal to max port number.
Solution: change max port value with gconf-editor (or System Tools > Configuration Editor). Find the key <apps/gnome-btdownload/settings/max_port> larger than default 6881 fixes this. I've set max port value to 6892... and it works.

---

### Post by RomeReactor on 2007-05-13
Hi. This issue is very common on fresh installs: The default setting for Gnome-Bittorrent is to assign only one port (6881); to solve this problem, open a terminal (Applications-->Accessories->Terminal) and enter

```
gconf-editor
```

Once it opens, go to **apps-->gnome-btdownload-->settings** and to change the values, double click on **min_port** (it should be 6881) and **max_port** (6889)

**NOTE:** I've had this issue since at least Dapper, but I believe it's been there since the beginning (Warty).

---

