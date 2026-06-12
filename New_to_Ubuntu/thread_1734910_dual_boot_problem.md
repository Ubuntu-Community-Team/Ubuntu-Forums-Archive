---
title: "dual boot problem"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by Autodave on 2011-04-20
I already have Ubuntu 10.10 installed on my drive.  Is it possible to install Window Vista now w/o wiping the drive clean first?

---

### Post by ttshivers on 2011-04-20
It is much easier to first install windows, then install Ubuntu, but you can still do it the other way around.

These two articles might help you [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"), [https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")

---

### Post by oldfred on 2011-04-20
Windows will only install to a NTFS primary partition (sda1 thru sda4) that has the boot flag (active partition in windows). You can format and set flags on the partition with gparted from a Ubuntu liveCD.

---

