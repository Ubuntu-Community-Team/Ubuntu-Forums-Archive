---
title: "Changing Mandriva for ubuntu"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2009-06-01
Hi, I have a spare laptop currently running windows and Mandriva. I'd like to keep the windows, uninstall the Mandriva and install Ubuntu instead. Is it going to be obvious to a technophobe how to do this without buggering everything up? If I download Ubuntu on (this) my everyday laptop (just running Ubuntu), burn it onto a disc and shove it into the other one (after uninstalling the Mandriva) will I be able to follow an idiot-proof menu to leave me with a machine that dual boots between windows and Ubuntu? Is there any step in the procedure I should look out for, a common stumbling block. Any advice in advance would be greatly welcome.
Thanks,
Dermot

---

### Post by perroazul on 2009-06-01
hi
once that you boot from the live cd, and you start installing ubuntu, you will reach the 'partitioning the disk' stage of the installation where if you go for manual partitioning, you could simply choose to install ubuntu over your previous mandriva partition. it's not hard to do, but it would be better if you have somebody who has done this before nearby.

---

### Post by fatality_uk on 2009-06-01
If you pretty much click through all the options, Ubuntu will take care of the paritioning for you.

---

### Post by Dermot Doyle on 2009-06-01
Thanks for the advice so far. Just thinking ahead, I realise I have never uninstalled an OS before. How do I uninstall Mandriva?

---

### Post by louieb on 2009-06-01
Its not like un-installing a program. With an OS you replace it with something else.  

like **perroazul **said - boot the Ubuntu install CD. When you get the partition stage chose manual. Click on the mandriva partition, chose edit, make its mount point / (root), check the format box. The Ubuntu install will replace mandriva.

---

### Post by Dermot Doyle on 2009-06-02
Cheers, I'll give it a go.

---

### Post by Dermot Doyle on 2009-06-03
Hi again,
I'm having a go at installing Ubuntu from a CD which seems to be working except I am a bit confused when I get to editing the partition to add Ubuntu and get rid of Mandriva. I have followed the instructions and got the edit box for Mandriva which seems to be /dev/sda8. It gives me the following options:
1. New partition size in megabytes: - do I need to set this?
2. Use as:   Ext3 journaling file system
             Ext4 journaling file system
             Ext2 file system
             Reiser jounaling file system
             JFS journaling file system
             XFS journaling file system
             FAT16 file system
             FAT32 file system
             Swap area
             do not use the partition

Which of these do I chose?
3. Format the partition:
4. Mount point:
The last two are not highlighted so I can't select them.
Any more advice would be appreciated.
Thanks

---

### Post by prvteprts on 2009-06-03
Just make sure the partition you have selected really is the Mandriva partition. You do not really need to set the size anymore, but perhaps you would want it to be maxed out. 

Back up all of your data, then select format and select "/" as the mount point.

By the way, do you already have a swap partition? Since you have been using another distro, most likely you would have one. If a swap was not specified, before proceeding with the install/formatting, the installer will ask you to select a swap partition.

---

### Post by Dermot Doyle on 2009-06-03
Thanks for the speedy reply. I'm sure I have got the right partition for the Mandriva and there is already a swap partition for that. Can I just leave that and use it with Ubuntu? Also, as I said, the format and mount point options in the box are not highlighted so I can't select them. Is that because I have not slected the correct option in the 'Use as:' box? If so, what should I choose?
I think I should point out again I am prety new to all this and am balancing on the borders of understanding and being completely out of my depth.
Thanks
ps. I have quit the install until I can get some more advice so I can't read off the screen as I write this. I think it said that Mandriva was /dev/sda8/ext3. Does that make sense? Should that be what I choose in 'Use as:'? The default is 'do not use this partition'.

---

### Post by prvteprts on 2009-06-03
Oh sorry. I forgot to mention you should either select ext3 or ext4 (recommended). I would suggest the ext4 as it is the more recent one. I'm not sure about /dev/sda8/ext3, I think it means Mandriva is on /dev/sda8 which uses ext3. Something like that.

I'm also pretty "new", it's just that I have actually done a lot of formatting and installing. Anyway, I'm glad to be of any help.

---

### Post by Dermot Doyle on 2009-06-03
Followed your advice and it all seems to have worked. I have a minor problem with permisions not letting me use the movie player, but I'm sure I'll sort that out. Thanks again for the help.

---

