---
title: "IPW2200 not showing up after following howto"
date: 2005-11-06
forum: Networking &amp; Wireless
---

### Post by skmassey on 2005-11-06
I followed the howto [here]("http://ubuntuforums.org/showthread.php?t=26623") and now my wireless card isn't being detected at all.  my dmesg is:

```
otto@Lappy64:/$ dmesg | grep ipw
[   44.732864] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[   44.732869] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[   44.732984] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[   44.732987] ipw2200: Unknown symbol ieee80211_wx_set_encode
[   44.733023] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[   44.733026] ipw2200: Unknown symbol ieee80211_wx_get_encode
[   44.733126] ipw2200: disagrees about version of symbol ieee80211_txb_free
[   44.733129] ipw2200: Unknown symbol ieee80211_txb_free
[   44.733265] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[   44.733269] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[   44.733324] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[   44.733328] ipw2200: Unknown symbol ieee80211_wx_get_scan
[   44.733398] ipw2200: Unknown symbol escape_essid
[   44.733619] ipw2200: disagrees about version of symbol ieee80211_rx
[   44.733622] ipw2200: Unknown symbol ieee80211_rx
[   44.734012] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[   44.734016] ipw2200: Unknown symbol ieee80211_rx_mgt

```

It showed up before I did the howto but it wouldn't show any wireless networks when I scanned even though I know I was in range of a wifi hotspot.

---

### Post by audax321 on 2005-11-06
Just a suggestion that may not be practical or work for you, but if you can try upgrading to Breezy. I'm not sure if you need wpa or not, but the 2200 worked right away for me with Breezy. I used a 2915 under Hoary and took me a good two days to get it working because it has some old driver for the card. The only problem I ran into under Breezy was related to transferring large files and there was a fix that worked for me posted here (a little bit down on the first page by xMetaRidley):

[http://ubuntuforums.org/showthread.php?t=75612](http://ubuntuforums.org/showthread.php?t=75612)

Actually it might not be a bad idea to give that fix a try... you never know. :)

EDIT: Just noticed you did post this in the Breezy forum, so you already have it :)

---

### Post by skmassey on 2005-11-06
Yeah, I am running breezy 5.10.  I know the HowTo is written for Hoary, but I assumed it would work.  The card "worked" before, meaning that it showed up under ifconfig, lspci, and iwconfig (showed network extensions) but it wouldn't associate with any access points.  Now it dosen't do any of that.  I guess I need to roll back to before I installed all that, problem is, I don't exactly know how...  I'm still quite a noob and i've been wrestling with trying to get wireless internet for over a month now.  Problem is, I have no wired connection because I live on a campus that is all wireless with no wired connections for students. Period.  So it has been relatively hard for me to go about installing packages I need and what not.  Thanks for the suggestions though :) .

---

### Post by skmassey on 2005-11-06
Hmm... I've now encountered another error that might have some bering on the situation.  I tried the fix noted in the post by audax321, and upon trying to reload the driver I get the error:
```
otto@Lappy64:/$ sudo modprobe ipw2200 hwcrypto=0
WARNING: Error inserting ieee80211 (/lib/modules/2.6.12-9-amd64-generic/net/ieee80211/ieee80211.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ipw2200 (/lib/modules/2.6.12-9-amd64-generic/kernel/drivers/net/wireless/ipw2200.ko): Unknown symbol in module, or unknown parameter (see dmesg)
otto@Lappy64:/$

```
and my dmesg appears as:
```
*** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1006.686113] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1006.686120]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1021.686950]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1021.686960] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1021.686967]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1036.687703]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1036.687712] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1036.687719]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1051.688879]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1051.688889] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1051.688896]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1066.689317]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1066.689326] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1066.689333]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1081.690192]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1081.690202] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1081.690216]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1096.690929]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1096.690938] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1096.690945]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1111.691780]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1111.691789] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1111.691797]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1126.899052]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1126.899063] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1126.899071]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1144.214673]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1144.214683] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1144.214691]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1159.727873]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1159.727883] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1159.727891]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1174.728342]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1174.728353] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1174.728361]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1190.741398]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1190.741415] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1190.741423]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1205.742209]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1205.742219] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1205.742228]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1220.743014]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1220.743024] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1220.743033]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1235.749032]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1235.749043] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1235.749051]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1250.749159]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1250.749169] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1250.749177]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1265.750098]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1265.750108] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1265.750116]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1280.750707]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1280.750717] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1280.750725]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1295.751495]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1295.751505] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1295.751513]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1310.752738]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1310.752749] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1310.752757]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1325.753096]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1325.753106] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1325.753114]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1341.375429]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1341.375441] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1341.375449]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1356.269151]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1356.269162] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1356.269170]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1371.270303]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1371.270313] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1371.270321]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1383.893085] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[ 1383.893092] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[ 1383.893213] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[ 1383.893217] ipw2200: Unknown symbol ieee80211_wx_set_encode
[ 1383.893257] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[ 1383.893261] ipw2200: Unknown symbol ieee80211_wx_get_encode
[ 1383.893364] ipw2200: disagrees about version of symbol ieee80211_txb_free
[ 1383.893368] ipw2200: Unknown symbol ieee80211_txb_free
[ 1383.893510] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[ 1383.893520] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[ 1383.893577] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[ 1383.893581] ipw2200: Unknown symbol ieee80211_wx_get_scan
[ 1383.893635] ipw2200: Unknown symbol escape_essid
[ 1383.893850] ipw2200: disagrees about version of symbol ieee80211_rx
[ 1383.893853] ipw2200: Unknown symbol ieee80211_rx
[ 1383.894252] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[ 1383.894256] ipw2200: Unknown symbol ieee80211_rx_mgt
[ 1386.272057]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1386.272067] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1386.272075]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1401.272052]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1401.272063] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1401.272071]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1416.273173]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1416.273184] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1416.273192]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1431.274007]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1431.274018] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1431.274026]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1446.275170]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1446.275180] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1446.275188]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1461.275263]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1461.275273] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1461.275281]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1477.280207]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1477.280218] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1477.280226]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1492.785816]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1492.785826] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1492.785834]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1498.974815] ieee80211_crypt: unregistered algorithm 'NULL' (deinit)
[ 1504.393248] ieee80211_crypt: registered algorithm 'NULL'
[ 1504.395600] ieee80211: disagrees about version of symbol ieee80211_get_crypto_ops
[ 1504.395607] ieee80211: Unknown symbol ieee80211_get_crypto_ops
[ 1504.395641] ieee80211: disagrees about version of symbol ieee80211_crypt_deinit_entries
[ 1504.395646] ieee80211: Unknown symbol ieee80211_crypt_deinit_entries
[ 1504.395699] ieee80211: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[ 1504.395704] ieee80211: Unknown symbol ieee80211_crypt_delayed_deinit
[ 1504.396069] ieee80211: disagrees about version of symbol ieee80211_crypt_quiescing
[ 1504.396073] ieee80211: Unknown symbol ieee80211_crypt_quiescing
[ 1504.422515] ieee80211: 802.11 data/management/control stack, 1.0.3
[ 1504.422521] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[ 1504.444127] ipw2200: disagrees about version of symbol ieee80211_get_crypto_ops
[ 1504.444134] ipw2200: Unknown symbol ieee80211_get_crypto_ops
[ 1504.444249] ipw2200: disagrees about version of symbol ieee80211_wx_set_encode
[ 1504.444254] ipw2200: Unknown symbol ieee80211_wx_set_encode
[ 1504.444290] ipw2200: disagrees about version of symbol ieee80211_wx_get_encode
[ 1504.444295] ipw2200: Unknown symbol ieee80211_wx_get_encode
[ 1504.444395] ipw2200: disagrees about version of symbol ieee80211_txb_free
[ 1504.444399] ipw2200: Unknown symbol ieee80211_txb_free
[ 1504.444542] ipw2200: disagrees about version of symbol ieee80211_crypt_delayed_deinit
[ 1504.444546] ipw2200: Unknown symbol ieee80211_crypt_delayed_deinit
[ 1504.444600] ipw2200: disagrees about version of symbol ieee80211_wx_get_scan
[ 1504.444604] ipw2200: Unknown symbol ieee80211_wx_get_scan
[ 1504.444663] ipw2200: Unknown symbol escape_essid
[ 1504.444875] ipw2200: disagrees about version of symbol ieee80211_rx
[ 1504.444878] ipw2200: Unknown symbol ieee80211_rx
[ 1504.445274] ipw2200: disagrees about version of symbol ieee80211_rx_mgt
[ 1504.445278] ipw2200: Unknown symbol ieee80211_rx_mgt
[ 1507.786814]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1507.786825] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1507.786833]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1523.289212]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1523.289228] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1523.289236]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1538.290256]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1538.290266] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1538.290274]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1553.291456]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1553.291467] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1553.291475]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1568.292024]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1568.292034] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1568.292042]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1583.292634]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1583.292645] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1583.292652]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1598.293404]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1598.293414] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1598.293422]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
[ 1613.294524]     ACPI-0362: *** Error: Looking up [Z007] in namespace, AE_NOT_FOUND
[ 1613.294540] search_node ffff81001ac52e00 start_node ffff81001ac52e00 return_node 0000000000000000
[ 1613.294548]     ACPI-0508: *** Error: Method execution failed [\_SB_.BAT1._BST] (Node ffff81001ac52c00), AE_NOT_FOUND
otto@Lappy64:/$
```

yeah... for some reason this laptop spews an obscene number of ACPI errors... it's something I need to get around to fixing but It would be nice to have an internet connection first.  Maybe this will help narrowing down a problem.

---

### Post by skmassey on 2005-11-06
I followed the fix [here]("http://ubuntuforums.org/showthread.php?t=75612") and uninstalled the stuff I installed from the HowTo linked above and when I restarted, everything worked and it picked up my wireless network.

---

