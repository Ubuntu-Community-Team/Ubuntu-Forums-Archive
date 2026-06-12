---
title: "Installing Ubuntu while preserving recovery partition"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Pas_sa on 2010-07-16
Hi folks,

I need to setup Ubuntu temporarily on a new Lenovo Thinkpad Edge - I'll only be using it for a week or two. When I'm done with it, I want to be able to remove Ubuntu and GRUB, leaving just the untouched, fresh Windows partition, and the Lenovo recovery partition.

I've tried using the Ubuntu installer - it tries to resize the 10GB recovery partition and install Ubuntu there. I presume this is because the 10GB partition is at the end of the HDD.

Is there any way I can easily temporarily install Ubuntu and then remove all traces of it without harming either the Windows partition or the recovery partition? Running Ubuntu off a USB stick is not an option, I'll be using it for at least a week.

Thanks :)

---

### Post by Ocxic on 2010-07-16
the recovery partition is separate from your windows partition, so jut don't delete that.
you can attempt to shrink your windows partition to make room for Ubuntu, BUT BACKUP your data, doing this does hove the potential to mess stuff up.

TIP: you can use the "dd" utility in ubuntu to backup your recovery partition to a file, then theres no worries.

---

### Post by QLee on 2010-07-16
[QUOTE=Pas_sa]...
Is there any way I can easily temporarily install Ubuntu and then remove all traces of it without harming either the Windows partition or the recovery partition? ...[/QUOTE]

This seems like one of the reasons for the creation of Wubi, it installs as a Windows application and can be uninstalled like other Windows applications.
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by mike555 on 2010-07-16
a week or two ? you could just run the cd live ,except not be able to save anything after reboot.

 perhaps a USB install , then you could have persistence.

---

### Post by da burger on 2010-07-16
Or a live cd (which is a touch easier to create) and the use a normal USB stick to store stuff.

---

### Post by Mark Phelps on 2010-07-17
> **Pas_sa said:**
> ... I've tried using the Ubuntu installer - it tries to resize the 10GB recovery partition and install Ubuntu there. 
Do NOT allow the Ubuntu installer to shrink partitions on a Win7 machine.  Doing so runs the risk of corrupting the Win7 partition and rendering it unbootable.  Since you obviously want to go back to using Win7, avoid doing this.

A wubi install will avoid the partitioning problem, but from the posts on here, comes with lots of other problems, not the least of which is the inability to boot into Ubuntu after install.

Agree heartily with the others in that, if you're only going to use if for a couple of weeks, do the LiveCD stuff.  Yeah, it's slow, but it's only going to be for a short while.

---

### Post by QLee on 2010-07-17
[QUOTE=Mark Phelps]...
A wubi install will avoid the partitioning problem, but from the posts on here, comes with lots of other problems, not the least of which is the inability to boot into Ubuntu after install.
[/QUOTE]

Mark , the way you have worded this statement makes it seem as if Wubi doesn't work at all. I think that would surprise the Wubi developers. Naturally, on a help forum there will be requests for help, and very few kudos from those who aren't having any problems. If you have evidence that Wubi doesn't work in any specific situations please inform us or file a bug report. I certainly can't guarantee that the OP won't have any problems, and I know you know that many problems eventually work out to something the user has (or hasn't) done correctly. Using a system, for evaluation, without making any changes to it is the stated mission of Wubi. And, Wubi is officially supported by Ubuntu.

---

### Post by Mark Phelps on 2010-07-17
> **QLee said:**
> Mark , the way you have worded this statement makes it seem as if Wubi doesn't work at all.
Sorry, that was not my intent.
> If you have evidence that Wubi doesn't work in any specific situations please inform us or file a bug report.
Read these forums.  There are plenty of posts where folks have installed Wubi, and afterward, can't boot their systems anymore.  You're telling me that I have to track these down for you now?
> And, Wubi is officially supported by Ubuntu.
Given that the "current" Wubi Guide STILL refers to Ubuntu 8.04,so much for official "support". That doesn't give ME confidence in trying something out when the documentation is two years old.

Look, I've been watching Wubi on these forums, and, ever since Win7 came out, there has been a large increase in the posts where folks installed Wubi and ended up with boot problems.  And, OK, that's probably NOT the fault of the "Wubi developers".  

But, to a new person, it doesn't much matter to them WHY they can't boot into Ubuntu -- and it leaves a bad taste in their mouth for what is their first, and most probably ONLY, experience with Ubuntu.

So, maybe instead of attacking me for daring to say something unkind about yet another of the Linux "sacred cows", you should go after the "official Wubi support" folks to update their documentation, and to fix the problems that STILL keep cropping up in Windows7/Wubi installations.

---

### Post by wahoobob on 2010-08-06
I have done this by making a system image with the windows 7 backup software and then installing ubuntu wubi.  If there is a problem with the boot, I can return to the system from the image and no harm has been done.

---

