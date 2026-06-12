---
title: "Make directory and remove directory mess"
date: 2011-02-16
forum: New to Ubuntu
---

### Post by ehobson on 2011-02-16
Hi

I'm in a frustrating mess at the moment. In my efforts to auto mount an ntfs partition I created several directories and then removed them, now I can't seem to find any of the data in the partitions.

So what I did was the following:

1. I wanted to auto mount an nfts partition. I used the code:
"sudo fdisk -l"

I was presented with the locations of my partitions and I selected the incorrect one, I selected the one that contained my bootfiles for windows:
"/dev/sda2"
in the list there was also a partition contiaining my data:
"/dev/sda5"
That is the partion I wanted to auto mount.

2. I attempted to auto mount "/dev/sda2" using:
"sudo gedit /etc/fstab"

3. I changed the fstab file so that it contained the code:
"/dev/sda2       /home/Data ntfs-3g  defaults  0   0"

4. I then created the mount point:
"sudo mkdir /home/Data"

5. I checked the /home/Data file and found that I had been working with the wrong partition.

I then repeated the procedure for /dev/sda5 and saw that this was the correct partition. I called the directory:
"sudo mkdir /home/data."

Now my problem I wanted to remove the directories that I had created. I used this code:
"*********"
"*********"

This removed the directories and when I rebooted I could see them listed in my places menu. Unfortunately all the files that they contained were gone.

Did I do what I think I did and delete them completely? My windows doesn't start now, which got me real worried. The good news is that I do have a backup of all my data.

Is there anyway to undo what I did without me reinstalling everything, including windows and linux?

Thanks

---

### Post by oldos2er on 2011-02-16
When you use rm with the recursive flag (-R or -r), it deletes every subdirectory and all files. You could try testdisk ([http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)) but I can't tell you with any certainty that you'd get all your files back.

---

### Post by Monotoko on 2011-02-16
Were they mounted at the time when you removed those directories? If so you have lost it, but it's a good thing you had the data backed up, most people don't.

---

### Post by ehobson on 2011-02-16
The partition with my data was mounted at the time. I knew I shouldn't have been so keen to try change things. Patience is the key, together with some more reading. I bumped into a nice post about setting up auto mount while in my panicked state. Thanks for the input.

---

### Post by iponeverything on 2011-02-16
for future reference:

```

rmdir

```

would have safe/correct command to use.

---

