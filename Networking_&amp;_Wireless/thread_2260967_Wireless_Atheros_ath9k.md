---
title: "Wireless Atheros ath9k"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by elwesthal on 2015-01-15
Hi all, I'm not getting my wireless pci card to work with Ubuntu 14.10. (Or Fedora21 for all that matters..) Most of the time the nwtwork isn't available at all and if it is and I manage to connect it lasts for a minute or two, then dies again.
I've googled and read the forum and noticed that several others had the same problem. I've tried some of the solutions but so far nothing is working.

I ran the famous "wireless script" but I'm not sure what to do with that information ;)

Regards!

---

### Post by elwesthal on 2015-01-15
I tried "dmesg | grep wlan0"
It doesn't look good but I'm out of ideas, maybe I should just give up the penguin for this card?
(Oh WHY did I put that one in my Developer station??)

> [    1.735613] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[    5.157839] wlan0: authenticate with 58:98:35:b8:01:71
[    5.163925] wlan0: direct probe to 58:98:35:b8:01:71 (try 1/3)
[    5.365471] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[    5.432679] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[    5.494835] wlan0: authentication with 58:98:35:b8:01:71 timed out
[    5.529594] wlan0: authenticate with 58:98:35:b8:01:71
[    5.532793] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[    5.536172] wlan0: authenticated
[    5.537476] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[    5.583612] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[    5.583666] wlan0: associated
[    5.583677] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  849.404597] wlan0: authenticate with 58:98:35:b8:01:71
[  849.410710] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  849.412668] wlan0: authenticated
[  849.416198] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[  849.544183] wlan0: associate with 58:98:35:b8:01:71 (try 2/3)
[  849.556328] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[  849.556390] wlan0: associated
[  895.210545] wlan0: deauthenticating from 58:98:35:b8:01:71 by local choice (Reason: 3=DEAUTH_LEAVING)
[  899.492475] wlan0: authenticate with 58:98:35:b8:01:71
[  899.498675] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  899.506867] wlan0: authenticated
[  899.508129] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[  899.520658] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[  899.520714] wlan0: associated
[  899.520982] wlan0: deauthenticating from 58:98:35:b8:01:71 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  899.542597] wlan0: authenticate with 58:98:35:b8:01:71
[  899.545864] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  902.879381] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[  904.547342] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[  904.547372] wlan0: aborting authentication with 58:98:35:b8:01:71 by local choice (Reason: 3=DEAUTH_LEAVING)
[  906.212334] wlan0: authenticate with 58:98:35:b8:01:71
[  906.218517] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  906.218552] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[  906.220467] wlan0: authenticated
[  906.224100] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[  906.232215] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[  906.232248] wlan0: associated
[  951.205997] wlan0: deauthenticating from 58:98:35:b8:01:71 by local choice (Reason: 3=DEAUTH_LEAVING)
[  954.712390] wlan0: authenticate with 58:98:35:b8:01:71
[  954.718752] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  954.720741] wlan0: authenticated
[  954.724043] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[  954.732520] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[  954.732554] wlan0: associated
[  954.732810] wlan0: deauthenticating from 58:98:35:b8:01:71 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  954.744193] wlan0: authenticate with 58:98:35:b8:01:71
[  954.747440] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  956.451291] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[  958.119328] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[  959.748555] wlan0: aborting authentication with 58:98:35:b8:01:71 by local choice (Reason: 3=DEAUTH_LEAVING)
[  959.932281] wlan0: authenticate with 58:98:35:b8:01:71
[  959.938447] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[  959.938483] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[  960.026521] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[  960.170416] wlan0: authentication with 58:98:35:b8:01:71 timed out
[  961.840427] wlan0: authenticate with 58:98:35:b8:01:71
[  961.846717] wlan0: direct probe to 58:98:35:b8:01:71 (try 1/3)
[  962.048051] wlan0: direct probe to 58:98:35:b8:01:71 (try 2/3)
[  962.252005] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[  962.256815] wlan0: authenticated
[  962.260059] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[  962.263772] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[  962.263833] wlan0: associated
[ 1127.404898] wlan0: authenticate with 58:98:35:b8:01:71
[ 1127.410991] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 1127.412966] wlan0: authenticated
[ 1127.416506] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[ 1127.421802] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[ 1127.421839] wlan0: associated
[ 1426.725390] wlan0: authenticate with 58:98:35:b8:01:71
[ 1426.731655] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 1426.858783] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 1427.027666] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 1427.183274] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 1429.357536] wlan0: authenticate with 58:98:35:b8:01:71
[ 1429.363698] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 1429.442829] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 1429.575558] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 1429.677934] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 1432.357518] wlan0: authenticate with 58:98:35:b8:01:71
[ 1432.363648] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 1432.481767] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 1432.579257] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3
[ 1432.677064] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4683.758274] wlan0: authenticate with 58:98:35:b8:01:71
[ 4683.762579] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4683.764510] wlan0: authenticated
[ 4683.768696] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[ 4683.796729] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[ 4683.796764] wlan0: associated
[ 4719.776387] wlan0: authenticate with 58:98:35:b8:01:71
[ 4719.782837] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4719.897827] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 4720.007076] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 4720.147332] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4722.320458] wlan0: authenticate with 58:98:35:b8:01:71
[ 4722.326636] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4722.376139] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 4722.532406] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 4722.582485] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4725.260472] wlan0: authenticate with 58:98:35:b8:01:71
[ 4725.266735] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4725.385250] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 4725.503324] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 4725.623411] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4732.087366] wlan0: authenticate with 58:98:35:b8:01:71
[ 4732.097607] wlan0: direct probe to 58:98:35:b8:01:71 (try 1/3)
[ 4732.300153] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 4732.351870] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 4732.353978] wlan0: authenticated
[ 4732.356129] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[ 4732.371845] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[ 4732.371910] wlan0: associated
[ 4898.647682] wlan0: authenticate with 58:98:35:b8:01:71
[ 4898.653985] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4898.770942] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 4898.933142] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 4899.009722] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4901.191808] wlan0: authenticate with 58:98:35:b8:01:71
[ 4901.197932] wlan0: direct probe to 58:98:35:b8:01:71 (try 1/3)
[ 4901.399420] wlan0: direct probe to 58:98:35:b8:01:71 (try 2/3)
[ 4901.603433] wlan0: direct probe to 58:98:35:b8:01:71 (try 3/3)
[ 4901.807432] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 4904.487809] wlan0: authenticate with 58:98:35:b8:01:71
[ 4904.493946] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 4904.495905] wlan0: authenticated
[ 4904.499432] wlan0: associate with 58:98:35:b8:01:71 (try 1/3)
[ 4904.508959] wlan0: RX AssocResp from 58:98:35:b8:01:71 (capab=0x401 status=0 aid=8)
[ 4904.508998] wlan0: associated
[ 5107.603502] wlan0: authenticate with 58:98:35:b8:01:71
[ 5107.609649] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 5107.723706] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 5107.861117] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 5107.991178] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 5110.179493] wlan0: authenticate with 58:98:35:b8:01:71
[ 5110.185643] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 5110.304377] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 5110.443300] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 5110.559359] wlan0: authentication with 58:98:35:b8:01:71 timed out
[ 5113.239509] wlan0: authenticate with 58:98:35:b8:01:71
[ 5113.245620] wlan0: send auth to 58:98:35:b8:01:71 (try 1/3)
[ 5113.410013] wlan0: send auth to 58:98:35:b8:01:71 (try 2/3)
[ 5113.574703] wlan0: send auth to 58:98:35:b8:01:71 (try 3/3)
[ 5113.706298] wlan0: authentication with 58:98:35:b8:01:71 timed out





---

### Post by jeremy31 on 2015-01-15
I see low signal from the access point, only 20% and that is probably the issue.  You could try different channels on the router to see if one is better than another.  A network range extender is another idea unless there is a better antenna available for the atheros card

---

### Post by elwesthal on 2015-01-15
Thanks for answering. I never thought it could be that easy since my tabs, laptops and macs have full strenght standing next to this station? But maybe that new card simply sucks, i will look into it

---

### Post by wildmanne39 on 2015-01-15
Hi, it looks like you may have a driver parameter set for your card, that has worked well but not since 14.04, so I suggest you remove it then try to connect.
```
echo "options ath9k nohwcrypt=0" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
Edit: Make sure that your ethernet is unplugged because you are using the wrong driver for it and it will make your connection slow and network manager defaults to the ethernet connection when it is plugged in.
Thanks

---

### Post by elwesthal on 2015-01-16
Thanks for answering. I removed my options and added yours, didn't seem to help though. I also asked on the Fedora forum but didn't get any answers so I'm about to give up and go windows style with this new machine. Guess I'll just have to do my Linuxprogramming in virtualbox.

I don't think it's hardware related since I have 5 meters to the router and all the other machines work nice, guess it's the driver that hates my wifi card.
Added a new wireless file

---

### Post by wildmanne39 on 2015-01-16
Hi, I am out of town at the moment but can help on Sunday, if you will post the script from my signature that would be great, it is a little different and I am use to it so it is much easier for me to read and understand.

I use this driver without any issues in 14.04 with no parameters.

I will check in Sunday but someone else may have you going before then.
Thanks

---

### Post by jeremy31 on 2015-01-16
Does this card have external antennas and have you checked the connection?  It should do much better at 5 meters

---

### Post by elwesthal on 2015-01-17
Hi again, no there's no visible antennas on the PCI card. EDIT... of course, how stupid am I.. the guy haven't put the antennas on.....
So, here's what i did (for anyone else)


[LIST]
[*]Unplugg the ethernet cable since it had a faulty driver
[*]create ath9.conf (options ath9k nohwcrypt=0)
[*]attach those antennas... (ehhrmm..)
[/LIST]

Thanks for all the help!!

---

### Post by wildmanne39 on 2015-01-18
So this issue is solved correct?

---

