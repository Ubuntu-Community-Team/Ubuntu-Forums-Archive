---
title: "An easy way to delete Windows XP from a dual boot system using Meerkat"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by Terry Maker on 2011-03-01
**DOES ANYONE KNOW HOW TO DO THIS?**

This one has probably been around before! But nothing came up on the search!


I've been using Maverick Meerkat on my Dell Dimension 3000 since last year, and the Windows XP is never booted now, so how do I remove it? Does anyone have any easy ideas?

After some time I now have a system that is set up with software to my liking and with data as well. From what I've read, it seems that I have to delete the lot and start over to have a Ubuntu only machine! 

Which is Crazy!

When the guys who thought out the install CD and offered a dual boot option, did they never think that this question would arise? or at least offer a way to increase the 18Gb partition.

Terry M

Any ideas would be gratefully accepted.

---

### Post by mikechant on 2011-03-01
> From what I've read, it seems that I have to delete the lot and start over to have a Ubuntu only machine! 

This is not true *unless you did a Wubi install* (see below).

However, depending on exactly how your hard drive is partitioned, sometimes it is easier to back up to an external drive, delete everything, re-partition and restore your data/OS.
Also, since recovering the space Windows uses and giving it to Ubuntu typically involves at least some partition changes it is always best to back up everything first. But if your data has any value at all to you I guess you already have a backup method?

Anyhow, here's a few things to start with:
[LIST=1]
[*]When you installed Ubuntu, did you use the 'Wubi' install method? If so, Ubuntu is installed inside Windows as a Windows Application, and you can't delete windows without deleting Ubuntu. So in that case you do need a fresh install to go 'Ubuntu Only'. If you're not sure if you did this, boot windows and go to Add/Remove programs; if Ubuntu appears in the list, it's a Wubi install.
[*]If we can see your partition layout, it's easier to give detailed instructions. If you open a terminal and type the command 'fdisk -l' without the quotes, and post the results this will help. (NB the second character in -l is a lower case L, not a number one!). 
[*]A fairly safe but not ideal way to recover the space is to just reformat the windows partitions, they will then be available for data storage in Ubuntu and should appear on the places menu. However, the space occupied by the Windows partitions *can* be shuffled around into the Ubuntu partitions to do things 'properly' but you really need to back everything important up if you do this in case it goes wrong.
[/LIST]

---

### Post by runeh76 on 2011-03-01
Hello :)

I would try **Gparted** and after that i think u need just configure **GRUP**. _MAKE A BACKUP BEFORE!_

Good Luck & Bye Bye Windows! :)

---

### Post by Terry Maker on 2011-03-01
It's a Wubi install, the Ubuntu appears on both the programs list on control panel, and I can also see it in explorer.

The 'original' install, was the dual boot option on the Canonical Download 'CD' that I made.

TM

---

### Post by runeh76 on 2011-03-01
U could wait month and install clean new 11.04...

---

### Post by Mark Phelps on 2011-03-01
> **Terry Maker said:**
> Which is Crazy!

When the guys who thought out the install CD and offered a dual boot option, did they never think that this question would arise? or at least offer a way to increase the 18Gb partition.


If you done a simple Google on Wubi Guide before you started complaining, you would have found the following:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

Look at sections 8.8 and 8.9 -- as you can  see, "the guys" already have answers to your questions.

---

### Post by Terry Maker on 2011-03-01
No luck with the "fdisk -l", both on windows, or Ubuntu! both gave me a "File not found" message!

I don't ever remember Fdisk being a part of XP anyway, other than on the install CD

TM

---

### Post by amjjawad on 2011-03-01
> **Terry Maker said:**
> **DOES ANYONE KNOW HOW TO DO THIS?**

This one has probably been around before! But nothing came up on the search!


I've been using Maverick Meerkat on my Dell Dimension 3000 since last year, and the Windows XP is never booted now, so how do I remove it? Does anyone have any easy ideas?

After some time I now have a system that is set up with software to my liking and with data as well. From what I've read, it seems that I have to delete the lot and start over to have a Ubuntu only machine! 

Which is Crazy!

When the guys who thought out the install CD and offered a dual boot option, did they never think that this question would arise? or at least offer a way to increase the 18Gb partition.

Terry M

Any ideas would be gratefully accepted.

No offense mate but if I were you, I would spend some time searching on google as my first step, then I might start a thread here as my last step ;)
Your question is already answered in many threads/websites.

Good luck and sorry if that wasn't helpful.

---

### Post by mikechant on 2011-03-02
As it *is* a wubi install, the answer is simple anyhow; Ubuntu is 'inside' Windows so you can't get rid of Windows without deleting Ubuntu as it stands.
So if you want Ubuntu only, you need to reinstall by booting from a Ubuntu CD or USB and selecting the 'use entire disk' option, after backing up any important data.

Wubi installs aren't really a good long term option anyhow; they tend to get problems which 'proper' installs don't.

If you've installed and configured a lot of software, it's possible to
a) generate an installed package list from your current install and use it to easily install the same packages on the new install
b) copy the hidden config directories in your home directory (beginning with '.') across to the new release. You can copy your entire home directory across including the config files if you want, as long as you've got a suitable backup device.

So most of the setup work you've done doesn't have to be wasted.

If you haven't got an external USB hard drive for the backup/restore process, I'd really recommend getting one for general backup use anyhow - they're not expensive!

---

### Post by Zimmer on 2011-03-02
Once you have rescued your data files... before you start to install Ubuntu to the whole disk... do a bit of reading (some of it may be difficult and confusing.. but..)

Read up on partitioning (links to follow ).

[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

this is useful for all sorts of stuff (GRUB particularly) but intended for those wanting to dual boot (properly) Windows and Linux and there is a lot here...
[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

................

When you have read about partitioning consider your preferred partition plan... 

As a suggestion, if you have a large HDD (100 gb plus) and your data requirements are not too large .. then create 3 Primary partitions of 10-15gb each and one extended partition with the remainder. Put your swap partition inside the extended partition and create a data partition there, too.

You can now install Ubuntu to the first Primary partition (and install GRUB to the MBR of the disk).

When you get confident of installing Linux and curious of other distros you will then have Two primary partitions to play with (install, Fedora, SUSE, Mint whatever or the next Ubuntu release to try them out properly...) while storing all your important stuff to folders in your DATA partition.. and backup your data partition to an external drive regularly (rsynch is useful here).

But read quite a bit first.
If your data is 'safe' then you can have confidence in recovery from mistakes made at install... :)

---

### Post by grahammechanical on 2011-03-02
Why does Ubuntu get the blame for the choices that we as users make?

At installation time we get the choice of installing Ubuntu and removing windows (use the entire disc) or Installing alongside Windows (partition the disc), or installing inside Windows (wubi = easy removal of Ubuntu.

We make the choice and the program does the job it is designed to do. Do the developers get thanked? No, but we get the complaints.

Someone selected use the entire disc and now they want windows back. Well, it is gone. User's choice.

Someone chooses to install inside Windows and they complain that it is now hard to remove Windows. Again it is user's choice.

Get something for free and we complain that it does not do what we want. Pay 100 - 150 pounds, dollars, whatever and we don't complain. In fact we pay again for the newest version of the OS.

What a sad lot we are.

Regards.

---

### Post by Terry Maker on 2011-03-02
SOLVED! SOLVED! SOLVED!

Decided to rebuild! 

Started 10:30, now finished! seemed the best way out.

Thanks to all those who offered help.

I feel that you learn more in rebuilding anyway.

Terry M

---

