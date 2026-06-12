---
title: "Manually installing ubuntu on an existing partition.  Impossible?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by Swashy on 2009-04-23
I noticed theres three partitioning options concisely explained in the doc help files for installing Ubuntu: Installing Ubuntu on the free space next to my windows  installation,and installing it over everything. Wait, make that two, manual install isn't explained at all.

I need manual install.
I already set up a partition for Linux next to my current windows after a failed Fedora installation, but it seems Ubuntu doesn't notice that there are more than one partitions outside of manual.

**How** do I install Ubuntu on the other existing partition manually? No matter what options I choose, be it a FAT file system or a Journal file system, I apparently need a non existent ROOT file system option for the partition. How do I do it?

I'm trying to install the desktop version of Ubuntu 8.04 - *The Hardy Heron*.

p.s.
Sorry if I seem condescending but I'm really pissed off at operating systems right now. I'm posting this from the live CD pre-installation Ubuntu.

---

### Post by supersonicdarky on 2009-04-23
I'd guess it wants you to set the mountpoint to /

---

### Post by kanikilu on 2009-04-23
If I'm understanding your question right, no, it's certainly not impossible. As you've already guessed, you'll want to choose the manual option when you get to the partitioning part of the installer.

There's a pretty detailed thread on partitioning here:

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

But, you simply want to use the existing linux partition that you say you have. Just set the mountpoint as "/" and format it as ext3 (unless you have another fs type in mind...). The only other thing you'll need is a swap partition.

---

### Post by Swashy on 2009-04-23
the only mountpoints are /dos and /windows.

edit: Whoops, nevermind I'm stupid. All the mount options popped up for ext3, thanks!

---

### Post by ajgreeny on 2009-04-23
Here are two sites which I hope will help you.
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Possibly the second one is most straightforward and easy to follow, though they both give the same info in different ways.

Come back again if you want more details, but reading these and then going to the "Manual" button at installation partitioning screen, should be relatively self explanatory.

---

### Post by Random-penguin on 2009-04-23
Choose the manual partition option, then this will open a new window from where you can see all your partitions. Choose the one you formated and edit it so that you change it to (for instance) ext3 and root (/). Don't forget you also need a seperate "swap" partition in Linux. Its common practise for this to be twice the size of the amount of RAM you have installed. If you haven't enabled this you can use the same window to delete the partion you've already setup and create two new partitions; one root and one swap.

You may also want to create a seperate partition for your home directory (/home) where all your user files will be kept (makes upgrades easier in the long term; in my opinion).

Good luck and enjoy your new linux systemhttp://ubuntuforums.org/images/smilies/icon_razz.gif

---

