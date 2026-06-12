---
title: "Various things"
date: 2010-11-09
forum: New to Ubuntu
---

### Post by NeverUsedItBefore on 2010-11-09
Right, this is my first ever post, I'm sorry if these are stupid questions!

1) I installed WUBI its great.
Can I just keep using it forever? I read somewhere that it's performance would be bad and it should be used only in the short term..

2) Related to 1)
If I want (or you tell me I need) 'full ubuntu', can it magically handle such things as creating a partition for me? & Do I have to create a partition, I had plenty of free disk space (34GB) ?

3) Is there an easy way to get my windows files in Wubi? Can it not just sync e.g.
My Documents in XP to Home Folder or documents in Wubi?

4) This one says it can transfer me across to Full Ubuntu, but it seems to need some partition action:
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

Also, it doesn't work with the wubi I downloaded "You are using Ubuntu 10.04 LTS - the Lucid Lynx "

Do you reckon someone will fix that up one day?

---

### Post by bcbc on 2010-11-09
There are no stupid questions. Some stupid answers ;)

1) Some people seem to keep wubi long term. You run risks - particularly since grub2 came along there have been some 'mishaps' that wubi is vulnerable to. Take care doing updates to packages grub-pc, grub-common and lupin-support. Avoid release upgrades or backup beforehand. NEVER do a hard shutdown - use ALT-SysRq+R-S-U-B instead

2) You will need a tool to partition. Win XP doesn't have a built in tool. If you want to use GParted you need to unmount the drive so you can't do it by booting wubi. You will have to create an Ubuntu CD and boot it in 'live mode' (Try without installing).

3) Look in /host to access data on windows
You could probably use rsync to keep directories in sync. Or just keep and reference the data in /host... 

4) [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html) is out of date and won't work. You can use [this]("http://ubuntuforums.org/showthread.php?t=1519354") instead, but you need to create the partitions first.

---

### Post by NeverUsedItBefore on 2010-11-09
OK great thanks.
It seems that to migrate from wubi to full then - there is no advantage over just following the full instructions including creating a partition etc.
I guess it's all free which is great ! But as a first time user, it seems like the opportunity is there for someone to simply create a one click install package for Windows that installs the full ubuntu and not just wubi.

I've already done some 'hard resets' oops.
So I have to press Ctrl+ SysReq + the keys R S and B?
Doing so seems to make a screenshot utility appear?

---

### Post by bcbc on 2010-11-09
> **NeverUsedItBefore said:**
> OK great thanks.
It seems that to migrate from wubi to full then - there is no advantage over just following the full instructions including creating a partition etc.
I guess it's all free which is great ! But as a first time user, it seems like the opportunity is there for someone to simply create a one click install package for Windows that installs the full ubuntu and not just wubi.

I've already done some 'hard resets' oops.
So I have to press Ctrl+ SysReq + the keys R S and B?
Doing so seems to make a screenshot utility appear?

ALT+SysReq then R S U B ([http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html) or [this]("https://wiki.ubuntu.com/WubiGuide#How to reboot cleanly even when the keyboard/mouse are frozen"))

If you insert an ubuntu CD in windows it pops up and one of the options is to reboot and install Ubuntu (including a utility that will partition automatically). There's even an ability to boot the CD from the hard drive (similar to the way wubi boots) if you can't boot from a CD.
So that is already there. If you just download wubi.exe then you don't get that option.

---

