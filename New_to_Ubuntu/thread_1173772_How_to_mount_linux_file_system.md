---
title: "How to mount linux file system"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ravi_buz on 2009-05-30
i installed and removed opensuse and now i cant boot intoo ubuntu.
when i booted using live cd i see that my ubuntu file system in in lmv2 format
how can i mount it
Here is a screen shot
[http://ubuntuforums.org/attachment.php?attachmentid=115689&d=1243664638](http://ubuntuforums.org/attachment.php?attachmentid=115689&d=1243664638)

---

### Post by shaoxiao on 2009-05-30
I don't know .Wish other people can help you ! Good luck !

---

### Post by bacardiandwatermelon on 2009-05-30
Ummm I maybe wrong but I think it would be something like this if i.e. the filesystem was called sda1

```
sudo mkdir /media/disk1
sudo mount /dev/sda1 /media/disk1
```

---

### Post by blueridgedog on 2009-05-30
Sda1 appears to be a part of a prior Linux Volume Manager set which may have included other parts.  Sda4 appears to be a Linux file system and is set to boot.  Have you tried mounting that and seeing what is there?

---

### Post by madmaxou on 2009-05-30
> **shaoxiao said:**
> I don't know .Wish other people can help you ! Good luck !
lol...

---

### Post by ravi_buz on 2009-05-30
> **bacardiandwatermelon said:**
> Ummm I maybe wrong but I think it would be something like this if i.e. the filesystem was called sda1

```
sudo mkdir /media/disk1
sudo mount /dev/sda1 /media/disk1
```

ubuntu@ubuntu:~$ sudo mkdir /media/disk1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/disk1
mount: unknown filesystem type 'LVM2_member'

---

### Post by ravi_buz on 2009-05-30
ubuntu is in 28gb partition and i am unable to mount it

---

### Post by Paqman on 2009-05-30
Did you originally set Ubuntu up as an LVM? Or is that the leftovers from your OpenSUSE install?

---

### Post by b@sh_n3rd on 2009-05-30
> **ravi_buz said:**
> ubuntu@ubuntu:~$ sudo mkdir /media/disk1
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/disk1
mount: unknown filesystem type 'LVM2_member'

The only way to get sda1 in working order is to reformat it in ext2/ext3. What you've got to do is, copy whatever you've got in that filesystem into a separate drive, reformat that to let's say, ext3, and then recopy everything that you backed up. I'm not sure if this will work or not but if every single item in that partition (up to a hair line :D) is copied, it *should*...

What I see is, you've got a 27.95 partition for Ubuntu? where did you install openSUSE in that partition table? that would help. Remember, the drive should ***NOT*** be mounted when reformatting. If it is, you'll get a key ahead of the partition name..

(your partition table reminds me of my sister's messy table..can't stand it :D..no offense!!)

**EDIT:** oh wait a minute...you can't copy that can you? can't mount? try to mount it with the openSUSE LiveCD..

---

### Post by ravi_buz on 2009-05-30
This is the new table ,i just installed ubuntu again (in the highlighted one) i just need to copy some files from sda1 .is it possible ,and i installed suse in another HDD and now removed it how could that corrupt this hdd [ATTACH]115744[/ATTACH]

---

