---
title: "Duel booting W7 and UNR"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by DanPiazza on 2011-01-14
I had UNR 10.10 installed just fine, but once I installed W7 (64-bit) on a second partition, it destroyed the bootloader for UNR. I tried EasyBCD, but it didn't help (maybe I just did it wrong...). Does anyone have any advice for creating a duel boot menu on boot for thesr two OS'?

Edit: I used one of the beta builds for EasyBCD 2.1 and it worked fine with Grub2 and installing the W7 bootloader on the MBR.

---

### Post by wilee-nilee on 2011-01-14
We can reload the grub bootlader. easybcd should have worked, though. post the output of this command run from a live Ubuntu cd.
sudo fdisk -lu

---

### Post by DanPiazza on 2011-01-14
Unfortunately I'm on a netbook and don't current;y have a USB stick to create a live boot on. I should be able to create one tomorrow using a friend's. I'll report back once I do so.

---

