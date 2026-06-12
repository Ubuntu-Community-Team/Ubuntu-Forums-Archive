---
title: "Migrating wubi install to own partition"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by AliSajidImami on 2009-11-03
Hello, guys.
The thing is, i'm going to try to migrate my wubi install to a dedicated ubuntu installation. I'll be using LVPM as it appears to be the thing.
Throughout the process, i'll be posting updates here.

First, my configuration
Processor: Intel Pentium D 3.20 GHz
Hard disk: 320 GB internal
Ram: 2 GB
3D card: Nvidia 7300 FX

Now, this guide will mostly contain information from a newbie level as i am one myself. For the veterans, i have some questions.
1. What settings should be backed up before such a step is taken? Is it okay to just copy the *home* folder?
2. Is there some process to catalogue all the softwares currently installed and use it to make the exact configuration on a fresh [SIZE=1]install?[/SIZE] I'm asking this for if anything goes wrong and i end up losing everything.
3. If i create a root partition now, do the migration, and then i increase the root and swap partition size, will it cause problems?

That's all for now. Check back for further updates.

All your suggestions, comments and ideas are welcome.

[B][SIZE=4]Process:
[/SIZE][/B][SIZE=4][SIZE=1]1. Downloaded lubi, LVPM and the partitioning tool.
2. Posted this post.
3. Currently Waiting.
4. Used UNetbootin, on bootup and made partition for my ubuntu install
5. Formatted the partition.
6. Rebooted into ubuntu wubi install
7. Installed lvpm.
8. Used the lvpm Transfer option, selected the newly created partitions to move to.
9. Waiting.
10. with the transfer done, rebooted to start my install.

Nothing has happened.

***[COLOR=Red]This attempt was a FAILURE[/COLOR]***
[/SIZE][/SIZE]

---

### Post by AliSajidImami on 2009-11-03
I have installed the UNetBootin.
Now i'm going to reboot and repartition.

---

### Post by AliSajidImami on 2009-11-03
So far so good.
I've repartitioned. i have screenshot and a log which i'll post in the end.
Next, comes the installation of LVPM itself that i'm doing now.
I'm also burnong Super GRUB DIsk.

---

### Post by AliSajidImami on 2009-11-03
Okay, i installed LVPM, opened it, selected "TRANSFER" option. Then i selected the partitions i had just created. The setup is now transferring. And it says it'll take an hour or so.
Fingers crossed.

---

### Post by AliSajidImami on 2009-11-03
All right. it did what it was supposed to do.
But when i rebooted, it still showed the screen like i was running wubi.
on the next menu, i chose the last optio, which said "ubuntu-on-hda11" which was where i had migrated it, and it said that no such partiotion exists.
I'm trying to figure out what went wrong.
Any Ideas?

---

### Post by leorolla on 2009-11-10
What is the last new?

Did you try booting with your SGD?

---

### Post by AliSajidImami on 2009-11-22
I tried rebooting with SGD, but it didn't detect the partition. I booted again, and apparently logged in to my new hard disk partition. I uninstalled wubi, and BAM! my installation was gone. i was left without my data.
:-(
I'm going to update the first post.

---

### Post by leorolla on 2009-11-23
Why did you uninstall Wubi ?!

Anyway, it may be that your data is not lost.

If you boot from a Live USB, can't you see the Linux partition?

---

