---
title: "Connected to net but can't access network for files"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by metrorat on 2007-10-05
Hi All... I am newb of the newbs but have rapidly become addicted to Ubuntu (7.04FF) over the past couple of months.

Setup:
Acer Aspire 5652 WLMi running Ubuntu/XP
Clunky old Dell XP box
Linksys WRT350N with storage link (5-partition NTFS USB drive attached)
Draytek Vigour 100 modem/bridge

Problem:
Since setting up wireless todayI hae found that I can't access the network drive attached to the 350n from Ubuntu.  I can however access the internet wirelessly (which is great).  I can map the partitions on the network drive from windows and connect to them so I'm pretty sure all router the settings are ok, however when I try and view the network from Ubuntu I get a 'Windows Network' icon and nothing beyond that except a depressingly empty window.

At the CLI smbtree comes back with nowt... this is a new development.  I couldn't connect to shared drives earlier but smbtree did list both my XP box and wireless network.  Now its keepng a stony silence.

Any help would be much appreciated... Thanks in advance.

---

### Post by metrorat on 2007-10-06
Update.... Linux saw the network and I could access the files for about 5 minutes.  Then it reverted back to the previous state of no access.  Weirdly the internet is running flawlessly. Are there any known issues with samba which prevent filesharing over LAN i.e sparodic detection of workgroup computers/networks (including itself)... I'm starting to tear hair out.  Can anyone help?

---

