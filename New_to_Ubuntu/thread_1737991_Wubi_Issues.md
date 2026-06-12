---
title: "Wubi Issues"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by h1123 on 2011-04-24
Good Afternoon Guys,

Quick question, and hopefully a solution, when watching videos on WUBI, ie from Youtube or Hulu, why does the system space diminish and How can I get this space back, ie by deleting files after having watched a show?

---

### Post by sffvba[e0rt on 2011-04-24
This is not a WUBI issue... your browser cache's files from the net... run clean-up and you will be good to go :)


404

---

### Post by Rubi1200 on 2011-04-24
The maximum size of a default Wubi install is 30GB, so space would probably run out quite quickly with videos.

Go to Applications > Accessories > Terminal and post the results of the following command:

```
df -H
```This will tell us how much space was originally given and how much is currently left.

EDIT: good point made there by not found and you can do that too. The command I gave will help us determine if you can allocate more space for the Wubi install so please also tell us how large the Windows partition is as well.

---

### Post by h1123 on 2011-04-24
Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0             4.9G   4.2G   483M  90% /
udev                   1.6G   304k   1.6G   1% /dev
none                   1.6G   1.3M   1.6G   1% /dev/shm
none                   1.6G   230k   1.6G   1% /var/run
none                   1.6G      0   1.6G   0% /var/lock
none                   1.6G      0   1.6G   0% /lib/init/rw
/dev/sda1              251G   115G   136G  46% /host
none                   4.9G   4.2G   483M  90% /var/lib/ureadahead/debugfs

Yeah I thought I'd assigned far more than that, is there no way of increasing it, because my Vista has been playing up major(I already switched back from full Ubuntu once) so I can't really remove wubi and then re-install it with a bigger alloted HDD Space

---

### Post by Rubi1200 on 2011-04-24
> **h1123 said:**
> Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0             4.9G   4.2G   483M  90% /
udev                   1.6G   304k   1.6G   1% /dev
none                   1.6G   1.3M   1.6G   1% /dev/shm
none                   1.6G   230k   1.6G   1% /var/run
none                   1.6G      0   1.6G   0% /var/lock
none                   1.6G      0   1.6G   0% /lib/init/rw
/dev/sda1              251G   115G   136G  46% /host
none                   4.9G   4.2G   483M  90% /var/lib/ureadahead/debugfs

Yeah I thought I'd assigned far more than that, is there no way of increasing it, because my Vista has been playing up major(I already switched back from full Ubuntu once) so I can't really remove wubi and then re-install it with a bigger alloted HDD Space
Yes, 4.9GB is not much at all and, as you see, it is already 90% full. The Windows install is only 46% full, so you have room to play with.

This link explains how to resize the root.disk to gain more space (post # 2):
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371)

---

### Post by Paddy Landau on 2011-04-24
I want to add a caution. WUBI is excellent for playing around and testing whether you like Ubuntu. But it is unreliable and subject to sudden inexplicable failure.

Please do not rely on WUBI for long-term use, and back up any data regularly.

If you wish to use Ubuntu long-term, uninstall WUBI and then install Ubuntu.

---

### Post by bcbc on 2011-04-24
Although I think Paddy is being a little dramatic (just the bit about 'sudden and inexplicable failure' ;) ), the fact is that wubi is relying on the ntfs file system to host it's virtual disk. The only way to fix an ntfs file system if it becomes corrupted is to run chkdsk from windows (or a windows repair prompt). So if your vista is unreliable and/or failing, then you could lose the ability to boot Ubuntu.

How can file system corruption occur? Any hard poweroff (or power failure if it's a desktop) can result in corruption. Resist the urge to power off if something hangs - usually Alt+SysRq R-E-I-S-U-B will get it restarted.

Note also that wubi uses a virtual disk that is a single file - therefore if corruption occurs, it can result in the loss of the virtual disk. It doesn't happen all that frequently - and often it's recoverable (from Windows) - but I have seen cases where it isn't. So the comment regarding backups is important.

The good news is you can migrate your current wubi install to a full install: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Or backup, uninstall, reinstall.

---

### Post by Paddy Landau on 2011-04-25
> **bcbc said:**
> Although I think Paddy is being a little dramatic (just the bit about 'sudden and inexplicable failure' ;) )
LOL :lol:. It's happened to me and to several other people on this forum. Not dramatic at all, just real life! (Yes, it happens to other systems, too, sometimes because of hardware failures, but Wubi seems more susceptible to it.)

---

