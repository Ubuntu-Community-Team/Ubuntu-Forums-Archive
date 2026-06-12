---
title: "DVD's in Ubuntu 10.04"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by Neuro78 on 2010-06-24
Hi, 
I have recently switched over to Ubuntu 10.04 Lucid Lynx from Windows on my Sony Vaio VGN-CDS21 and have install all the patches to play commercial DVD's however I have found that some DVD's play but others don't. 

An US copy of Jay and Silent Bob Strike Back but a new UK DVD of Wolfman fails to work and through up an error stating that the DVD can not be read. I have followed the instructions on installing the correct codecs but still get the error in both M Player and LVC. 

I have tried using AcidRiper to copy over as an AVI but it will not recognise that there is a DVD in the DVD drive. - but it can copy over JSBSB DVD. 

I'm stumped!
I have deleted and reinstalled all aspects of Media player and Codecs  but to no avail :o(


Cheers

Neuro78

---

### Post by mc4man on 2010-06-24
Just to d. ck. something - run this and see who made the dvd drive - if matshita then you can't play if there is a region mismatch 
(though a firmware solution for some matshita laptop drives has recently arrived

Don't see sony using panasonic drives but you never know
```
sudo lshw -C disk
```

---

### Post by Neuro78 on 2010-06-24
> **mc4man said:**
> Just to d. ck. something - run this and see who made the dvd drive - if matshita then you can't play if there is a region mismatch 
(though a firmware solution for some matshita laptop drives has recently arrived

Don't see sony using panasonic drives but you never know
```
sudo lshw -C disk
```

Yup it's a Matshita.

I've tried to set the region to 2 (Europe) but I get:

Would you like to change the region setting of your drive? [y/n]:y
Enter the new region number for your drive [1..8]:2
New mask: 0xFFFFFFFD, correct? [y/n]:y
ERROR: Region code could not be set!


Help! :oO

---

### Post by mc4man on 2010-06-24
**Do not change regions just to play one disk **- you are only allowed 5 region sets before the drive gets locked
(figure 1 set initially to R 1, so at best you only have 4 left. (it's possible you've already used up all your changes

Once the drive is locked you are **completely** sol as far as changing to another region.

if you post the output from lshw (just the *-cdrom info ), can tell you if the drive can be 'fixed'
(though the procedure must be done in windows

---

### Post by anewguy on 2010-06-24
> **mc4man said:**
> **Do not change regions just to play one disk **- you are only allowed 5 region sets before the drive gets locked
(figure 1 set initially to R 1, so at best you only have 4 left. (it's possible you've already used up all your changes

Once the drive is locked you are **completely** sol as far as changing to another region.

if you post the output from lshw (just the *-cdrom info ), can tell you if the drive can be 'fixed'
(though the procedure must be done in windows

+1  It is very dangerous to change the region code on your drive.  As mc4man mentioned, you are only allowed 5 changes.  The entire idea of changing the region code on the drive is that it is expected to be a PERMANENT change.


Dave ;)

---

### Post by Neuro78 on 2010-06-24
> **anewguy said:**
> +1  It is very dangerous to change the region code on your drive.  As mc4man mentioned, you are only allowed 5 changes.  The entire idea of changing the region code on the drive is that it is expected to be a PERMANENT change.


Dave ;)

Hi, 

I Live in the UK so all my DVD's are reg 2, only by chance did I try a Reg 1 DVD. 

How do I run LSHW? is that in Terminal?

Cheers

:o)

---

### Post by Neuro78 on 2010-06-24
> **mc4man said:**
> **Do not change regions just to play one disk **- you are only allowed 5 region sets before the drive gets locked
(figure 1 set initially to R 1, so at best you only have 4 left. (it's possible you've already used up all your changes

Once the drive is locked you are **completely** sol as far as changing to another region.

if you post the output from lshw (just the *-cdrom info ), can tell you if the drive can be 'fixed'
(though the procedure must be done in windows

Sorry was having a spaz momment. 

 *-cdrom
       description: DVD-RAM writer
       product: DVD-RAM UJ880AS
       vendor: MATSHITA
       physical id: 1
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/THE_WOLFMAN_2010
       version: 1.20
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/THE_WOLFMAN_2010
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted


Cheers

---

### Post by mc4man on 2010-06-24
> How do I run LSHW? is that in Terminal?

yes ( the same as before) - just post the outputed info

Ex. ( looking for what I highlighted in blue
> doug@doug-laptop:~$ sudo lshw -C disk
[sudo] password for doug: 
  *-cdrom                 
       [COLOR="Blue"]description: DVD writer
       product: DVD+-RW UJ-867S
       vendor: MATSHITA[/COLOR]
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/THE_MATRIX_16X9LB_N_AMERICA
       [COLOR="Blue"]version: 1.00[/COLOR]
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime,uid=1000,gid=1000,umask=77,iocharset=utf8 state=mounted status=ready

> I Live in the UK so all my DVD's are reg 2, only by chance did I try a Reg 1 DVD.
I really hope you haven't used up your changes 
(some windows dvd players will switch regions for you with little to no warning

To check - post complete terminal output

Assuming you have regionset installed

With a region 1 dvd in the drive
```
regionset
```

Ex.
> doug@doug-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: SET
vendor resets available: 4
[COLOR="Red"]user controlled changes resets available: 4[/COLOR]
drive plays discs from region(s): 1, mask=0xFE

Edit : was posting at same time - do and post the regionset deal - then you'll know what your options are

---

### Post by stmiller on 2010-06-24
Install libdvdcss2 from medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then just use VLC for playback. VLC does not care about any region mess. It just works. :)

---

### Post by mc4man on 2010-06-24
> Install libdvdcss2 from medibuntu:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Then just use VLC for playback. VLC does not care about any region mess. It just works. 
Generally good advice - just not applicable in this case.
This is about specific hardware - matshita laptop dvd drives - that won't allow access to encrypted sectors when there is a region mismatch.

No codec, software, or Os can change that - only in some cases a dump of the firmware, patching and re-flashing will resolve...

---

### Post by Neuro78 on 2010-06-25
> **mc4man said:**
> yes ( the same as before) - just post the outputed info

Ex. ( looking for what I highlighted in blue


.
I really hope you haven't used up your changes 
(some windows dvd players will switch regions for you with little to no warning

To check - post complete terminal output

Assuming you have regionset installed

With a region 1 dvd in the drive
```
regionset
```Ex.


Edit : was posting at same time - do and post the regionset deal - then you'll know what your options are

cowboy@cowboy-laptop:~$ regionset
regionset version 0.1 -- reads/sets region code on DVD drives
Current Region Code settings:
RPC Phase: II
type: LAST CHANCE
vendor resets available: 4
user controlled changes resets available: 1
drive plays discs from region(s): 1, mask=0xFE

Would you like to change the region setting of your drive? [y/n]:

I tried to set the region to R2 with DVD (R2) in the drive but it comes up with an error. 

Looks like I only have one shot left. 

Thanks for all the help :)

---

