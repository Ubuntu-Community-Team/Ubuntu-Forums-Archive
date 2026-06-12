---
title: "wlan0 not appearing in network manager"
date: 2007-12-15
forum: Networking &amp; Wireless
---

### Post by mofrikaantje on 2007-12-15
Hi,

I've read documentation, I've searched google and this forum, and I still don't know what to do.

_Problem_:      - Yesterday morning my wireless connection worked as usual. Yesterday afternoon it didn't.
_Symptoms_:
- ifconfig showed my wireless connection (wlan0) until yesterday (but network manager didn't), and after trying to reinstall drivers and some other stuff I read on wiki's, it (ifconfig) only shows lo and eth0.
- I tried reinstalling my drivers. I tried reinstalling them, but this time I used the propietary drivers. I tried reinstalling them with ndiswrapper. No go.
- I got frustrated. I tried following [these steps]("http://ubuntuforums.org/showthread.php?t=624037") (using iee80211 and the ipw2200 driver), but I got an error:

```
sander@sander-laptop:~$ cd Desktop
sander@sander-laptop:~/Desktop$ cd ipw*
sander@sander-laptop:~/Desktop/ipw2200-1.2.2$ make
-e 
 ERROR: ieee80211.h not found in '/lib/modules/2.6.22-14-386/include'.

-e You need to install the ieee80211 subsystem from http://ieee80211.sf.net
and point this build to the location where you installed those sources, eg.:

% make IEEE80211_INC=/usr/src/ieee80211/

will look for ieee80211.h in /usr/src/ieee80211/net/

make: *** [check_inc] Fout 1
```
(Fout 1 = error 1)

- I got pissed off.

_Specifications_: - Ubuntu 7.10 with loads of added stuff (duh)
                         - Intel® PRO/Wireless 2200BG card in an Acer _notebook_

_Note_: I still can connect to the internet with cable...
[B]
Please help[/B] - I can't seem to find any useful and helpful documentation of threads here (and elsewhere)...:confused:

---

