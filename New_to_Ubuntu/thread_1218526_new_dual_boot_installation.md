---
title: "new dual boot installation"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by emeraldgirl08 on 2009-07-20
Hi. Am installing Jaunty on my sisters comp that has this partition set up:

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1bfbae8d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        2563    20483873+   7  HPFS/NTFS

I get up to the manual edit partition. I do not know what to do after this. 

I do not want to erase the NTFS partitions. They must stay there. So Jaunty is going to be installed after the NTFS partition. The computers has 2 gb of RAM. I only want the NTFS and the Jaunty to coexist on this drive. 

Can anyone help???

---

### Post by emeraldgirl08 on 2009-07-20
Okay. I couldn't wait any longer. I didn't know what to do so I expanded the NTFS to fit the entire hard drive. I then installed Jaunty "side by side" with NTFS. 

I gave NTFS 20gb and Jaunty the rest.

Now. I got to the last screen to begin installation and chose advanced. I think I may have read something about Windows not being able to see Linux so I chose to install a bootloader. I didn't know where to put it so I put it in the sda1. I believe that's Windows bootloader. Not sure.

Did I flub it up??? I don't know yet b/c it's installing.

**EDIT:**

I did it right. It finished installing and rebooted. I got Grub to give me a menu with booting choices :D

So if you are booting M$ install the bootloader into the Win boot partition.

---

### Post by powel212 on 2009-07-20
It looks like you are on the right track. What I do is create an empty, unformatted partition for ununtu then during the install I select "install to largest continuous free space. This way the windows partition is left alone and the empty space is used for the Ubuntu system. This is the easiest way I have found to create a clean dual boot.

I hope that helps

Powel

---

### Post by jflaker on 2009-07-20
It is pretty simple:
Pay attention to the installer...When you get to the partitioner, you will have the opportunity to resize your windows partition....Just shrink it so that you have at LEAST 10GB of unformatted space...then let the installer install and configure the partitions on the unformated space...Just make sure you pick the correct partition after the resize or you will overwrite Windows.

---

### Post by emeraldgirl08 on 2009-07-20
:popcorn:

It was pretty nerve-wracking! I was at this since Ten this morning! I'm somewhat familiar with Ubuntu b/c I have it installed on my Lappy since Intrepid.

However my sis' desktop is a homebuilt one so that sorta threw a monkeywrench in. I was going to do Fedora but I got some kind of I/O error and scrapped that. I wanted Fedora b/c I heard that it's very good with Intel hardware. Ubuntu was the other choice b/c of the familiarity and knowledge that it's pretty easy to pick up with a little effort.

So now that I got the two OS'.  I have more homework to do! My job is not quite yet complete.

Thanks for the tips guys.

---

