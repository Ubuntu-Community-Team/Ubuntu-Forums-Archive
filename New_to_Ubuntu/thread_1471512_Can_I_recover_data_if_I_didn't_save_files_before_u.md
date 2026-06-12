---
title: "Can I recover data if I didn't save files before using recovery cd?"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by nasreensaleem on 2010-05-03
My computer was not booting yesterday, it was going in a loop again and again, and I tried safe mode and all, finally I had a recovery cd, and my husband also, didnt save anything, just wanted to boot up the computer, so he used the recovery cd without saving anything( I did not know about saving before). Now computer starts, but my old files and everything gone, but used space is still like before. But I do not see my files, document, pictures anymore. And when I scanned my computer with antiviral, it was scanning through some old known files, but they are not showing up anywhere.
 
Can ubuntu software help me recover those files?
 
If not, what kind of software do I need?
 
Thank you.

---

### Post by cariboo on 2010-05-03
Are you actually using Ubuntu? Your problem sounds more like something that would happen in Windows. You can use something like [this]("http://ubuntu-rescue-remix.org/Download"), to try and restore your missing files .

---

### Post by nasreensaleem on 2010-05-03
Thank [EMAIL="you@cariboo"]you@cariboo[/EMAIL], no I never used ubunto, after searching several places, it sounded like a recovery file so I was downloading it right now. I will try linux, I will let you know what happens, or if you have any other suggestion. Is linux free?

---

### Post by aysiu on 2010-05-03
Linux is free, and you can use it to recover deleted files.

Instructions (with screenshots) here:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by spydeyrch on 2010-05-03
> **nasreensaleem said:**
> My computer was not booting yesterday, it was going in a loop again and again, and I tried safe mode and all, finally I had a recovery cd, and my husband also, didnt save anything, just wanted to boot up the computer, so he used the recovery cd without saving anything( I did not know about saving before). Now computer starts, but my old files and everything gone, but used space is still like before. But I do not see my files, document, pictures anymore. And when I scanned my computer with antiviral, it was scanning through some old known files, but they are not showing up anywhere.
 
Can ubuntu software help me recover those files?
 
If not, what kind of software do I need?
 
Thank you.


It sounds to me like your husband installed windows over your old windows install. It sounds to me like your old windows drive was never formated and wiped clean. 

When you install windows on top of an already installed windows. The new installation will take your old windows and place it in it's very own directory within the new windows. Typically it is called something like "Windows Old" or "Old windows" and it is usally on the root of your C:\. If you virus scanner was finding old files that you can't seem to find, then that is what most likely happened. to get to those old files, you need to find that "old windows" directory.

Also, what version of windows is the new one and what version was the old one? Thanks! :D

-Spydey :KS

P.S. You can use ubuntu to locate those old files, if in fact the situation is as I think that it is, or you can just boot into your newly installed windows and go from there. It will actually probably be easier to do it from within windows. Just my opinion.

---

### Post by nasreensaleem on 2010-05-03
spydeyreck, you are right! Oh my goodness, you are a genius! I found some of them, I am hopeful I will found them all, in " My old document". I slept only 3/4 hours, and my husband is gone to office, I am trying to figure all this out, and I am not good at all at this. I really found old files. Its window xp, both versions are same, but I had updated window in the previous setting, but the recovery cd my husband used didnt have new versions of window,everything went to a primitive look, and one of my typed project is not in window word, its in note pad. Thank you everyone, for helping. I am saved!

---

### Post by spydeyrch on 2010-05-03
> **nasreensaleem said:**
> spydeyreck, you are right! Oh my goodness, you are a genius! I found some of them, I am hopeful I will found them all, in " My old document". I slept only 3/4 hours, and my husband is gone to office, I am trying to figure all this out, and I am not good at all at this. I really found old files. Its window xp, both versions are same, but I had updated window in the previous setting, but the recovery cd my husband used didnt have new versions of window,everything went to a primitive look, and one of my typed project is not in window word, its in note pad. Thank you everyone, for helping. I am saved!

Awesome! I am glad that it worked out for you. You should also probably tell your husband thank you for not formatting your windows drive as that would have gotten rid of your files and made it a very painful process to recover them.

If I may add my two bits, I would recommend that you do a few things, and not necessarily in this order but they are good points to take into account:

1) Backup your files on a regular basis. I back mine up once a week via an automatic program. I just had to initially set it up the first time and let it go from there. External HDD are very cheap these days and the price to storage amount vs. loss of everything well justifies getting a good sized external HDD (hard disk drive).

2) Once you have backed up your files to your external drive, then either do one of these: a.) reinstall windows but do what we call a fresh install. This will wipe your hard drive, making it clean of any leftover files, and then install a fresh copy of windows; or b.) after backing up your files, install ubuntu; or c.) after backing up your files do a dual boot configuration: both windows and ubuntu.

By leaving your "old" windows" directory on your HDD, you have, in essence, two OSs (Operating Systems) taking up space but can only use one of them. If you just get rid of the "old windows", obviously after saving your files, you will run into issues down the road.

Also, if you would like some help doing any of the above and more if needs be, come back here and ask. Hopefully you will be willing to try ubuntu, even if it is via WUBI. You never know. :D

One last thing, are there any other issues that you currently have with our system that you need addressed? Just asking. :)

-Spydey :popcorn:

---

