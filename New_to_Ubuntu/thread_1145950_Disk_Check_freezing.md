---
title: "Disk Check freezing"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by Geoffbaker on 2009-05-02
Hi
After booting normally for some weeks I now have a message saying routine check of hard disk. Unfortunately it gets to 48% then freezes. No error messages or any way past that I can find. Help would be appreciated. I can get past by pressing escape and skipping check and all seems to be working normally then but it means I have to keep a watchful eye on the boot..
Cheers
Geoff

---

### Post by Herman on 2009-05-02
There are all kinds of different flavors of file system checks that we can use.

The one that is run at boot-up was [SIZE=-1][FONT=Bitstream Vera Sans Mono]fsck -C -R -A -a [/FONT][/SIZE]the last time I checked, which means that fsck walks through the operating system's /etc/fstab file and runs whatever generic file system check is appropriate and safe for each file system in the list. That means if you have an ext* file system, fsck will run e2fsck for you.
Generally, it's best to wait for a file system check to complete, even if it appears frozen. It may be doing something that takes a long time.

Fortunately, you are also able to run e2fsck yourself, manually. I prefer to do so from a Live CD. When you run e2fsck manually, you can set your own options so it's more likely to be effective and it gives you feedback if there's something else that needs to be done. 
A good command to begin with is something like,
```
sudo e2fsck -C0 -p -f -v /dev/sda2
```Where: your ext* file system is in partition /dev/sda2, check with a partition editor to make sure.

If you're not too keen on using the command line, you can open Gnome Partition Editor in your Ubuntu Live CD and right-click on the partition to be checked and click 'check'.
Then click 'apply', and 'apply' again, and wait a few minutes. When the file system check has finished, you can click on the arrows for the drop-down boxes which will tell you what commands GParted ran for you and show you the results. GParted runs e2fsck with fairly effective options and it should be able top fix most file system problems for you.

Either of those two file system checks are probably able to clear up whatever problem your regular fsck at boot-up is stopping at.

---

### Post by Geoffbaker on 2009-05-02
Thanks for the info.
I will give it a go.
Cheers
Geoff

---

