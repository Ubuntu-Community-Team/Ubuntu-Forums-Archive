---
title: "Partial package install I think, ran out of space, now I can't logon."
date: 2010-02-10
forum: New to Ubuntu
---

### Post by laurabray on 2010-02-10
I only installed Ubuntu with 8GB because this is my first time and I've just been exploring (I didn't know any better but now I do!). But I kept installing the recommended updates/packages and finally one day in the middle of downloading/installing these updates/packages, I ran out of space. The next time I tried to boot Ubuntu, I got a strange log-in screen and a little error message in the upper right-hand corner saying the default power configurations for GNOME were incomplete and I needed to see my administrator.  When I try to log in, it's a login loop.

So here I am running a LiveCD trying to figure out if there's any way I can update my system without doing a full re-install. I've also got Vista on my machine. If I try to install packages on my LiveCD, can I fix it? I need help! Also, if this isn't possible, are all my Ubuntu files lost forever?  Is there a way to make my Linux bigger even though it doesn't have its own partition?

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
4 heads, 44 sectors/track, 2774983 cylinders
Units = cylinders of 176 * 512 = 90112 bytes
Disk identifier: 0x97646c29

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      127973    11261533+  1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *      127973     1515405   122094000    7  HPFS/NTFS
/dev/sda3         1515406     2774983   110842864    f  W95 Ext'd (LBA)
/dev/sda5         1515406     2774983   110842842    7  HPFS/NTFS
```

---

### Post by Cheezespread on 2010-02-10
I can't see a Linux partition in there .

---

### Post by laurabray on 2010-02-10
> **Cheezespread said:**
> I can't see a Linux partition in there .

I know, I installed Linux in Windows so I don't know what happened or how that works.

---

### Post by Cheezespread on 2010-02-10
You did a Wubi install , is it ?. 
Sorry . I have no clue about how Wubi works. Hopefully someone else would respond to you soon enough.

---

### Post by laurabray on 2010-02-10
> **Cheezespread said:**
> You did a Wubi install , is it ?. 
Sorry . I have no clue about how Wubi works. Hopefully someone else would respond to you soon enough.

Yes, I used Wubi.

---

### Post by sandyd on 2010-02-10
> **laurabray said:**
> Yes, I used Wubi.

open up a terminal
type this in
```

sudo apt-get clean
sudo dpkg -a --configure

```
oops hang on.
You have to run that in the wubi installation.

If you cant, your royally screwed.
Which is one of the bad things about installing w/ wubi.
You cannot expand the space you allocated using wubi.

If you can, press Control + F1 at the login screen, login, then run the above

---

### Post by SecretCode on 2010-02-11
As carlee says, there are some recovery techniques that you just can't do with a wubi installation. But there are some...

From your windows boot menu, you select Ubuntu at the bottom - as soon as you've pressed Enter, press and hold the Shift key. This should cause the "GRUB" boot menu to appear, and one of the items should look like "Ubuntu Linux ... (recovery)". Select that one and press Enter to continue booting.

Messages will scroll past, then you should get another menu where one of the options is 'resume' - choose that, and you should get to a console login prompt. Log in.

If this works, you should be able to delete some files (enough that you can boot normally and rescue your data files).

(If it doesn't work, post details and error messages.)

I assume you aren't comfortable with the command line yet, so we should take it step by step. Post the output of 
```
du -hx --max-depth 1 /
```

---

### Post by laurabray on 2010-02-11
> **SecretCode said:**
> As carlee says, there are some recovery techniques that you just can't do with a wubi installation. But there are some...

From your windows boot menu, you select Ubuntu at the bottom - as soon as you've pressed Enter, press and hold the Shift key. This should cause the "GRUB" boot menu to appear, and one of the items should look like "Ubuntu Linux ... (recovery)". Select that one and press Enter to continue booting.

Messages will scroll past, then you should get another menu where one of the options is 'resume' - choose that, and you should get to a console login prompt. Log in.

If this works, you should be able to delete some files (enough that you can boot normally and rescue your data files).

(If it doesn't work, post details and error messages.)

I assume you aren't comfortable with the command line yet, so we should take it step by step. Post the output of 
```
du -hx --max-depth 1 /
```

So I was able to use the recovery mode, I think that's what I was looking for!  I selected an option to clear space, then went to the last known good configuration, basically.  Here's the output to your code:

```
laura@ubuntu:~$ du -hx --max-depth 1 /
du: cannot read directory `/.kde': Permission denied
4.0K    /.kde
4.0K    /cdrom
0    /sys
8.0K    /boot
4.0K    /selinux
16K    /host

```

Thanks so much, you saved me!! :) Now my next project will be moving over to ONLY Linux and no Windows.

---

### Post by SecretCode on 2010-02-12
Are you now able to boot to the GUI and work with your files?

Becasue this doesn't look like you have anything left - no /home, no OS files...: 
> **laurabray said:**
> ```
laura@ubuntu:~$ du -hx --max-depth 1 /
du: cannot read directory `/.kde': Permission denied
4.0K    /.kde
4.0K    /cdrom
0    /sys
8.0K    /boot
4.0K    /selinux
16K    /host

```

I'm hoping the root (/) shown there is not the real ubuntu root...

---

### Post by laurabray on 2010-02-12
I am able to boot like normal and moved a bunch of photo files from my /home folder to my data partition so I should have plenty of room for Ubuntu.  After I posted that code, Terminal started scrolling a bunch more lines so maybe my real Ubuntu root wasn't on my original post.  But why was it saying permission denied?  All I know is, things are back to normal! Hurray!

---

### Post by SecretCode on 2010-02-12
> **laurabray said:**
> But why was it saying permission denied?

Quite often your home folder will have a few files or directories that are owned and used by 'root'. Even though they are specific to your account. Nothing to worry about.

---

