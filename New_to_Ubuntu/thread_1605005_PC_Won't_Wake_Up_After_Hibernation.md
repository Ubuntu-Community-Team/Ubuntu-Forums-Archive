---
title: "PC Won't Wake Up After Hibernation"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by freedombono on 2010-10-24
Hi everyone, this is my first post here, but in the two weeks I've had  Ubuntu installed I've been helped immensely by past threads here.  However, this time I can't find anything that will help me in the  archives, so I figured it was time to post.

I shut down my netbook with hibernate, and on restart, after I select to boot from Ubuntu, I don't enter into Linux at all, and get a black and white command-line type screen saying

mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have requested /sbin/init.
No init found. Try passing init= boot arg.

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


Help?

EDIT: If I choose to boot into windows instead of Ubuntu, everything proceeds normally and I can use it without any problems (well, anymore than usual for Windows anyway ;) ).

---

### Post by SuaSwe on 2010-10-24
Hi there freedombono!

Unfortunately, some computers just have issues with hibernation - should this apply to yours, your best bet would be to file a bug report to Launchpad (have a look here for further details: [https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html](https://help.ubuntu.com/9.10/hardware/C/pm-suspending.html)).

What PC model are you using?

---

### Post by freedombono on 2010-10-25
Thanks for the reply.

Unfortunately, I can't do what the link suggested because I cannot boot into Linux, and even when booting from a live disk I cannot access my partition.

I have a Compaq Mini 110 with an Intel Atom 1.6 GHz and 1GB of RAM.

I really don't want to lose the stuff in my linux partition, otherwise I'd just reinstall. :x

Can anyone please help me?

---

