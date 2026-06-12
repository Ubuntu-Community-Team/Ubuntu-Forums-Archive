---
title: "wireless intermittent when streaming or downloading"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by ccphilly1984 on 2010-02-06
hey there all, i'm having an issue with my wireless card hanging on me (and even making my router shut down for the rest of the network) when downloading large files using bittorrent or streaming movies to my xbox 360 using ushare... im not sure if my wlan0 config is messed up, if it is a crap driver that came with the distro. whats weird is that after this crash, i can't get ushare to work until i su and run the app without the start/stop arguments and ctrl c out of it. 

i'm running ubuntu netbook remix 9.10 on a gateway lt2032 (basically an acer aspire one)

---

### Post by ccphilly1984 on 2010-02-07
well i did some snooping around... tried using wicd as a network manager... fixes that problem, but when i close my netbook lid and reopen it, it will not re connect to the network and when i try to open up wicd, it crashes the computer 100%. i really need some help... this problem sounds like something i'd expect from windows... and the reason im using linux these days is to find reasons not to use windows

---

### Post by bapoumba on 2010-02-07
It would help giving your wireless card specifications, thanks.

---

### Post by ccphilly1984 on 2010-02-07
> **bapoumba said:**
> It would help giving your wireless card specifications, thanks.


how do i do that in linux? gateway lt2032u netbook... not sure what kind of network card they put in there

---

### Post by bapoumba on 2010-02-07
Please paste the output to 
```
lspci | grep -i net
```

---

### Post by ccphilly1984 on 2010-02-08
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by ccphilly1984 on 2010-02-08
i did a search for ubuntu and my model number... found a doc about this problem on a similar netbook to mine... i will let you know if this works...

Wireless works out of the box, but connection is flaky. To fix, open a terminal and type 'sudo apt-get install linux-backports-modules-wireless-karmic-generic'

said something about acer eee pc, which is identical in almost every spec and shape to my gateway, minus the logos.

---

### Post by sandyd on 2010-02-08
have you tried lowering the connection bitrate? dont know if this bug exists anymore, but ubuntu sometimes on some cards runs the connection at the highest bitrate possible, which is a major problem, as the highest bitrate is usually not the stablest/reliable.

---

### Post by ccphilly1984 on 2010-02-08
> **carlee said:**
> have you tried lowering the connection bitrate? dont know if this bug exists anymore, but ubuntu sometimes on some cards runs the connection at the highest bitrate possible, which is a major problem, as the highest bitrate is usually not the stablest/reliable.

hmmm... how would i change that configuration setting? i can try that out.

---

### Post by ccphilly1984 on 2010-02-08
one thing that i noticed was weird is that that intermittent problem went away when i changed my network manager to wicd, but when using wicd, once i closed the netbook cover and reopened it, i lost all wireless until i rebooted... so i changed back to the standard network manager... im hoping i can work with this because it is the closest to working 100%

---

