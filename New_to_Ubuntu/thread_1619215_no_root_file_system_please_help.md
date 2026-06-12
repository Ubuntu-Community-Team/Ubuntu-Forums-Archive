---
title: "no root file system please help"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-11
I am installing ubuntu 10.10 for my uncle in his computer now  we made a new partition as ext3 and linus swap and when we went into installation the error message came saying no root file system defined please correct this from the partition menu [COLOR=DarkRed]_***and as we are very new we dont know how to handle this please some one help us***_[/COLOR]

---

### Post by mcduck on 2010-11-11
When you do the partitioning you need to select what each partition is used for.

The error message tells you that you haven't set any partition to be used as / (the root partition, kind of the equivalent of C:\ in Windows).

The partioner should have a dropdown box that lets you set the mount points for the partitions. Just make sure the partition you intend to be the main Linux partition has it's mount point set as "/".

---

### Post by TeoBigusGeekus on 2010-11-11
> **fatharraxman said:**
> I am installing ubuntu 10.10 for my uncle in his computer now  we made a new partition as ext3 and linus swap and when we went into installation the error message came saying no root file system defined please correct this from the partition menu [COLOR=DarkRed]_***and as we are very new we dont know how to handle this please some one help us***_[/COLOR]
Apart from the type of your new partition (ext3), you also have to define its mount point. 
For every linux environment to function properly, it must have a root partition mounted on /.
A good idea would be to create another partition (ext3 as well) and mount it as /home.

---

### Post by fatharraxman on 2010-11-11
Thank you for your kind care 
I now  understood my fool action but how can I correct yhiis I didnt find any box tell you how to make this partition as root am using Gparted

---

### Post by TeoBigusGeekus on 2010-11-11
You don't have to use gparted to create partitions for a new installation of ubuntu. It can be during install with the partitioner. Just right click the partition, select change (I think, try it out) and give its file system (ext3,4 etc.) and its mount point (/, /home, /boot, etc.)

---

### Post by mcduck on 2010-11-11
> **fatharraxman said:**
> Thank you for your kind care 
I now  understood my fool action but how can I correct yhiis I didnt find any box tell you how to make this partition as root am using Gparted
You can't do that beforehands in any partition editor, that's something you need to do in the *Ubuntu installer*.

edit: Here's a guide (with pictures) to help you: [http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/]("http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/")

---

### Post by fatharraxman on 2010-11-11
Thank you very much for your kind help 
but am very fool really 
I spoiled it all now I dont now how to deal with this new problem when i correct the \ the installation hanged up I made a restart and again from usb it gave me a black screen with root on it what shall i do??????? it say
> can not creat/ver/lib/update/-notifier/updates-available:Input/output error
Welcome to ubuntu!
*Documentation: [http://help.ubuntu.com/](http://help.ubuntu.com/)

What am I supposed to do please??

---

### Post by Devon Fletcher on 2011-01-06
**[FONT=&quot]Re: No root file system is defined -What is the workaround[/FONT]**[FONT=&quot] [/FONT]
  [CENTER][CENTER][FONT=&quot]    [/FONT][/CENTER][/CENTER]
  [FONT=&quot]1. boot Ubuntu from CD (or USB stick)
2. run Gparted (System>Administration>Partition Editor), to set up the Ubuntu Partition. I formatted the partition as ext4, this may not be essential.
3. run Disk Utility, select the partition (click on the appropriate rectangle in 'Volumes').
4. click 'Edit Filesystem Label' and type "/" (without quotes) in the 'Choose a new filesystem label' dialogue box. click 'Apply'.
5 double-click the 
&#8216;Install Ubuntu' icon, away she goes![/FONT]

---

