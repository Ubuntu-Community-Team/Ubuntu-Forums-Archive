---
title: "fsck died with exit status 4"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by libihero on 2009-02-21
My computer froze, so I shut it down by holding on to the power button, and when it restarts, it goes through a process then ends with this:

-An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root file system mounted in read-only mode.
-The root filesystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system. 
bash: no job control in this hell
root@ednan-laptop:~#

what do i type in, or do in general?
thanks!

---

### Post by whoop on 2009-02-21
Well it says to run fsck, so maybe type fsck :-)
Note, make yourself a cup of tea, it might take some time and could require manual confirmations now and then...

---

### Post by libihero on 2009-02-21
Tried it, and after a few errors, it read:

Error reading block 1245187 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>?

---

### Post by whoop on 2009-02-21
> **libihero said:**
> Tried it, and after a few errors, it read:

Error reading block 1245187 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan. Ignore error<y>?

OK, that sucks.
I wonder what happens if you type "n"

---

### Post by philinux on 2009-02-21
fsck -v

this is for verbose mode. It should offer to fix the problems.

---

### Post by libihero on 2009-02-21
after pressing "n" it read:





Error while scanning inodes (311296): Can't read next inode
e2fsck: aborted
root@ednan-laptop:~#_

---

### Post by libihero on 2009-02-21
So i tried the fsck v
and then i tried a scan no questions asked, and it said:

/dev/sda1: UNEXPECTED INCONSISTANCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
root@ednan-laptop:~#



how do i run fsck manually?
because whenever i type in fsck and try it, it doesn't work.

---

### Post by libihero on 2009-02-22
Bumpp

---

### Post by libihero on 2009-02-22
bump :(

---

### Post by libihero on 2009-02-22
bumpppppppppppp

---

### Post by deepclutch on 2009-02-22
do you got a livecd(Ubuntu)?if yes ,boot with it.then once ready ,open a terminal in Gnome Desktop(or any pseudo terminal) :
Don't mount your affected partition.
then run:
```
sudo e2fsck -fvy /dev/sdx
```where sdx is your partition number of Ubuntu harddisk installation.what this command does is to automatically fix the issues ,including bad superblocks.Have a try.
EDIT:do you know your Ubuntu hdd partition number right?If else ,use "sudo fdisk -l" and see.

---

