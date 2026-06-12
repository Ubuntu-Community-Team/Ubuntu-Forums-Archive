---
title: "seem to lost massive amount of space"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by kapi on 2009-03-25
I have an 80 gb laptop, it takes 2gb to load ubuntu itrepid ibex. The software is minimal really with gimp, inkscape, couple of browsers, open office etc.

and yet when I go to properties in file system it says I only have 11.2gb left. 

Any suggestions please

---

### Post by kanikilu on 2009-03-25
Did you just recently install?

How are your partitions setup? **sudo fdisk -l**

What does **df -h** output?

Have you used baobab or filelight to get a graphical representation of disk usage?

---

### Post by kapi on 2009-03-25
woa, so many questions, thanks. 

I haven't installed anything lately, infact I need to get rid of virtual machine but it won't let me delet a snap shot (but thats another story)

i installed ubuntu and only have on computer 'file system' and cd/dvd drive.

boa thingy no I havent i just look at properties of the file system, but will try now as we speak

thanks

---

### Post by kapi on 2009-03-25
the df -h out put is:

craig@craig-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G   56G   12G  84% /
tmpfs                 727M     0  727M   0% /lib/init/rw
varrun                727M  224K  727M   1% /var/run
varlock               727M     0  727M   0% /var/lock
udev                  727M  2.7M  724M   1% /dev
tmpfs                 727M  500K  726M   1% /dev/shm
lrm                   727M  2.0M  725M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
/dev/sdb1             466G   28G  438G   6% /media/LaCie
craig@craig-laptop:~$ 
craig@craig-laptop:~$

---

### Post by davec64 on 2009-03-25
Hvae a look in your home folder with nautilus, but go up to view and select show hidden files, you haven't got something very larger lurking there have you?

---

### Post by LowSky on 2009-03-25
See below the thing I highlighted red, its your hard drive, it say you have used 56GB of Data out of 71 GB availible (which is correct because 80GB is never the actual amount -its usually lower)

So I don't know what you have actually installed on you machine but something is taking up 56GB, and because Linux save like 5-10% of the hard drive space availible, you only haiving 12GB is about right.

In the future please use code tags it makes reading this stuff so much easier

```
the df -h out put is:

craig@craig-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[COLOR="Red"]/dev/sda1              71G   56G   12G  84% /[/COLOR]
tmpfs                 727M     0  727M   0% /lib/init/rw
varrun                727M  224K  727M   1% /var/run
varlock               727M     0  727M   0% /var/lock
udev                  727M  2.7M  724M   1% /dev
tmpfs                 727M  500K  726M   1% /dev/shm
lrm                   727M  2.0M  725M   1% /lib/modules/2.6.27-11-generic/volatile
overflow              1.0M   36K  988K   4% /tmp
/dev/sdb1             466G   28G  438G   6% /media/LaCie

```

---

### Post by halitech on 2009-03-25
not sure if this will work since your home partition is in / but try it

```
sudo df -h /home/craig
```

also look in /var/log and see how much is in use there. I'm thinking its your VM stuff thats taking room

---

### Post by LowSky on 2009-03-25
It probably is all those snapshot you said you take.

Because  the file is so big it cant be moved to the trash, so you will have to permanently remove the file, try holding down Shift+delete to remove the file, Also you might need sudo access to the folder.
to do so open a terminal and type

```
gksu nautilus
```

---

### Post by kanikilu on 2009-03-25
> **halitech said:**
> not sure if this will work since your home partition is in / but try it

```
sudo df -h /home/craig
```

also look in /var/log and see how much is in use there. I'm thinking its your VM stuff thats taking room I don't think that's going to work since df reports filesystem usage, and /home is not it's own partition on his machine.

Instead, you *could* use ```
du -h ~/
``` but that's going to spit out a lot, most likely, so either pipe it to more or redirect to a file to view later:
```
du -h /home/craig | more
- or -
du -h ~/ > ~/Desktop/du.txt
```

But, that's a bit cumbersome when you can use the GUI tools to do the same thing (and get a nice graph/chart to boot) ;)

---

### Post by linuxisevolution on 2009-03-25
> **kapi said:**
> woa, so many questions, thanks. 

I haven't installed anything lately, infact I need to get rid of virtual machine but it won't let me delet a snap shot (but thats another story)

i installed ubuntu and only have on computer 'file system' and cd/dvd drive.

boa thingy no I havent i just look at properties of the file system, but will try now as we speak

thanks

Your virtual machines take up a lot of space. To remove them delete their virtual drives. If you have an 80gb virtual drive it's gonna take around 40gb of your disk space. What are the sizes of your virtual machines?

---

### Post by halitech on 2009-03-25
I wasn't sure if it would or not, works for me but I always make a seperate /home partition in case I mess up :)

---

### Post by kanikilu on 2009-03-25
> **halitech said:**
> I wasn't sure if it would or not, works for me but I always make a seperate /home partition in case I mess up :) Me too ;)

As suggested, the likely culprit is your VM's. Do you use VMWare or VirtualBox, or...? I use VirtualBox and by default the disk images are in ~/.VirtualBox, so find where your images are and see how much space they are taking...

---

### Post by kapi on 2009-03-25
Thankyou, Thankyou, Thankyou, Thankyou, Thankyou.

did I say thankyou. I installed filelite (not bad little ap) but the real trick came as you guys suggested by viewing hidden files.

I accessed the virtualbox folder and deleted the contents of the snapshot folder and Woa! huge saving.

Now have 50GB spare

I really appreciate the Ubuntu forum and the help everyone provides

Thanks

---

