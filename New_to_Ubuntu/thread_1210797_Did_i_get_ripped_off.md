---
title: "Did i get ripped off ???"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by NOTAGEEK on 2009-07-11
I just checked my memory and got what is listed below...  I bought and paid for a new pc the other day that is supposed to have 4 gigs of mem...

is there a way to check out everything in this pc to see if i got what i paid for ??? 

thanks...



             total       used       free     shared    buffers     cached
Mem:          3024        374       2649          0         16        178
-/+ buffers/cache:        179       2844
Swap:          172          0        172

---

### Post by sdlynx on 2009-07-11
If you are running 32bit Ubuntu you can only get around 3GB of RAM (something to do with the way it allocates RAM).  Switch to 64bit if you want to be able to utilize all of your 4GB (even then you'll get only about 3.8GB but hey better right).

---

### Post by howefield on 2009-07-11
> **NOTAGEEK said:**
> I just checked my memory and got what is listed below...  I bought and paid for a new pc the other day that is supposed to have 4 gigs of mem...

is there a way to check out everything in this pc to see if i got what i paid for ???

Are you running a 32 bit operating sytem ?

If so, you will not see all your 4 gig of RAM. To be able to address all of it, you would need to run the 64 bit version, or the server kernel of the 32 bit.

---

### Post by cariboo on 2009-07-11
What does it show during POST?

---

### Post by NOTAGEEK on 2009-07-11
> **cariboo907 said:**
> What does it show during POST?


I bet you were waiting for this---i give up---what's post ???

---

### Post by howefield on 2009-07-11
> **NOTAGEEK said:**
> I bet you were waiting for this---i give up---what's post ???

Power On System Test

Does it show all 4 gigs when you first boot the machine, prior to the operating system booting...

---

### Post by OzzmanNT on 2009-07-11
In any operating system that is written in 32bit code you will not be able to address more than 3GB of memory (give or take a few MBs here and there, not going into the details here).

POST is referring to when the computer first boots up, that screen you see that gives you a lot of hardware specs (you may have to press esc to see it). This will ALWAYS show you the correct amount of memory your computer is able to use.

---

### Post by earthpigg on 2009-07-11
```
uname -a
```

mine says:

```
ep@ep-9:/$ uname -a
Linux ep-9 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 _**x86_64**_ GNU/Linux
```

see the x86_64? that means i have 64 bit ubuntu installed.

if it just says x86, with no _64, that means you have 32 bit ubuntu installed.

if you have 32 bit, you can only access 3 gigs of ram... without jumping through a bunch of nutty hoops, that is.

do you *_need_* anything more than 3 gigs of ram? lets find out.

run 'free -m' from time to time. especially when you have a zillion things going on at once on your computer.

```
ep@ep-9:/$ free -m
             total       used       free     shared    buffers     cached
Mem:          3895       3870         24          0         82       2844
-/+ buffers/cache:        943       _2951_
Swap:         1592         10       1581
```


if the column i have underlined below _***never***_ drops below 150 or so, then you have plenty of ram with just 3 gigs. that last 1 gig wont make your machine run any faster, smoother, or better (note 1 below). if it aint broke, dont fix it.... unless you want to cuz it looks fun.

if that number does drop down below 150 or so, then maybe you would benefit from reinstalling, and installing 64 bit ubuntu this time.

a 32 bit ubuntu cd can only install 32 bit ubuntu, a 64 bit ubuntu cd can only install 64 bit ubuntu.




note 1: you can google search '32 bit ubuntu vs 64 bit ubuntu'. at certain tasks, 32 bit ubuntu runs a little faster. at other tasks, 64 bit ubuntu runs a little faster. there are some things 32 bit can do that 64 bit cannot do as easily. 32 bit is 'tried and true', 64 bit is 'wave of the future'. there is _*nothing*_ that 64 bit can do that 32 bit cannot, except see more RAM. at the vast majority of tasks, you wont notice a bit of difference.

---

### Post by running_rabbit07 on 2009-07-11
Open System Monitor and click on the System Tab. Under harware you should see memory there, that is what you have. You will not see every bit of RAM. Like mine shows 1.9Gigabytes yet I installed 2. Check the screenshot.

---

### Post by NOTAGEEK on 2009-07-11
> **howefield said:**
> Power On System Test

Does it show all 4 gigs when you first boot the machine, prior to the operating system booting...

IT NEver shows anything...

> **OzzmanNT said:**
> In any operating system that is written in 32bit code you will not be able to address more than 3GB of memory (give or take a few MBs here and there, not going into the details here).

POST is referring to when the computer first boots up, that screen you see that gives you a lot of hardware specs (you may have to press esc to see it). This will ALWAYS show you the correct amount of memory your computer is able to use.

ok i got it, i had to restart 4 times cuzz that page gets accessed from the tab key but only stays on for <2 seconds... my eyes finally focused on what looked like 4096 maybe...

thanks...

---

### Post by earthpigg on 2009-07-11
> **NOTAGEEK said:**
>  my eyes finally focused on what looked like 4096 maybe...

if it was 40XX then no, you did not get ripped off.

---

### Post by NOTAGEEK on 2009-07-11
> **earthpigg said:**
> ```
uname -a
```mine says:

```
ep@ep-9:/$ uname -a
Linux ep-9 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 _**x86_64**_ GNU/Linux
```see the x86_64? that means i have 64 bit ubuntu installed.

if it just says x86, with no _64, that means you have 32 bit ubuntu installed.

if you have 32 bit, you can only access 3 gigs of ram... without jumping through a bunch of nutty hoops, that is.

do you *_need_* anything more than 3 gigs of ram? lets find out.

run 'free -m' from time to time. especially when you have a zillion things going on at once on your computer.

```
ep@ep-9:/$ free -m
             total       used       free     shared    buffers     cached
Mem:          3895       3870         24          0         82       2844
-/+ buffers/cache:        943       _2951_
Swap:         1592         10       1581
```
if the column i have underlined below _***never***_ drops below 150 or so, then you have plenty of ram with just 3 gigs. that last 1 gig wont make your machine run any faster, smoother, or better (note 1 below). if it aint broke, dont fix it.... unless you want to cuz it looks fun.

if that number does drop down below 150 or so, then maybe you would benefit from reinstalling, and installing 64 bit ubuntu this time.

a 32 bit ubuntu cd can only install 32 bit ubuntu, a 64 bit ubuntu cd can only install 64 bit ubuntu.




note 1: you can google search '32 bit ubuntu vs 64 bit ubuntu'. at certain tasks, 32 bit ubuntu runs a little faster. at other tasks, 64 bit ubuntu runs a little faster. there are some things 32 bit can do that 64 bit cannot do as easily. 32 bit is 'tried and true', 64 bit is 'wave of the future'. there is _*nothing*_ that 64 bit can do that 32 bit cannot, except see more RAM. at the vast majority of tasks, you wont notice a bit of difference.


 
i got my disc off ebay and it is only 32 bit with a bonus program (bluebirds) whatever that is...

i have my hdd partitioned messed up enough to where i cant even run update manager that has 111-1 mb of updates that i dont have room on the hdd... as soon as i get up the nerve or feel comfy enough tahing care of the partition and maybe re-installing to 64 bit---its on my things to do list... 

here is what i got...
2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux


 total       used       free     shared    buffers     cached
Mem:          3024        379       2645          0         13        164
-/+ buffers/cache:        200       2823
Swap:          172          0        172

sure wish there was a way to find out about my q9300 processor that is supposed to be overclocked to run at 3.3...

thanks...

---

### Post by nhasian on 2009-07-11
you got ubuntu off of ebay?  thats where you got ripped off not your computer hehe

anyway, you can download the 64 bit version of ubuntu for free from:

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

---

### Post by earthpigg on 2009-07-11
```
total used free shared buffers cached
Mem: 3024 379 2645 0 13 164
-/+ buffers/cache: 200 _**2823**_
Swap: 172 0 172
```

yeah, you have more RAM than you know what to do with :P

i686 means 32 bit. my mistake on saying it would tell you x86.

as for your hard drive being full, please post the output of:

```
df -h
```

and

```
sudo fdisk -l
```

this is a lower case L, by the way: ```
l
```

---

### Post by NOTAGEEK on 2009-07-11
> **running_rabbit07 said:**
> Open System Monitor and click on the System Tab. Under harware you should see memory there, that is what you have. You will not see every bit of RAM. Like mine shows 1.9Gigabytes yet I installed 2. Check the screenshot.


now that is an interesting place to go!!! thanks...  i saw my processor there and it sid q9300 at 2.5...  i paid extra for the overclocking service... it should be running at 3.3... unless perhaps that sys monitor is just id'ing the cpu and the oclking is done in bios ???  thanks...

---

### Post by NOTAGEEK on 2009-07-11
> **earthpigg said:**
> ```
total used free shared buffers cached
Mem: 3024 379 2645 0 13 164
-/+ buffers/cache: 200 _**2823**_
Swap: 172 0 172
```yeah, you have more RAM than you know what to do with :P

i686 means 32 bit. my mistake on saying it would tell you x86.

as for your hard drive being full, please post the output of:

```
df -h
```and

```
sudo fdisk -l
```this is a lower case L, by the way: ```
l
```



Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.2G   20M 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  108K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  144K  1.5G   1% /dev
tmpfs                 1.5G   84K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.28-11-generic/volatile
/dev/sr0              388K  388K     0 100% /media/cdrom0


Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdc0fdc0f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          13       38588   309848408    7  HPFS/NTFS
/dev/sda2           38589       38913     2610562+   5  Extended
/dev/sda5           38589       38891     2433816   83  Linux
/dev/sda6           38892       38913      176683+  82  Linux swap / Solaris



JEEZE---And i had to go and be a surgon instead of an IT person... lol... thanks...

---

### Post by NOTAGEEK on 2009-07-12
> **nhasian said:**
> you got ubuntu off of ebay?  thats where you got ripped off not your computer hehe

anyway, you can download the 64 bit version of ubuntu for free from:

[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)



thanks but i had no pc when i got on a friends laptop to get on ebay...  i got my pc, 9.04 disc, and a bunch of other stuff there---did pretty good too...

---

### Post by earthpigg on 2009-07-12
you loaded your rifle with a mag containing only 3 rounds. :P

i see you have a windows partition....

do you have/use windows on that computer?

if not, the gruntproof fix is to simply reinstall and choose 'guided - use entire hard drive'.

at present, less than 1% of your hard drive is available for use - and that 1% is full.

---

### Post by Sef on 2009-07-12
> you got ubuntu off of ebay?  thats where you got ripped off not your computer hehe

Not necessarily.  Sometimes it is easier to buy it than to download it.

---

### Post by NOTAGEEK on 2009-07-12
> **earthpigg said:**
> you loaded your rifle with a mag containing only 3 rounds. :P

i see you have a windows partition....

do you have/use windows on that computer?

if not, the gruntproof fix is to simply reinstall and choose 'guided - use entire hard drive'.


i tried win xp pro and locked it up---then win 7 beta build 7057---locked it up---then 9.04 and thought i gave it the whole drive but i think mr gates had better ideas...

if i ever get good at this stuff ultimately i would like to put 64 bit 9.04 on the 2nd half of a hdd divided roughly inhalf partition wise... then in the future i could always add win 7 to the front half of the hdd if i get in the mood...

thats the kind of stuff i have been reading about and i have been getting much help here on this forum... and i really appreciate it...

thanks...

---

### Post by earthpigg on 2009-07-12
when you decide to repartition and reinstall, it will be _**much much much**_ **_quicker_** to _**delete all the partitions and create new ones**_ than to resize the existing ones.

---

### Post by nhasian on 2009-07-12
you can even order a free CD directly from ubuntu... but it takes a while to get.  yeah I understand compensating someone for their time to download/burn the iso and for the cd and shipping it.  It just seems like bad mojo.  :lolflag:

> **Sef said:**
> Not necessarily.  Sometimes it is easier to buy it than to download it.

You should run a memtest and HD Test and perhaps some burnin tools on your computer to make sure there arnt any hardware defects.

[QUOTE=NOTAGEEK]i tried win xp pro and locked it up---then win 7 beta build 7057---locked it up---then 9.04[/QUOTE]

NOTE: i just noticed this was my 1000th post!

---

### Post by NOTAGEEK on 2009-07-12
> **earthpigg said:**
> when you decide to repartition and reinstall, it will be _**much much much**_ **_quicker_** to _**delete all the partitions and create new ones**_ than to resize the existing ones.


this is why i am trying to hold off setting up 9.04 the way i want it...  i would like to install studio, etc etc... but it makes no sense right now if im going to clean the hdd and start over...

i need more know how b4 i try as i dont want to mess things up right now they are crazy enough...

ill lose all my bookmarks etc and i cant even make a list of them as i went and bought a stupid lexmark printer... i downloaded the driver and all looked fine till i clicked print and it just sat there... hopefully its cuzz there is no memory left...

thanks...:guitar:

---

### Post by nhasian on 2009-07-12
oh thats easy.  if you save everything in your /home directory you will save a lot of your settings and configurations.  specifically the firefox bookmarks are in ~/.mozilla

i also recommend on your fresh install to make /home a separate partition to make fresh installs easier in the future.

> **NOTAGEEK said:**
> ill lose all my bookmarks etc and i cant even make a list of them as i went and bought a stupid lexmark printer... i downloaded the driver and all looked fine till i clicked print and it just sat there... hopefully its cuzz there is no memory left...


---

### Post by 3rdalbum on 2009-07-12
You need to turn off frequency scaling in the BIOS in order for the overclocking to work. Otherwise the CPU will scale down to its stock speed.

---

### Post by JohnnySage50307 on 2009-07-12
There is a pretty good chance you've got your 4GB of RAM; it seems to me you're registering slightly above 3GB.  I am unfamiliar with the nuances of why a 32bit Linux machine wouldn't be able to register the entire volume, but I've been running into many instances where Jaunty is acting a lil unusual.
 
Most Linux processes are exceptionally streamlined, and there's actually a pretty good chance that even if all you had was 3GB, you wouldn't see a significant improvement if you had 4GB.  Worse comes to worse, if you did get ripped off a GB, go to geeks.com or newegg.com and order yourself a new strip.  I know you're not a geek, but it's not difficult to install:  Turn off machine and open your case; find the RAM slots that look just like what you just bought; if they're all filled, pull one out and put the new one in otherwise put the new one in an empty slot; close case and restart; done!
 
Honestly, I doubt you'll really need to buy more memory.  Always make sure your machine does what you want:  It's easy to over-accessorize your machine and just waste money buying hardware you'll never fully utilize.

---

### Post by jerome1232 on 2009-07-12
> **NOTAGEEK said:**
>  i went and bought a stupid lexmark printer

thanks...:guitar:

lexmark + Linux = unhappy printer owner

I'm not sure if you can get them to even work.

It's just about impossible to go wrong with an hp, epson and cannon I believe are well supported under linux as well.

---

### Post by 3rdalbum on 2009-07-12
> **JohnnySage50307 said:**
> There is a pretty good chance you've got your 4GB of RAM; it seems to me you're registering slightly above 3GB.  I am unfamiliar with the nuances of why a 32bit Linux machine wouldn't be able to register the entire volume, but I've been running into many instances where Jaunty is acting a lil unusual.

A 32-bit operating system can address 4 GiB of RAM, but remember the components in your computer also have their own bits of memory that need to be addressed. Graphics card memory takes a big chunk out of the addressable 4 GiB. When you add the addressable memory used by SATA controller, USB controller, sound card, network device etc you end off with around 3.3 GiB of main system RAM that can be addressed.

If you use a 64-bit operating system, the address space becomes very large. The memory maps for inbuilt devices are still present, but they use memory addresses far in advance of what RAM you actually have.

Not being able to use all 4 GiB of RAM on 32-bit Ubuntu is not a bug in Ubuntu, it's a reality on all 32-bit operating systems. When the CPU is running in 32-bit mode it must be able to access your other sources of memory within the 4 GiB address space.

---

### Post by NOTAGEEK on 2009-07-12
> **3rdalbum said:**
> A 32-bit operating system can address 4 GiB of RAM, but remember the components in your computer also have their own bits of memory that need to be addressed. Graphics card memory takes a big chunk out of the addressable 4 GiB. When you add the addressable memory used by SATA controller, USB controller, sound card, network device etc you end off with around 3.3 GiB of main system RAM that can be addressed.

If you use a 64-bit operating system, the address space becomes very large. The memory maps for inbuilt devices are still present, but they use memory addresses far in advance of what RAM you actually have.

Not being able to use all 4 GiB of RAM on 32-bit Ubuntu is not a bug in Ubuntu, it's a reality on all 32-bit operating systems. When the CPU is running in 32-bit mode it must be able to access your other sources of memory within the 4 GiB address space.


Thanks for that---and the fairly easy to follow description that** even i understood** all but just a word here and there... there still could be hope for me ??? :p

---

