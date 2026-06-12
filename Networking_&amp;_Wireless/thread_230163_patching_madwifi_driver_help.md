---
title: "patching madwifi driver help"
date: 2006-08-05
forum: Networking &amp; Wireless
---

### Post by wildseven on 2006-08-05
hii. i am trying to patch my madwifi driver so i can packet inject.   my wg511t works fine but aparantly on the aircrack-ng website i MUST patch. well i am trying to follow these steps [http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)
and i downloaded the madwifi-ng-r1679.patch from [http://patches.aircrack-ng.org/](http://patches.aircrack-ng.org/) 

the instructions i followed step by step, but there is a couple things that didnt work well.
i did wifi0 which didnt work, said there was no device, so i guessed maybe they wanted to turn my other wifi off so i did eth0 off and that was already off.

i then did 
```
find /lib/modules -name 'ath*'  -exec rm -v {} \; 2>/dev/null
find /lib/modules -name 'wlan*' -exec rm -v {} \; 2>/dev/null
```
for both of them nothing happend, i waited for the verbose for a couple minutes but nothing.

then this line didnt work
```
svn checkout http://svn.madwifi.org/trunk/ madwifi-ng
```

i didnt bother with the wget because i downloaded the patch previous to turn off my ath0 and eth0

i did
```
patch -Np1 -i madwifi-ng-r1679.patch
```
and it asked me what file i wanted to patch and i wasnt sure. i stopped here. any help at all would be nice, thank you.

---

### Post by wildseven on 2006-08-05
anything?

---

