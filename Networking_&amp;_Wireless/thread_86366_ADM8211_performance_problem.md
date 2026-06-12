---
title: "ADM8211 performance problem"
date: 2005-11-04
forum: Networking &amp; Wireless
---

### Post by Burkey on 2005-11-04
I have an ADMTek 8211 based PCI card in my Athlon64, the adm8211 kernel module is loaded and working, BUT it has shocking performance and frequently I see my signal go to 0 and then bounce back up...

dmesg shows..
```

[ 1865.365472] eth2: RX deauthentication from 00:12:17:32:77:fa (reason=7)
[ 1865.431094] eth2: authenticate with AP 00:12:17:32:77:fa CHAN=11
[ 1865.431098] eth2: TX authentication (alg=1 transaction=1)
[ 1865.444046] eth2: RX authentication (alg=1 transaction=2 status=0 Success)
[ 1865.444053] eth2: TX authentication (alg=1 transaction=3)
[ 1865.445624] eth2: RX authentication (alg=1 transaction=4 status=0 Success)
[ 1865.445628] eth2: authenticated
[ 1865.445631] eth2: associate with AP 00:12:17:32:77:fa
[ 1865.445634] eth2: TX AssocReq (capab=0x11)
[ 1865.447266] eth2: RX AssocResp (capab=0x11 aid=3 status=0 Success)
[ 1865.447270] eth2: associated

```

This is a repeating process and it is not only frustrating but stops things like World of Warcraft from being playable at all.

Has anyone seen this before or have any hints?

A little about my PC..

Ubuntu Breezy 5.10
```

Linux wraith 2.6.12-9-amd64-generic #1 Mon Oct 10 13:27:39 BST 2005 x86_64 GNU/Linux

```

please help, driving me crazy.

---

