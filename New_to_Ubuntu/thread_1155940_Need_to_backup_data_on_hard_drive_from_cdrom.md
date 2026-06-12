---
title: "Need to backup data on hard drive from cdrom"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by indianajo on 2009-05-11
I damaged the ubuntu intreped ibix desktop 32 bit hard disk op system by installing wine and running psp.exe, an old version 3 utility for windows 3.1 that doesn't have an installer.  Gnome windows don't have title bars and x's and frames and stack over the system bar at the top.  So I tried to backup my data prior to reintalling the operating system. Under hard disk op system I copied and pasted a directory, pushed "write" button, file manager has an error writing to the cdrom. Maybe my 10 year old cdrom is too old to be compatible for write, maybe file manager is damaged. I'll try buying a new dvd writer, I need one anyway.  So I put the Ubuntu live disk in the cdrom, brought it up running from cdrom, tried to view my data on the hard disk, by clicking "computer" button.  It has an icon under computer, 35 mb, which is correct for my partition, but I can't find any data on it under user or anywhere else.  Couldn't find my data under "file system" either.  If I can find my data, I will buy a new DVD writer and backup my data that way, Do I lack permission as the live disk user to view my data on the hard drive? How do I get permission?

---

### Post by cholericfun on 2009-05-11
thats worrisome..
you dont need any special permissions while in the LiveCD

so not having anything showing up there is strange...

maybe go to System-Admin-Gparted 

theres a Check/fix option that might fix your filesystem so it can be read again.

---

### Post by ashmew2 on 2009-05-11
> **indianajo said:**
> I damaged the ubuntu intreped ibix desktop 32 bit hard disk op system by installing wine and running psp.exe, an old version 3 utility for windows 3.1 that doesn't have an installer.  Gnome windows don't have title bars and x's and frames and stack over the system bar at the top.  So I tried to backup my data prior to reintalling the operating system. Under hard disk op system I copied and pasted a directory, pushed "write" button, file manager has an error writing to the cdrom. Maybe my 10 year old cdrom is too old to be compatible for write, maybe file manager is damaged. I'll try buying a new dvd writer, I need one anyway.  So I put the Ubuntu live disk in the cdrom, brought it up running from cdrom, tried to view my data on the hard disk, by clicking "computer" button.  It has an icon under computer, _**35 mb,**_ which is correct for my partition, but I can't find any data on it under user or anywhere else.  Couldn't find my data under "file system" either.  If I can find my data, I will buy a new DVD writer and backup my data that way, Do I lack permission as the live disk user to view my data on the hard drive? How do I get permission?

Please tell me its 35 GB! :P
Sorry for the sarcasm. Anyhow , 

What i understood is you broke your ubuntu system and you need to backup your data to say a usb drive when you are inside a live session.

As far as i know , you could open a terminal and do :

```
sudo fdisk -l
```

Check the partition from which u want to recover the data. Let's assume its /dev/sda5

So , just do :
```

sudo mkdir /media/backup
sudo mount -t ext3 /dev/sda5 /media/backup
```

Now do :

```

cd /media/backup
ls
```

And the files SHOULD show! :D

---

### Post by indianajo on 2009-05-11
Thanks to both for responding. Askew2 you were right about 35 GB partition, sorry, I've have been doing computers since 4k was a big ram and an operating system was a 6 cm stack of folded paper tape.  (PDP11).

---

### Post by ashmew2 on 2009-05-11
> **indianajo said:**
> Thanks to both for responding. _**Askew2**_ you were right about 35 GB partition, sorry, I've have been doing computers since 4k was a big ram and an operating system was a 6 cm stack of folded paper tape.  (PDP11).

We all make mistakes sir ;)

Btw , you got that problem sorted out yet ?

---

