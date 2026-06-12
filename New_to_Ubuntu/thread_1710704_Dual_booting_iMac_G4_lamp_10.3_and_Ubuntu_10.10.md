---
title: "Dual booting iMac G4 lamp 10.3 and Ubuntu 10.10"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by Cliffton on 2011-03-20
Hello All...
I wanted to share my success at finally getting my iMac to dual boot with Ubuntu 10.10. Here are the steps I used.

1. Back-up all wanting files from your iMac.
2. Startup Mac with MacOS System install disc.
3. Open Disc Utility from top menu.
4. Partition disc into 4 partions -- remember this will erase HD.
5. Make two small partitions -- I made mine about 1GB each.
6. Make two larger partitions -- one for MacOS, one for Ubuntu.
7. Go back to Mac installer and install MacOS onto appropriate       partition
8. Finish install and make sure Mac boots properly.
9. Start up computer with Ubuntu disc by rebooting and holding down "c" key.
10. Install Ubuntu from desktop icon.
11. Follow all instructions, choose manual set-up when deciding where/how to install ("Use entire disc, or manual set-up").
12. Use one small partition as swap space, and one as New World bootloader.
13. Use remaining partition for Ubuntu.

After struggling with different set-ups, this is the one that worked for me with no extra configuration needed. Ubuntu works great and I almost decided to have it as the sole OS on my iMac, but thought I'd leave the MacOS on for nostalgia sake.

---

