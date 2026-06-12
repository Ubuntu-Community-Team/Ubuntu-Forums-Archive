---
title: "Ubuntu on my laptop"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by gerryharris on 2010-09-21
Trying to install Ubuntu on my laptop.
My laptop has 2 Windows 7 partition's installed.
When I try to install ubuntu get a message that it can't detect an installed operating system and do I want to format the entire HD.
I want to have Ubuntu and 2 Windows 7 partitions installed so that i can select which one i want to boot from.
Cheers
Gerry

---

### Post by Rubi1200 on 2010-09-21
Are you trying to install via Wubi or a regular install to the drive?

Did you create a partition for Ubuntu on the drive and how?

Do you have a recovery partition on the drive that came pre-installed?

We need these details in order to help you further.

---

### Post by gerryharris on 2010-09-21
> **Rubi1200 said:**
> Are you trying to install via Wubi or a regular install to the drive?

Did you create a partition for Ubuntu on the drive and how?

Do you have a recovery partition on the drive that came pre-installed?

We need these details in order to help you further.
Thanks for the prompt reply

This is my first attempt at Linux/ Ubuntu so please forgive me if I'm asking stupid questions.

Trying to install from the free DVD from PC Pro magazine.
No, I didn't create a partition.
No I don't have a recovery partition, I deleted it when I installed Windows 7

Cheers
Gerry

---

### Post by Rubi1200 on 2010-09-21
Before you continue, make backups of any important data (something could go wrong).

Then, boot into Windows and use the built-in disk management tool to create a partition for Ubuntu (but don't format it).

Then, run chkdsk a couple of times and boot back into Windows to make sure everything is good.

And, finally, use the Ubuntu DVD to install to the "largest continuous free space"

After that, you should be set.

Here are some links to help:
[http://www.w7forums.com/use-chkdsk-check-disk-t448.html](http://www.w7forums.com/use-chkdsk-check-disk-t448.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

---

### Post by Dustin2128 on 2010-09-21
you could also use a gparted or knoppix live disc for partitioning. I never had any success with windows' tool when trying to get my brother's laptop on a dual boot.

---

### Post by -kg- on 2010-09-21
> **Rubi1200 said:**
> Before you continue, make backups of any important data (something could go wrong).

Then, boot into Windows and use the built-in disk management tool to create a partition for Ubuntu (but don't format it).

Then, run chkdsk a couple of times and boot back into Windows to make sure everything is good.

And, finally, use the Ubuntu DVD to install to the "largest continuous free space"

Uh, not quite right.  If you create a partition, whether formatted or not, you will not have any free space to install into (unless you're referring to creating an Extended partition).  

You say that you have two "Windows 7" partitions (I assume you mean, formatted to NTFS)...what are you using the second partition for?  If nothing much (and especially if there's nothing much in it, or it has a lot of free space), I would boot into Windows and use Disk Management to shrink that partition, creating the "Continguous Free Space" in which to install.  If there's actually no real use for it, you could even delete that partition.

If you can't (or don't want to) do without the extra partition, then you'll need to shrink either the Win 7 boot partition or the second partition (or both) to create the free space.  Again, this is best done with Windows' Disk Management tool rather than GParted, especially the Win7 boot partition.  Of course, before you shrink these partitions, you want to defrag them.

Check out the page linked to in my signature block.

---

### Post by gordintoronto on 2010-09-21
To use the Windows 7 disk management tool:
in Windows Control Panel, search for "disk," and one of the items is "Create and format hard disk partitions." Click on it, highlight the C: drive, select "action," "all tasks," "shrink volume."

---

### Post by gerryharris on 2010-09-23
My disk is set up as:-
C Winows 7
D Windows 7
E Data
F Data
K Data
and a 29Gb unallocated area.

I can boot from either my C or D partition.
T want to keep the existing partitions as they are.
When I try to install Ubuntu it says it can't find a pre installed operating system, or words to that effect, and do I want to format the entire disk.

Cheers
Gerry

---

### Post by clarkhlong@gmail.com on 2010-09-23
How do I format hardrive and install ubuntu on a dell c840 laptop that still has a kernel of w2k (non operable) ??
thanks:)

---

### Post by gordintoronto on 2010-09-23
> **gerryharris said:**
> 
T want to keep the existing partitions as they are.
When I try to install Ubuntu it says it can't find a pre installed operating system, or words to that effect, and do I want to format the entire disk.

Cheers
Gerry

There is an "advanced" button, select it and proceed. It will put you into Gparted, where you can double-click on the free space, and say you want a partition there, formatted as EXT3, and mounted as "/".

---

### Post by gerryharris on 2010-09-25
> **gordintoronto said:**
> There is an "advanced" button, select it and proceed. It will put you into Gparted, where you can double-click on the free space, and say you want a partition there, formatted as EXT3, and mounted as "/".
Tried that an the Ubuntu install overwrote all my partitions.:(:(
Took several hours to restore my Windows and data partitions.
Thought I'd have another go and this time the Ubuntu instal recognised that I had Windows and other partitions installed.
Ubuntu installed OK in the unallocated space. :):)
Cheers
Gerry

---

