---
title: "reverting from 11.04 back to 10.10"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by skypuppy on 2011-05-14
I'm getting the busybox and initramfs after 14 hours up letting the machine "upgrade," hoping that I would not have to rebuild all the work I'd alreaady done to get 10.10 working the way I want it to.  (raid and drivers and all the software that I wanted from packages.)

So now that my computer is frozen with only the initramfs available, is there a simple, magic way to "unroll" this wonderful upgrade, please?

Thanks.

---

### Post by Ym7^Hn4@?Xu on 2011-05-14
There is a thread [here]("http://ubuntuforums.org/showthread.php?t=1694896") that may help you.

---

### Post by beew on 2011-05-14
> **skypuppy said:**
> I'm getting the busybox and initramfs after 14 hours up letting the machine "upgrade," hoping that I would not have to rebuild all the work I'd alreaady done to get 10.10 working the way I want it to.  (raid and drivers and all the software that I wanted from packages.)

So now that my computer is frozen with only the initramfs available, is there a simple, magic way to "unroll" this wonderful upgrade, please?

Thanks.

There is no way to "roll back".  With hind sights I can only make a few suggestions.

1) back up important files before you update the OS no matter how you want to do it.

2) Some people may disagree and swear by their perfect experience but I would suggest doing fresh install instead of  upgrade. It is a lot simpler and takes a lot less time (20 minutes) and it is much more likely to work. Whereas upgrade takes hours even if it goes smoothly and there are many things that may break it, and even if it appears to succeed there may be hidden problems that manifest later on and it would be difficult to diagnose.

3) Do a fresh install instead of wasting your time to trouble shoot a blotched upgrade, it doesn't worth the troubles.

---

### Post by skypuppy on 2011-05-14
That may be the only way now, but I *hate* losing the scores and scores of hours I have already spent getting 10.10 to work the way I want it.

I shoulda known better.  <sigh>
I shoulda had a bit image backup.  Is there a tool that can do that or do I need to open a new thread?

---

### Post by fabricator4 on 2011-05-14
> **skypuppy said:**
> That may be the only way now, but I *hate* losing the scores and scores of hours I have already spent getting 10.10 to work the way I want it.

I shoulda known better.  <sigh>
I shoulda had a bit image backup.  Is there a tool that can do that or do I need to open a new thread?

Backup all your data to an external hard drive.  Make sure you get all the hidden files and directories (start with '.') as that is where a lot of your configuration is.

Try the solution in post 2 of the thread that you were referred to.  If that doesn't work you have 2 choices, try a fresh install of 11.04 or a fresh install of 10.10.  If you're starting from scratch set up a separate /home directory if you don't have one already.

I too recommend fresh installs over the upgrade, and back up data before doing any of the above.

Chris.

PS I should have also said there's a third way: do a fresh install but select "other/manual" instead of "use entire disk", then select the correct partition to install to, then untick the format box.  The installer will try to do a fresh install to the partition, but will delete redundant system files.  I suspect at least one person in your situation used this successfully to revert the upgrade, since they claimed that they "somehow managed to keep all their data and config".  Personally, I've not had complete success when I attempted to test this.

---

### Post by ClientAlive on 2011-05-14
Something that may be of use to you in the future?

[http://clonezilla.org/](http://clonezilla.org/)

:)

---

### Post by skypuppy on 2011-05-14
Sweet.  Clonezilla sounds like it is on it's way to being a really good backup system.  Not quite mature enough yet but getting there.  Wonder if I could help work on it?  Will check that further.  Thanks!

---

