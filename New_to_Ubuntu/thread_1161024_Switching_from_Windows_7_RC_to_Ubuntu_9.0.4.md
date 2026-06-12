---
title: "Switching from Windows 7 RC to Ubuntu 9.0.4"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by MPD51 on 2009-05-16
Hey everyone.

I just gave Windows 7 a try, and although it's pretty nice, my college course (Telecommunications) mainly uses Linux, so I'm choosing to replace my Windows with pure Linux Ubuntu 9.0.4 64 bit to better immerse myself in it (keep my skills sharp).

I've only had virtualized Linux (via Virtual Box, centOS and Fedora) run before so this is a new problem for me.

With my data all backed up, I can go ahead and do a fresh install. With Windows, it allows me to format the HDD with NTFS. I haven't found such a utility when installing through the Ubuntu disk. When I reach the installation point pertaining to selecting the partition mount point, the selection area is blank. I see the headers, and the buttons at the buttom (although they are all greyed out except for Quit, Back, and Next).

What I'm asking in a nutshell is: what would it take for Ubuntu to detect a valid mount point? Do I have to use a particular utility to format the whole HDD as ext3 (or whichever it uses) before I can install Ubuntu?

Thanks in advance.

---

### Post by wanchai on 2009-05-16
During the installation it should definitely ask you about the partitioning of the system. You need to decide how many partitions you want, their size, mount point or swap and which file system. How this exactly works depends on the method you're using. The graphical install, i.e. using a desktop aka live CD, and text mode install look different, but they need the same info.

Have a look at [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall) for the graphical install. Step 8 shows the partitioning. By the way, I always go with "manual".

Some more infos: [https://help.ubuntu.com/9.04/installation-guide/i386/index.html](https://help.ubuntu.com/9.04/installation-guide/i386/index.html)


By the way, a lot of people would lecture you to google your problem before posting. And your topic doesn't match the question at all. I only looked at your post because I was curious what you'd say about Win7. Anyhow, welcome to the forums and have fun with Ubuntu! It's a good choice.

---

### Post by Paddy Landau on 2009-05-16
It's been a while since I did this, but the Ubuntu Live CD (I presume that's what you're using?) does it all for you. It should prompt you to create two partitions; your main partition and your swap partition.

The default format is for the main partition is ext3 for version 8 (Hardy or Intrepid) and ext4 for version 9 (Jaunty). The swap partition should be roughly the size of either your RAM or double your RAM (depending on whom ask!).

You can, if you prefer, divide your main partition into two: One for the root (/), which needs to be about 20-30Gb, possibly not even that much, and the other for your home (/home), taking the rest of the space.

---

### Post by hyperdude111 on 2009-05-16
> **Paddy Landau said:**
> It's been a while since I did this, but the Ubuntu Live CD (I presume that's what you're using?) does it all for you. It should prompt you to create two partitions; your main partition and your swap partition.

The default format is for the main partition is ext3 for version 8 (Hardy or Intrepid) and ext4 for version 9 (Jaunty). The swap partition should be roughly the size of either your RAM or double your RAM (depending on whom ask!).

You can, if you prefer, divide your main partition into two: One for the root (/), which needs to be about 20-30Gb, possibly not even that much, and the other for your home (/home), taking the rest of the space.

EXT3 is still jaunty default although EXT4 is an option

---

### Post by Paddy Landau on 2009-05-16
> **hyperdude111 said:**
> EXT3 is still jaunty default although EXT4 is an option
Thanks, I didn't realise. I understand that some people have had problems with ext4, but I don't know whether this was resolved.

I don't know if [Ext2 File System Driver for Windows]("http://sourceforge.net/project/showfiles.php?group_id=43775") or [Ext2 IFS Driver]("http://www.fs-driver.org/") for Windows can read the new ext4.

---

### Post by hyperdude111 on 2009-05-16
> **Paddy Landau said:**
> Thanks, I didn't realise. I understand that some people have had problems with ext4, but I don't know whether this was resolved.

I don't know if [Ext2 File System Driver for Windows]("http://sourceforge.net/project/showfiles.php?group_id=43775") or [Ext2 IFS Driver]("http://www.fs-driver.org/") for Windows can read the new ext4.

These drivers read EXT3 but not EXT4.

---

### Post by MPD51 on 2009-05-28
Hey everyone,

I appreciate the suggestions, but I've yet to solve my problem.

I believe it's a driver issue, here is a photograph of what happens when I reach step 4 of the graphical install (Desktop CD):

[IMG]http://i559.photobucket.com/albums/ss32/ronnyvince/IMG_0155.jpg[/IMG]

As you can see, the table is pure blank.

Furthermore, when I just load Ubuntu from the CD and open up the partition editor, there are no drives detected.

Has anyone encountered this/know how I may proceed?

Thanks in advance.

---

### Post by wanchai on 2009-05-29
Haven't seen anything like that before. Let's assume for a moment that this is a problem with the partition manager and let's do something very simple. Boot the machine form the live CD and try:
ls -l /dev/sd*

Ok, many people would consider this trivial, but I don't know how deep you've gotten into Linux by now. Anyway, this command should list your disk drives and partitions. The first drive is /dev/sda, the second /dev/sdb, etc. If a drive is partitioned, the partitions will show up as /dev/sda1, /dev/sda2, etc.

If you do see /dev/sda, then we're good and you could try to partition this disk using fdisk, a simple non-graphical tool. Type "sudo fdisk /dev/sda". If you type "m" you'll get a list of commands. The first one to try would be "p" to print (on the screen) the current partition table. Then you can go ahead and delete and recreate your partitions. At the end you need to type "w" to commit the changes to disk.

If you don't see any /dev/sda, then, well, you're in trouble. Just for the heck of it, try ls -l /dev/hd*  In previous versions of Ubuntu, the drives were mounted as /dev/hda, but nowadays you shouldn't have any hd* anymore.

If you really don't see any of the disk drives, well, then maybe you should post something in a hardware forum with a subject that's more descriptive of your problem than this one here. It would be helpful if you would tell people what kind of hardware you are using. Hardware experts would also want to see the output of dmesg (use "dmesg > dmesg.txt" and attach the file generated).

---

### Post by MPD51 on 2009-05-29
Thanks, I have the problem solved (thanks in full part to Mike'sHardLinux).

I had to add the kernel option 'pci=nomsi' when I was booting up the Desktop CD.

Thanks for the suggestions, though. I appreciate it! =D

---

