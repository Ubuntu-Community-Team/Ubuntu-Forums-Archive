---
title: "Dual Partition Icons"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by PPPilot on 2010-07-17
Here is a strange issue on Lucid. I had some unallocated disk space and decided to create a usable partition using gparted. I created one ext3 partition for this space and gave it the name Audio-Video. When complete I noticed that there were now two Audio-Video icons in Places and also in Computer. One has the normal hard drive icon and shows all the normal partition information when you click properties. The other icon shows the floppy drive icon and shows unknown for all information. I guess my question is, how do I get rid of the second weird icon????

---

### Post by jtarin on 2010-07-17
What other options are available upon right-clicking the floppy-drive icon?

---

### Post by PPPilot on 2010-07-17
First option is Open and since the partition is already mounted I get this error message:
```
Unable to mount location

[mntent]: line 1 in /etc/fstab is bad
mount: /dev/sdc5 already mounted or /media/Audio-Video busy
mount: according to mtab, /dev/sdc5 is already mounted on /media/Audio-Video

```Second option is Open with Other Application

There are none listed.

Third option is Copy

Nothing happens when selected.

Fourth option is Rename and selection shows this error message:

The item could not be renamed.
```
Sorry, could not rename "Audio-Video" to "Audio": Operation not supported by backend

```Fifth option is Copy to and selection shows this error message:
```
Error while copying "Audio-Video".

There was an error copying the file into /home/john/Desktop.
Can't open mountable file
```Sixth option is Mount which results in same error as Open:

It would appear that there is something wrong in fstab.

I have Karmic on another partition and booted it up and it only shows a single icon for this partition.

If I unmount this partition, this weird icon will mount it with no errors.

---

### Post by jtarin on 2010-07-17
> It would appear that there is something wrong in fstab.I agree.Open up fstab as root and comment one of the duplicate lines by placing a # at the beginning. You might post your /etc/fstab so we can confirm this.

---

### Post by PPPilot on 2010-07-17
I do not see any duplicates in here....
```
/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=ea1ee81c-62e6-42ec-bacb-4a29d01832d5 /media/ea1ee81c-62e6-42ec-bacb-4a29d01832d5 ext4 defaults 0 0
UUID=5ba2de08-7e6b-4950-b1cb-398b2f62aa6f / ext4 defaults 0 1
UUID=93c85f39-5e6c-43e5-b1b4-7965cbc4bb89 swap swap sw 0 0
UUID=a2bb21e7-efde-487c-8b2d-6e7fe019dcee swap swap sw 0 0
UUID=413cc995-105e-4637-950c-a63b5ecfc5bb /media/Secondary ext3 defaults 0 0
UUID=356e08d6-8ca6-4144-a05e-14ff175641e3 /media/Storage ext3 defaults 0 0
UUID=4d959dd2-0f50-4f77-80f8-4e791cf86697 /media/Audio-Video ext3 users 0 0

```/dev/fd0 /media/floppy0 vfat noauto 0 0
UUID=ea1ee81c-62e6-42ec-bacb-4a29d01832d5 /media/ea1ee81c-62e6-42ec-bacb-4a29d01832d5 ext4 defaults 0 0
UUID=5ba2de08-7e6b-4950-b1cb-398b2f62aa6f / ext4 defaults 0 1
UUID=93c85f39-5e6c-43e5-b1b4-7965cbc4bb89 swap swap sw 0 0
UUID=a2bb21e7-efde-487c-8b2d-6e7fe019dcee swap swap sw 0 0
UUID=413cc995-105e-4637-950c-a63b5ecfc5bb /media/Secondary ext3 defaults 0 0
UUID=356e08d6-8ca6-4144-a05e-14ff175641e3 /media/Storage ext3 defaults 0 0
UUID=4d959dd2-0f50-4f77-80f8-4e791cf86697 /media/Audio-Video ext3 users 0 0

---

### Post by jtarin on 2010-07-17
Do you have a floppy drive? No? Comment it out then reboot.Why do you have 2 swap areas?

---

### Post by PPPilot on 2010-07-17
Yes, I do have a floppy but I commented it  out and nothing changed. Even the real floppy icon is still there.

---

### Post by PPPilot on 2010-07-17
Forgot to answer about the two swap partitions. I noticed on this forum that there were a lot of problems when people upgraded to Lucid so instead of upgrading I installed Lucid in its own partition and that install created its own swap partition. So I have one from Karmic and one from Lucid. They are both used by either version and since I have only 512 Mb memory of which 32 Mb is used by my on board video, it does not hurt to have a little extra swap space.

---

### Post by jtarin on 2010-07-17
So you have Karamic and Lucid installed....side by side? Post karamics fstab.

---

### Post by PPPilot on 2010-07-18
Here is the Karmic fstab:
```
/dev/fd0 /media/floppy0 vfat users,noauto 0 0
UUID=ea1ee81c-62e6-42ec-bacb-4a29d01832d5 / ext4 defaults 0 1
UUID=93c85f39-5e6c-43e5-b1b4-7965cbc4bb89 swap swap sw 0 0
UUID=a2bb21e7-efde-487c-8b2d-6e7fe019dcee swap swap sw 0 0
UUID=413cc995-105e-4637-950c-a63b5ecfc5bb /media/sdb1 ext3 defaults 0 0
UUID=356e08d6-8ca6-4144-a05e-14ff175641e3 /media/sdc1 ext3 defaults 0 0
UUID=254ca0ec-e849-4b12-a4e9-c1bb05ff517b swap swap sw 0 0
UUID=79056955-4822-4203-b0c3-468eeb1f6468 /media/sdc5 ext4 noauto 0 0
UUID=dbb939d1-5681-4af1-9fb2-83b6bcb1c022 /media/sdc6 ext4 noauto 0 0
```

---

### Post by PPPilot on 2010-07-18
I just looked at Places a few minutes ago and now the second Audio-Video icon is gone. I guess I'll keep checking from time to time to see if it stays gone before I mark this solved. If it is solved, I do not know how....

---

