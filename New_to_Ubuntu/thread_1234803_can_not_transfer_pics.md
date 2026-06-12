---
title: "can not transfer pics"
date: 2009-08-08
forum: New to Ubuntu
---

### Post by Bill99fan2 on 2009-08-08
can not transfer pics from cd keeps telling me Cannot mount volume.

---

### Post by Liolikas on 2009-08-08
Next time write more interesting topic name.
Try:
```

sudo mkdir /mnt/cdrom
sudo mount /dev/cdrom /mnt/cdrom

```
and post here what happens.

---

### Post by credobyte on 2009-08-08
Try:
```
sudo mkdir /media/cd && sudo mount /dev/cdrom /media/cd
```

---

### Post by Bill99fan2 on 2009-08-08
where do i put this sorry i'm very new to ubuntu

---

### Post by Sef on 2009-08-08
> where do i put this sorry i'm very new to ubuntu


Applications > Accessories > Terminal

Just copy and paste the command.

No need to apologize.  We were all noobs at one time.

---

### Post by credobyte on 2009-08-08
> **Bill99fan2 said:**
> where do i put this sorry i'm very new to ubuntu

You need to paste it into Terminal ( see Sef's post ) - if you are/were a Windows user, it's pretty much the same as cmd ( MSDOS ) :)

---

### Post by Bill99fan2 on 2009-08-08
tried them none worked still having same problem i do have dvd rw drives this is the error

                   Invalid mount option when attempting to mount the volume 'UDF Volume'.
i get this when inserting a disk

---

### Post by credobyte on 2009-08-09
Post the output of ( type it in terminal ):
```
uname -a
```

---

### Post by CaptainMark on 2009-08-09
credobyte - terminal almost the same as msdos command line, uurgh almost cried a little bit when i read that. :(

---

### Post by credobyte on 2009-08-09
> **CaptainMark said:**
> credobyte - terminal almost the same as msdos command line, uurgh almost cried a little bit when i read that. :(

Command line is command line, no matter how it's called ( msdos, terminal, beatbox .. unless you know what it is, who cares ? ) :rolleyes:

---

### Post by Bill99fan2 on 2009-08-09
did not work should i just go get a new dvd rewriter or will i have the same problems

---

### Post by halitech on 2009-08-09
was the disk written in windows? if it was, was it closed (ie. finalized) after writting?

---

### Post by leedrew on 2009-08-09
**sorry for the bold but can't see so well. Anyways I was wondering if you put a different cd in the drive does it come up with the same error message?**
**if so try updating the driver for the cdrom. **
**I don't know am a nooby somewhat but like hardware alot**

---

### Post by JohnFH on 2009-08-09
> **Bill99fan2 said:**
> did not work should i just go get a new dvd rewriter or will i have the same problems

Don't do that.  You will still have the same problem.

It's hard to say how to fix your problem because we don't know a lot about it.  Choose Applications > Accessories > Terminal and then type the following commands and post the results.

```

uname -a
cat /etc/fstab
sudo mount /dev/cdrom

```

Also the following thread might be relevant to your problem:
[http://ubuntuforums.org/showthread.php?t=650697&page=4]("http://ubuntuforums.org/showthread.php?t=650697&page=4")

---

### Post by Bill99fan2 on 2009-08-09
i have used the disk before in to install pics off it i reinstalled Ubuntu and now i am having this problem with both my dvd burners

---

### Post by halitech on 2009-08-09
is it only this 1 disk that won't read? 

when you say you have used the disk before, do you mean the actual drive or the disk(media)?

---

### Post by Bill99fan2 on 2009-08-09
this is the message i get when i enter that
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Bill99fan2 on 2009-08-09
halitech its more than 1 disk and i have used the cd before

---

