---
title: "USB stick not mounting"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by The Swan Knight on 2009-01-05
Hey, I've been a lurker here for a year (as long as I've had Ubuntu), and I have to say that the community here is top notch. However, I have a question: I stick in my kingston 1gb USB stick, and I get this message: "Cannot mount volume. Invalid mount option when attempting to mount the volume "KINGSTON""

any help would be appreciated, thanks!

---

### Post by pyromanic123boom on 2009-01-05
What are you trying to boot on the drive?

---

### Post by The Swan Knight on 2009-01-05
I'm looking to reinstall Ubuntu, so im going to put syslinux and HH iso on it.

How did you know i was going to boot something from it?

---

### Post by HermanAB on 2009-01-05
Schticks are automounted by HAL in /media, if there is no entry for the device in /etc/fstab.  There is also a file lurking in /media called .hal-mtab.  You can see it with "ls -al /media".  

If the schtick worked before, then there may be a bad entry in .hal-mtab or in /etc/fstab.  Edit those files and see what is going on in there.

Note that if the schtick has never worked before, then it may be unformatted / corrupted.  In that case, you need to run mkfs.vfat and format the device before you can again mount it.

Hope that helps!

Herman

---

### Post by pyromanic123boom on 2009-01-05
> **The Swan Knight said:**
> I'm looking to reinstall Ubuntu, so im going to put syslinux and HH iso on it.

How did you know i was going to boot something from it?

I guessed, I don't know ; )

Easiest thing to do:  open gparted, (terminal) find it there, and reformat it to a partition that will work for what you're doing. Then any errors, etc., will be cleared away.

---

### Post by The Swan Knight on 2009-01-05
Ah yes, but I have no internet as my wifi adapter isn't working yet. 

How am I supposed to mkfs.vfat when i can't locate the device?

Is it possible to install Ubuntu from a flash card rather than a USB stick?

---

### Post by pyromanic123boom on 2009-01-06
Oh, no Internet...not as bad as when I had still had dial-up a few years ago. That sucked

Locating the device:  When you plug it in, I know it gives you an error, but if you open gparted in the terminal (or it's System-->Administration-->Partition Editor), does it show up there? It should be a drop-down list with your volume in it. You'll know it's the flash drive by the size, if it's there.

As long as it's a storage media with enough space, and booted through USB (card reader?), it should work. CDs will always work as well, if you've got a burner. I know you used to be able to order discs for free from Canonical as well, although it takes like 6 weeks and I'm sure you don't want to wait that long.

---

### Post by coati on 2009-01-06
What command would one use to open gparted in the terminal?Thanks for your help,this thread is similar to a problem I am having.

Sorry I did not mean to hi-jack the thread just thought it would be easier than starting another

---

### Post by coati on 2009-01-06
:KS:o

---

### Post by cometa2k7 on 2009-01-07
To find GParted, just go to 'System > Administration > Partition Editor'

If you can't find it there, just open a terminal and do:```
sudo apt-get install gparted
```

Then check 'System > Administration > Partition Editor' again,

---

### Post by Captain_tux on 2009-01-07
> **coati said:**
> What command would one use to open gparted in the terminal?Thanks for your help,this thread is similar to a problem I am having.

Sorry I did not mean to hi-jack the thread just thought it would be easier than starting another

> **cometa2k7 said:**
> To find GParted, just go to 'System > Administration > Partition Editor'

If you can't find it there, just open a terminal and do:```
sudo apt-get install gparted
```

Then check 'System > Administration > Partition Editor' again,

Yes, that's correct... and to open GParted from a terminal once it's been installed, just type **gparted** at the command prompt.

---

