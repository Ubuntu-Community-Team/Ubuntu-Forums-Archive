---
title: "OS crashes with both DVD drives in use"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-04-04
i set up my computer the other day with 2 dvd drives. both are connected to a single IDE cable. 
(*when i installed the drives, i really had to pull the cable to make it stretch to reach the DVD drive, because the cord was kinda short. it worked though)

everything worked fine for a day. i would extract music off one cd while examining the contents of another. all of the sudden, after putting (gasp) a cd in **both** drives, rhythmbox crashes, the mouse freezes, and the entire system crashes.

#1 now correct me if i'm wrong, but isn't one of the big advantages of linux supposed to be stability? i would expect a windows machine to crash, not linux.
if all services really are connected to the OS using "pipes", to promote stability, the HAL service should've crashed, but not the entire operating system. :?

#2 i don't think this is a hardware issue, because both drives work fine as long i'm only using one of them at a time. if it were a break in the wire or a loose connection, one of the drives wouldn't work at all. 

this happened spontaneously. that is, i was just listening to music one minute and it crashed, without me changing any configuration.

erm... how do i go about fixing this? :-s

---

### Post by asuastrophysics on 2009-04-04
UPDATE

computer can't seem to start with a cd in one of the drives. if one of the drives has a cd in it at login, it seems like HAL just stops. i get a background picture and a frozen "loading" mouse.

what is going on?

---

### Post by ds_shellback on 2009-04-04
Hmm, not much to go on here, but.

I assume you set master/slave by jumper on the drive (explicitly set _:-k:-k:-k:-k_ cable select).

The IDC connectors used on ribbon cables don't take kindly to being stretched since the connection is made by piercing the insulation without stripping back to the bare conductor. Might be advisable to get a longer cable.

Just a thought

---

### Post by asuastrophysics on 2009-04-04
yeah i keep thinking it might be the cable. seemed too spontaneous to be software-related.

(just out of curiosity) what about stability though? isn't the linux OS supposed to isolate this issue from the rest of the kernel?
(i read this somewhere; something about pipes, or pipelines to other applications)

i think if this were to happen in windows, it would be the "blue screen of death", (stop error) which is usually an I/0 error. 

Why does linux just freeze?

---

### Post by asuastrophysics on 2009-04-04
i pulled out the IDE cord and tested every wire for continuance. all of them passed. i can also boot up the liveCD no problem. 

what else could this be??? obviously NOT a hardware issue

 until then i can't use any of my cd drives grrrrrr....

](*,)](*,)](*,)](*,)

---

### Post by Racecar56 on 2009-04-04
[SIZE=4][COLOR=Red][SIZE=2][COLOR=black]Does it act weird in any other way?[/COLOR][/SIZE][/COLOR][/SIZE]
If it does, maybe your installation is corrupt.
If it is, maybe you should (back up your /home's files if they aren't already and) do a reinstall.
[SIZE=4][COLOR=Red]WARNING: This whole post is a thought.
[/COLOR][/SIZE]

---

### Post by asuastrophysics on 2009-04-04
no i haven't had any other real problems. i just reinstalled the OS four days ago.

should i try to look under fstab? maybe conflicting mount points?

---

### Post by Racecar56 on 2009-04-04
> **asuastrophysics said:**
> no i haven't had any other real problems. i just reinstalled the OS four days ago.

should i try to look under fstab? maybe conflicting mount points?

Good idea.

---

### Post by asuastrophysics on 2009-04-04
This is the output of fstab with both cd drives unmounted:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=974ac55a-081b-49be-8db8-586081465800 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=516a3e83-6efb-460c-a982-69ce35a761d5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

This is bazaar because only one of my drives is in here; **/dev/scd0**
The other is for some reason missing.

---

### Post by crjackson on 2009-04-04
> **asuastrophysics said:**
> 
(just out of curiosity) what about stability though? isn't the Linux OS supposed to isolate this issue from the rest of the kernel?
(i read this somewhere; something about pipes, or pipelines to other applications)

i think if this were to happen in windows, it would be the "blue screen of death", (stop error) which is usually an I/0 error. 

Why does linux just freeze?

It does indeed sound like a hardware issue. Linux is VERY stable. I have 2 DVD Burners connected to my system (see specs below). I can burn 2 separate DVD movies (full speed) at the same time while listening to MP3's and surfing the web. I've done this many times and never produced a coaster or a error, or a lock-up, or even a slow down.

Windows can't do this on the same machine.

---

### Post by Racecar56 on 2009-04-04
> **asuastrophysics said:**
> <snip>
This is bazaar because only one of my drives is in here; **/dev/scd0**
The other is for some reason missing.

That is weird. Definitely weird.

> **crjackson said:**
> It does indeed sound like a hardware issue. Linux is VERY stable. I have 2 DVD Burners connected to my system (see specs below). I can burn 2 separate DVD movies (full speed) at the same time while listening to MP3's and surfing the web. I've done this many times and never produced a coaster or a error, or a lock-up, or even a slow down.

Windows can't do this on the same machine.

I tried opening 200 tabs in Windows on my really souped-up PC and it crashed immediately, while on my 2+ year old laptop with less than half as much stuff as my PC does, running Linux, worked fine with _no_ slowdowns.(My PC runs Linux too, and I use it _much_ more than I use Windows, but I dualboot Windows XP and Linux on my PC in case something dosen't work in Wine.
I've always liked Linux since the first day I used it. :D

first post on 2nd page

---

### Post by asuastrophysics on 2009-04-04
alright i'm replacing the IDE cable

after hitting CTRL + ALT + F1 at the login screen, i logged into the shell. 

after trying to mount the drive, i got I/O error messages everywhere. 
...so it was a hardware issue. thanks! :grin:

in windows, if you get an I/O error, a blue screen comes up telling you the error. 
if you use the GUI in ubuntu, it just freezes and gives no information as to the cause of the problem. the only way to know an I/O error has occurred is to run in tty. 

...should i send this as an idea to the launchpad?

---

