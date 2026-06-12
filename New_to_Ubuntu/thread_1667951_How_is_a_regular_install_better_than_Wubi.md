---
title: "How is a regular install better than Wubi?"
date: 2011-01-15
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-01-15
I've been using Ubuntu since 2008, and I've only used Wubi to install.  So far from what I know, the limitations are no hibernation/standby, limited to a 30 GB virtual disk, and that if Windows (as in a virus or something) goes down it pretty much takes Ubuntu with it.

I've used Wubi on my desktop until it broke, and I've been using it on my laptop since its setup all weird (hard drive partitioned, both having Windows files on it, if I choose Vista from GRUB it loads "recovery" mode when I just choose Vista, Vista only loads via Windows Bootloader).  So far I rarely had a problem using it other than two problems I had.  Not to mention people keep saying that Wubi is only for trying Ubuntu (which I don't get.  It installs and saves, and I'm sure someone doesn't want to uninstall Ubuntu via Wubi and lose everything.  Not to mention Live CD is a way of trying Ubuntu without installing).

When my desktop gets fixed, I plan on installing Ubuntu and dual-booting it.  What are the benefets of a regular install, over a Wubi install.  I'm not changing my laptop as I never had a problem using Wubi, but I just want to learn a little more between the two as a regular install is still something new to me, and I wish to use it once my desktop is fixed.

---

### Post by kn0w-b1nary on 2011-01-15
1. Faster Boot.
2. Custom Partitioning (Encrypted LVM)
3. If anything goes wrong on the windows shutdown like a power loss, ubuntu doesn't have to run checks.

These were on the top of my head though there may be more,:)

---

### Post by Frogs Hair on 2011-01-15
More stable file system over the long term and more disc space available for your installation  . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by kaldor on 2011-01-15
WUBI is also really slow. If you install it on a poorly maintained Windows, Ubuntu will also suffer from the slowness of Windows and needs defrags.

---

### Post by JKyleOKC on 2011-01-15
Well, you already mentioned the three biggest drawbacks for wubi as sompared to a normal HD install. That said, I use wubi on my HP laptop, under WinXP Pro, because the LiveCD didn't want to run on it. However I don't use the laptop much at all, and when I do it's usually for some Windows-only task. Most of my computing is done via the four mini-tower boxes I have in my home-office LAN, all of which run Xubuntu.

---

### Post by abdulapopoola on 2011-01-15
You get to feel the real thing.
Your system runs faster and you get to hibernate.
Most importantly, you can access your Windows partitions from your Ubuntu.

---

### Post by lisati on 2011-01-15
If Windows gets broken (maybe some malware slips in unnoticed gets up to mischief) there's less hassle getting into Ubuntu with a regular install.

---

### Post by LinuxFox on 2011-01-15
Thanks for the responses, after reading, I understand a regular install a little better. :)  I'm still keeping the laptop as a Wubi install due to Window's weird setup.  Though I look forward to doing a regular install along with XP once my desktop is fixed (I still need Windows for Windows things).

As for Wubi being slow, if it's slow, then it's fast for slow.  I find my Wubi install faster than using Windows.  I can only imagine how much faster it will be. 8)

---

### Post by bcbc on 2011-01-15
It's not slow. It's much faster than a live USB. I can't notice a difference between wubi and a normal install - although I believe it is slower.

The big downside is that everything is on a single file (root.disk). You can't really lose or corrupt a whole partition easily (although some people seem to manage it), but it's not nearly as hard to lose or corrupt a file. Back it up now and then for insurance.

The next big thing is grub2. Updating this [tends to break wubi booting]("http://ubuntuforums.org/showthread.php?t=1639198"). But the problems aren't too difficult to solve if you've used Ubuntu for a long time, as you have. I recommend locking grub-pc and grub-common - these updates don't give you any benefit and lots of pain.

Finally, I like to hibernate my windows install a lot. You can't boot wubi while windows is hibernated. By the way, there shouldn't be any problem suspending when using Wubi.

Wubi support is also very limited.

---

### Post by LinuxFox on 2011-01-15
You know, I never thought about backing up that root.disk file ever.  This is coming from someone who always back-up their files.  I guess the GRUB2 problem happened to me the other day.

I usually don't update GRUB, or when it asks, I keep it the same.  I was updating my Mother's computer (also a Wubi install) and it must have updated GRUB. I was able to fix it thanks to a Wubi topic and some help from some people on the forums :)

---

### Post by bcbc on 2011-01-15
> **LinuxFox said:**
> You know, I never thought about backing up that root.disk file ever. 
it's not the most efficient backup - you're actually backing up the 'free space' on your virtual disk, as well as arbitrary OS files along with the important stuff. But it's really easy to do. Copy, Paste. To restore, copy back over.

---

