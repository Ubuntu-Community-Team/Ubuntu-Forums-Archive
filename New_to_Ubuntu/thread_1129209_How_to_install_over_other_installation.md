---
title: "How to install over other installation?"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Xarver on 2009-04-18
Hello, this is Xarver.

I have a Dell Inspiron 8600 and want Ubuntu 8.10
I forgot my password and account name because I have been gone,
and want to delete all my files, so I want to reinstall.

I have Windows also on my computer, and want a dual boot.
I want Ubuntu 8.10 and Windows on the same computer, 
I know how, but the CD won't let me.

When I go on the installer to the partition editor step, I see no Windows.
It only allows me to edit my older Ubuntu's partition and the one going to be installed. [_Screenshot here_]("http://i39.tinypic.com/2cqzll5.png").

What is wrong?
I want a dual boot with My New Ubuntu and Windows,
not My New Ubuntu and Old Ubuntu!

[_Here's a screeny of my partitions_]("http://i41.tinypic.com/k99cub.png").


I want a dual boot with Windows XP and Ubuntu 8.10
Help please. :D

~ Xarver

---

### Post by nandemonai on 2009-04-18
Hmm interesting.. Not too sure what's up there.

What do you get when you enter 'manual' partitioning mode?

Edit: On second look why do you have two swap partitions?

I'd suggest manual mode, nuke all the logical partitions inside sda2 then recreate ubuntu partitions.

One for /
One for swap
And if you want a seperate home then one more for /home/

---

### Post by -kg- on 2009-04-18
What nandemonai said.

If you select Guided - Resize, as your screenshot indicates, it will select the partition *it* wants to resize which in your case is your old Ubuntu partition.  You would be able to install the new installation in the free space that was created, but you would still have your old installation listed in GRUB, as well as your Windows installation.  No worry about not having Windows...it would still be there and listed in GRUB as well.

Alternatively to deleting the old Ubuntu partition (which is actually an unneeded step), go into manual partitioning and mark the old ext3 (sda7 on your GParted screen) as / (which is root), delete one of the swap partitions (you only need one, as nandemonai said...I would delete the one closest to the ext 3 partition and as part of the installation process, expand the ext3 partition into the space freed up), and mark the other as the installation swap file.

I notice that you have a small (approx) 204 MB ext2 partition in front of the ext3 partition.  Make sure you don't accidentally mark that for installation.  Unless you're using that partition for something, I would mark it for deletion.  When partitioning a hard drive, there are sometimes small spaces like that when the partitioner is rounding clusters, and if you extend or partition these spaces, it sometimes causes problems.

Do the above, and the installer will use the existing ext3 partition as the installation partition (along with the marked swap space), overwriting any information in that partition with the new installation files.  The installer will automatically replace GRUB in the MBR with it's own GRUB, allowing dual booting with itself and Windows.

With 10 GB of space available for Ubuntu, a separate /home partition isn't practical.  You have little enough space for Ubuntu itself.  If you decide you'd really like to do this, it would be quite an operation, because you'd have to shrink your sda3 partition (all the way to the right), expand your extended partition, move the swap partition to the end, and then create your /home partition in the space provided.

It certainly can be done, but it depends on what you're using your sda3 partition for and what you anticipate for it's usage and future needs for space in it.

---

