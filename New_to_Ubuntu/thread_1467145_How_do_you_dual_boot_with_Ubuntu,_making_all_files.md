---
title: "How do you dual boot with Ubuntu, making all files readable by both OS's?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by Joker98 on 2010-04-30
Right now, I have Windows XP installed. I'm about to install some version of Linux (probably Ubuntu 10.04).

How can I make sure all files from Windows XP will be available for use (including text documents, movies, music, etc) in Ubuntu?

---

### Post by ScottinSoCal on 2010-04-30
> **Joker98 said:**
> Right now, I have Windows XP installed. I'm about to install some version of Linux (probably Ubuntu 10.04).

Congrats.

The question you asked here is not the question in your subject, so one at a time:

> How can I make sure all files from Windows XP will be available for use (including text documents, movies, music, etc) in Ubuntu?

Your XP installation uses NTFS, and that's readable by default, so no problem. To write to it is pretty easy, too.

> How do you dual boot with Ubuntu, making all files readable by both OS's?

As far as I know, this can't be done. Linux is going to go into a separate partition, and it will be formatted with some flavor of a Linux file system (EXT3, EXT4, etc), and not the Windows NTFS file system. Microsoft software doesn't play well with others, and they don't include anything to allow you to read/write to non-Microsoft file formats.

---

### Post by Joker98 on 2010-04-30
But if I install Ubuntu 10.04, I will be able to access my Windows files (even if it won't work the other way around)?
Cool, thanks.

I just want to listen to music in Linux.

---

### Post by phrostbyte on 2010-04-30
Windows can read ext2 I believe with a custom driver. I wouldn't recommend downgrading to ext2 just for that though.

Linux however, can read NTFS (and most OSes filesystems) just fine.

---

### Post by philinux on 2010-04-30
> **Joker98 said:**
> But if I install Ubuntu 10.04, I will be able to access my Windows files (even if it won't work the other way around)?
Cool, thanks.

I just want to listen to music in Linux.

Accessing windows files from ubuntu no problem.

Accessing ubuntu from windows you need to see this.
[http://ubuntuforums.org/showthread.php?t=1181698](http://ubuntuforums.org/showthread.php?t=1181698)

---

### Post by phrostbyte on 2010-04-30
Check the side bar in Nautilus (the file manager in Ubuntu). There should be an HDD entry that is basically your Windows installation. You should be able to read and write to it without issue.

---

### Post by jonnny_j22 on 2010-04-30
Hey Every one I was literally about to ask the exact same question, so thought I'd post in here to keep the threads down!

If I understand about ntfs, does that mean it would be possible to create a separate partition for windows (to store the contents of my documents) and then use ubuntu to acces the music from this partition, as well as saving music to it. 

I'm new so I don't know the correct language to ask - basically can i create a third partition for both OS to share?

---

### Post by nicfallenangel on 2010-04-30
> **phrostbyte said:**
> Windows can read ext2 I believe with a custom driver. I wouldn't recommend downgrading to ext2 just for that though.

The ext2 driver for windows does read ext3. **However:** it does not respect permissions (root ownership, read only, etc.). Linux on the other hand does read NTFS really well and I have used it to write for years with no issues.

---

### Post by J V on 2010-04-30
You can also share your home directory with windows by turning your folders into symlinks...

~/Pictures symlinks to /mnt/windows/Users/YourUserName/My Pictures

This means when something saves on linux it *actually* saves on the windows partition (Making them both readable)

---

### Post by madjr on 2010-04-30
you can create a secondary NTFS partition that can be used to store stuff you want both OS to use

example 3 partions:
-Windows partition (NTFS)
-Ubuntu (ext4)
-secondary backup (NTFS or fat32)

you will have time to do it later even after install , so when you feel the need

---

