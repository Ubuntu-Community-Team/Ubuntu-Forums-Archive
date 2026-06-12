---
title: "fixing MBR after wrong removal of linux"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by sp-1070 on 2011-01-14
So you did what hundreds have done before you you did it wrong.
Situation A you had a dualboot but uninstalled linux wrong so you cant boot no more.

Solution pop in a windows cd or bootable usb (use wintoflash) let it start all the way and the press R for recovery console when it tels you.

you hit enter and youre in a prompt and it tells you to select wich windows you want to fix looks like this

1(C:\windows)

if you have more there will be more but well do it for one seeign youll only have to fix one.

itl ask a password if you had one put that in if you had none hit enter.

then you are in the console go like this 

fixboot 
it asks if youre sure of course we are

fixmbr
again are you sure

hit escape
get the disc and usb out.

and it should now start just fine again.

Alternative : Do a clean install.
Clean installations are always nice the have a good feel to them beign clean to do this there are 2 ways

Way 1 :The way of the ninja 

(Why ninja ? cause its stealthy you get to keep youre stuff)

Make a live disc/usb
Start partition magic.
Make a partition for youre installation.
Mount the hdd and put evrything you want to keep in a nice order on the right partition.

Now start the process discribed above except we dont go to repair you go to isntall a fresh one.
Install on the empty partition (i usually just compare size partition for install xp for an instance i always do 4gig's)

install
boot 
enjoy 

or you format the damn thing and then install you loose evrything wich can be fine if you want to start it all over wich i dont.

Hope it helps see ya bye bye:popcorn:

---

### Post by oldos2er on 2011-01-14
> or you format the damn thing and then install you loose evrything wich can be fine if you want to start it all over wich i dont.

Or you could've backed up your data before you even started. Unfortunately, installing an operating system and then removing it is not the same as installing and removing an application. Maybe someday it will be, but we're not there yet.

---

### Post by wep940 on 2011-01-14
Or even better yet - BEFORE you wipe out linux, boot Windows and download the free program MBRFIX (get it from downloads.com).  You have to unzip the file then run MBRFIX.   Read the readme html file first.  This program will restore the MBR so it only boots Windows.  Then, just simply use a LiveCD and remove the Linux partitions with parted or gparted.

---

### Post by sp-1070 on 2011-01-17
true but i do it like this these days a partition for youre operating system and the rest on other partitions wich makes it quite easy to remove one operating system without loosing work it does cost some time to get the hang of it but when you found the way you want it it works just fine

---

### Post by sp-1070 on 2011-01-17
you tried it that way ?? does that actually work ??

---

### Post by Megaptera on 2011-01-17
> **wep940 said:**
> Or even better yet - BEFORE you wipe out linux, boot Windows and download the free program MBRFIX (get it from downloads.com).  You have to unzip the file then run MBRFIX.   Read the readme html file first.  

I've not seen that before so I took a look and it seems to be aimed at advanced users.

Quote from download.cenet.com should be noted and I've taken the libery of adding a hint of bold! :D
"This handy application manages your master boot record (MBR), but** the interface and program complexity render it appropriate for advanced users only**. MBRFix's command-line-executable interface has 13 functions that are easily listed with the /? option. The utility was designed to save an MBR to a file for transfer or backup. Drive-partition information is easy to get and delete with two command-line arguments. Advanced users will find it simple to read, write, or generate drive signatures with the proper arguments. The included HTML document page lists the arguments but expects users to understand their use. MBRFix is a tiny executable and operates quickly; most operations are completed in a few seconds. **However, users can accidentally delete partitions and important data. Accordingly, we highly recommend this invaluable freeware tool only for system techs and advanced users who often install operating systems and switch out drives**."

---

### Post by wep940 on 2011-01-18
Not that complicated - if you have a single hard drive you simply open the command line in Windows and type:
 
mbrfix /drive 0 fixmbr
 
If you have more than 1 hard drive, you just need to know which is the boot drive.
 
Nothing complicated about that - the worst I can say is it dangerous if you don't know the boot drive.
 
I've used this MANY times, both in returning dual-boot systems to just Windows only, and after times when I somehow messed up the MBR.  It does work, works great, and is a simple fix.

---

### Post by Megaptera on 2011-01-20
I too prefer the fixmbr method using Windows disc as supplied with laptop. I was amazed the first time that I did it that such a simple few steps worked!

---

