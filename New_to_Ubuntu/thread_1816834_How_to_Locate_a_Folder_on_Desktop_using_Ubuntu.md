---
title: "How to Locate a Folder on Desktop using Ubuntu?"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by Michael_D_E on 2011-08-02
I am trying to rescue a folder that contains many files from the DESKTOP of a Motion Computing Tablet PC. Windows XP Professional was caught in a "BOOT LOOP" and the tech department recommended that I try Ubuntu from a LiveCD to boot the computer and locate the folder and copy it to a USB stick before wiping the computer clean and reinstalling the operating system.

I downloaded Ubuntu 11.04 and burned an ISO disc and after trying a few options under F6 I finally got the program to run after checking "acpi=off".

Now it is running, but I can't find any of the files on the hard drive... what I seem to be seeing is a new folder structure that has nothing in it...

I hope someone here can help me find the way to locate and copy a folder with files from the existing HD to a USB Stick...

Thank you!

---

### Post by skatinjj on 2011-08-02
You need to mount your hard drive first.  

If you click on Places at the top and do not see your hard drive then you will have to follow these steps.

First run this:

```
sudo fdisk -l
```

to get a list of the drive and partitions.

Now, they display as /dev/sdX where x is a b c and so on and the number indicates partition.

If the drive you are trying to recover is the only hard drive or the first hard drive then it will be /dev/sda# (replace # with the partition number, probably 1)

Next run:

```
sudo mount /dev/sda# /mnt
```

to mount the drive to your /mnt directory.  Of course replacing # with the correct partition number.

Now you have to do the same for your USB drive if it doesnt load automatically.

Now the drives should be visible on the Desktop and in the Places menu.

---

### Post by skatinjj on 2011-08-02
Any questions or concerns you can always post the results of fdisk here in code tags and we can assist you more directly.

---

### Post by Michael_D_E on 2011-08-02
Thank you for the info... a few minutes ago i noticed something called "60 GB Filesystem" under places and it turns out to be everything that is on the computer... now I am trying to locate a folder on the "Desktop" that my wife put there, but I don't actually see any folders on the "Desktop"... I will keep searching and once found I will mount the USB Stick and use your method if it doesn't find it automatically.

Thank you!

---

### Post by Michael_D_E on 2011-08-02
Problem Solved! USB mounted automatically and I found the folder in Documents & Settings, Michael, Desktop...

I like this UBUNTU.

---

### Post by skatinjj on 2011-08-02
Are you trying to recover files that were saved to the desktop of your Windows installation?

If so, the directory your looking for is documents and settings. There you will see a list of folders that are named after each user in addition to all users and default user.  In each folder that is named after a user is their my documents.

---

### Post by skatinjj on 2011-08-02
> **Michael_D_E said:**
> Problem Solved! USB mounted automatically and I found the folder in Documents & Settings, Michael, Desktop...

I like this UBUNTU.

Glad you got it solved.  If you have not already, please mark the thread as solved using thread tools.

---

