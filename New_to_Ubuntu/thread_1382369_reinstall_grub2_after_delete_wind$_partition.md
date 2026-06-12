---
title: "reinstall grub2 after delete wind$ partition ??"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by thrvers on 2010-01-15
My friend install dual OS = ubuntu & wind$, but now he like ubuntu then ask me that he want delete wind$ partition then merge to ubuntu partition without reinstall ubuntu, because many data on his HDD.
How to doing that after edit partition using gparted ??

PS: using ubuntu 9.10 (grub2)

THX
-rezzz-

---

### Post by Sef on 2010-01-15
Your friend needs to **back up** that data.   There is no guarantee that whatever is done will not require a reinstall.

---

### Post by bcn17 on 2010-01-15
gparted will work fine. It's not hard, just click the windows part of the histogram of your harddrive. Right click. Delete, remove or w/e. Then click apply. It should then be listed as unpartitioned space. 

> **Sef said:**
> Your friend needs to **back up** that data.   There is no guarantee that whatever is done will not require a reinstall.

This is very important. Any time you are changing the size of a partition with data on it there is a risk of data loss. I don't know the risk. I have always backed up data. deleted and resized, then did fresh installs.

---

### Post by JC Cheloven on 2010-01-15
> **Sef said:**
> Your friend needs to **back up** that data.   There is no guarantee that whatever is done will not require a reinstall.
+1

But you can give it a try quite confidently. Don't forget to backup, don't blame anyone if something goes wrong (managing partitions is always risky). The steps involved would be:

- Backup the critical data.
- Start form livecd. Run gparted.
- Select the windows partition. Delete it. 
- Apply changes.
- Select the ubuntu partition. Extend it (by dragging its edge) to the free space created before.
- Apply changes (this can take a long time).

You're done. Restart your system and see how was it.

---

### Post by thrvers on 2010-01-15
THX for gparted, then howto rewrite grub2 ??

Information on his partition **maybe** change look like this
before:
- /dev/sda1 wind$
- /dev/sda2 ubuntu
- /dev/sda3 swap

after:
- /dev/sda1 ubuntu
- /dev/sda2 swap

howto fix that on grub2 ??

-rezzz-

---

### Post by JC Cheloven on 2010-01-15
> **thrvers said:**
> THX for gparted, then howto rewrite grub2 ??

Information on his partition **maybe** change look like this
before:
- /dev/sda1 wind$
- /dev/sda2 ubuntu
- /dev/sda3 swap

after:
- /dev/sda1 ubuntu
- /dev/sda2 swap

howto fix that on grub2 ??

-rezzz-

I don't think so. I think you will rather get
- /dev/sda2 ubuntu
- /dev/sda3 swap

And I'm not 100% sure, but I don't see a reason for grub to stop working. The xp entry will remain, and point nowhere, but that's all. The command
```
sudo update-grub2
``` should fix it.

---

### Post by thrvers on 2010-01-16
thx for replay, i'll inform you later about result.

-rezzz-

---

### Post by thrvers on 2010-01-18
Sorry for late replay, my friend can not wait to recovery and a lot of errors so he reinstall ubuntu.

THX all
-rezzz-

---

