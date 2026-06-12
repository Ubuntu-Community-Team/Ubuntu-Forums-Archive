---
title: "Trying wubi out, but in need of advice"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by Res2216firestar on 2009-02-27
Hello all, I am (for the third time) attempting to use wubi from *indows XP, but while I wait for the iso to download, I would like a quick question answered: The first time I tried wubi, everything went right except the ubuntu installation, I got stuck on partitioning, it gave me no options to continue with, empty selection box, next button grayed out, nothing. The second time, I got stuck in GRUB with no way to boot, at that point I gave up. Now I would like to try again, but would like some pointers for avoiding the above, esp. the partition problem, since I think the GRUB problem was just a lemon install. Thanks--Sam

---

### Post by theozzlives on 2009-02-27
When I install WUBI for people, I just put the live CD in and click install in Windows. Works fine. Be sure you're burning the CD at the slowest speed and doing a Md5sum wouldn't hurt.

---

### Post by avtolle on 2009-02-27
Did you defrag the HDD prior to beginning the install via Wubi? IIRC, from reading the Wubi guide, when partitioning problems are encountered during the installation, many times the problems are related to a badly fragmented drive. Another suggestion would be to run chkdsk -r (IIRC) from Windows before installation. HTH.

---

### Post by issih on 2009-02-27
<ignore me...both the people above look more knowledgeable on this subject>

I may be wrong here, as I haven't used wubi, but as I understand it, with wubi you never touch the partitions of your hard drive, the entire linux distribution is installed as a special file inside your windows file system.

I think wubi also uses the windows bootloader, so I don't think grub would be involved either, although maybe the wondows loader just chainloads grub to start ubuntu.

In essence I'm confused as to what you are doing. If you are using wubi, then you shouldn't need to mess with partitions or grub at all, thats the point of it, its to allow you to try ubuntu without needing to get into the technical nitty gritty of installing the OS too much.

If you boot your pc from the live cd, then that is NOT a wubi install and all these things begin to make sense...

---

### Post by Ms_Angel_D on 2009-02-27
> **issih said:**
> <ignore me...both the people above look more knowledgeable on this subject>

I may be wrong here, as I haven't used wubi, but as I understand it, with wubi you never touch the partitions of your hard drive, the entire linux distribution is installed as a special file inside your windows file system.

I think wubi also uses the windows bootloader, so I don't think grub would be involved either, although maybe the wondows loader just chainloads grub to start ubuntu.

In essence I'm confused as to what you are doing. If you are using wubi, then you shouldn't need to mess with partitions or grub at all, thats the point of it, its to allow you to try ubuntu without needing to get into the technical nitty gritty of installing the OS too much.

If you boot your pc from the live cd, then that is NOT a wubi install and all these things begin to make sense...

Wubi Still "acts" as if it's partitioning which technically it is it's partitioning the virtual drive created to use in the install of the OS. But as someone above said typically a partition error with wubi means the windows drive needs to be defragged before install.

---

### Post by Bölvaður on 2009-02-27
-- great... Im just repeating what the others said --


Defragment the windows partitions that need to be resized.

From what I understand, wubi does not install grub. You will have to install from live cd to get the beloved grub.

If I had to take a wild guess why you failed at partitioning. You probably didnt have enough space on the harddisk (bytes occupying the place wubi wanted to repartition)

---

### Post by Res2216firestar on 2009-02-27
Nice call, guys. Looks like my hard disk is badly fragmented. Defragmenting now, also, my hard drive has 13GB of free space, so I think that's fine. Another thing: Both times I installed wubi, when I selected to boot into ubuntu, it did go int GRUB, first time, it ran well, second time, I had problems getting it to boot. Thanks--Sam

---

### Post by Res2216firestar on 2009-02-27
Thanks guys. Greetings from Ubuntu! Installation went great, thanks.

---

### Post by stchman on 2009-02-27
> **Res2216firestar said:**
> Hello all, I am (for the third time) attempting to use wubi from *indows XP, but while I wait for the iso to download, I would like a quick question answered: The first time I tried wubi, everything went right except the ubuntu installation, I got stuck on partitioning, it gave me no options to continue with, empty selection box, next button grayed out, nothing. The second time, I got stuck in GRUB with no way to boot, at that point I gave up. Now I would like to try again, but would like some pointers for avoiding the above, esp. the partition problem, since I think the GRUB problem was just a lemon install. Thanks--Sam

From everything I have read when you install Ubuntu via wubi you are exposing it to the weaknesses of the NTFS file system.

I recommend you install Ubuntu on it's own partition.

---

