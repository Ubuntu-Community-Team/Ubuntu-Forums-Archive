---
title: "Bootloader"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by Steelfan555 on 2009-10-15
I have Windows 7 and Ubuntu (9.04) on 2 different partitions, and yesterday i went to delete the Ubuntu Partition, using gparted, and when i tried to boot into Win 7, I received a Grub error, and could go no further. So i reinstalled Ubuntu, and everything worked fine. I can leave Ubuntu on for now, but eventually it will have to go. Any ideas?

---

### Post by mike555 on 2009-10-15
you will need to edit grub to not look for Ubuntu partition , then format Ubuntu partition (if you must get rid of it) to ntfs , and use it for a backup partition ..


or you could delete the partition join it with the Windows partition , then repair MBR with a Windows repair disc.

---

### Post by Steelfan555 on 2009-10-15
> **mike555 said:**
> you will need to edit grub to not look for Ubuntu partition , then format Ubuntu partition to ntfs , and use it for a backup partition ..
First: How do i edit Grub to not look for Ubuntu?
Second: Would reformatting be the same as deleting?
> (if you must get rid of it)
Just on this computer :) its installed on others as well.

---

### Post by mike555 on 2009-10-15
here is the problem, grub is looking for whatever is listed in it , if it doesn't see a partition as bootable it errors out ......... so if you (as root) edit your Boot/Grub/menu.1st file and put a "  #  " sign in front of the Ubuntu lines (or delete them) and save , then next time you start grub wont look at the Ubuntu partition .......

 hope I typed it right so you can understand it...

-- this is assuming you don't want to boot the Ubuntu partition --

---

### Post by mike555 on 2009-10-15
reformating is not the same as deleting , if you use gparted to delete you will not be able to use the partition ....... until you reformat the partition , if your going to just use the partition as storage for Windows format it as NTFS ......

 that said you can just reformat a partition without deleting it first ..... ether way will loose anything on that partition (so make sure you do the right one)

---

### Post by yanceypd on 2009-10-15
If you have a Vista system disk you can repair the master boot record.  Then using computer manager remove the Ubuntu partition  I do believe.

---

### Post by PrePenguin on 2009-10-15
Just download easyBCD and repair Vista MBR and delete the ubuntu partition then reclaim it in computer management in control panel.

---

### Post by sandyd on 2009-10-15
> **PrePenguin said:**
> Just download easyBCD and repair Vista MBR and delete the ubuntu partition then reclaim it in computer management in control panel.
hes using windows 7.

---

### Post by PrePenguin on 2009-10-16
> **carlee said:**
> hes using windows 7.
 
 
 
Dont matter easyBCD repairs windows 7 MBR same as Vista's matter of fact you need this to edit both Vista and Windows 7 since they do not use boot.ini nomore since XP.

---

### Post by Steelfan555 on 2009-10-17
Sorry for my late posts, i was out of town yesterday.
> **PrePenguin said:**
> Just download easyBCD and repair Vista MBR and delete the ubuntu partition then reclaim it in computer management in control panel.
Thanks! THis worked perfectly! I knew there had to be a way to edit the boot.ini, but since i skipped vista and only have Win7 and Xp, i couldn't find it.

Mike555, im sure your idea would work, but i did not want to use Grub at all (my fault for not making it clear). 

Thanks to everyone for there help!

---

