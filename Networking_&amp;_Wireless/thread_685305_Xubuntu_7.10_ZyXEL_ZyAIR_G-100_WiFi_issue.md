---
title: "Xubuntu 7.10 ZyXEL ZyAIR G-100 WiFi issue"
date: 2008-02-02
forum: Networking &amp; Wireless
---

### Post by rhy7s on 2008-02-02
I have an old laptop I'm installing Xubuntu on which has no ethernet interface but has a ZyXEL ZyAIR G-100 802.11g PCMCIA WiFi card. This worked fine during text based setup on my 128bit WEP network but once logged into the desktop it's a no go. There is the 140 or so updates listed in update manager but no way to get them. It won't even connect if I run the wireless open and give the notebook a static ip. Using iwconfig and ifconfig I can get it to associate with the AP but can't get any network activity. Using the network manager was entirely unsuccessful and I've since uninstalled it. I've been through 2 installs and a lot of googling and trawling the forum today not getting any further. The card shows up as an Intersil ISL3890 version 01, does anyone have any experiences that could be of assistance? Thanks.

edit: Just bit the bullet and went with ndiswrapper (as per the [wiki]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")) - seems to be running fine thus far.

---

