---
title: "[SOLVED] Clean Installed Intrepid:  AR5212 in ThinkPad R61i Now Constantly Dropping C"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by AlphaMack on 2008-10-31
As the title says I clean installed my root partition from Hardy to Intrepid on my R61i.  Network Manager connects to my WAP without problems.  Unfortunately, if I walk away and the screen goes dim, the connection is dropped and I'm prompted to enter my WAP's password (which is already saved).  This always appears in dmesg when the connection drops:

```

[13331.771381] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[13500.442776] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[13500.451694] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[15708.813624] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[16517.195123] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[16517.690060] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[17905.820167] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready

```

I have a built-in AR5212 card using ath_pci.

This is very annoying especially since I'm still trying to download all of my desired packages and connection speeds are already as slow as they are from the upgrade frenzy.

I never had this problem in either Gutsy or Hardy.

I haven't had a chance to upgrade existing packages yet, so I'm hoping that this bug has been squashed.

---

### Post by AlphaMack on 2008-10-31
I just noticed that in Users and Groups, a lot of items under Privileges were unchecked - one of them being "Connect to wireless and ethernet networks."  I checked everything under my account.  This has to be some sort of bug because under Hardy I recall that all privileges were checked.

I'm crossing my fingers that this solves the issue, short of the kernel upgrade waiting in the wings.  (Still trying to download all of my packages at the moment.)

---

### Post by AlphaMack on 2008-11-01
Installing linux-backport-modules seems to have fixed the issue for now.  My guess is that it is some sort of regression with NM and the Atheros drivers.

Edit:  Scratch that...after rebooting it started repeatedly dropping again.  I ditched NM for Wicd and I haven't had ANY drops since.

---

