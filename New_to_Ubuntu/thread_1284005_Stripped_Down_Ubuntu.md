---
title: "Stripped Down Ubuntu"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by GapToothedGypsy on 2009-10-06
Hi Guys,

I am very much a ubuntu newbie (but have some unix skills) and have recently installed 9.04 on my eeePC 1005HA succesfully and I am very happy with the result.

However I have noticed that I have lost quite a bit of disk space for the install and OS. I want to use this netbook for temporary picture storage in the field only, so disk space is a premium.

My question is, how do I strip down ubuntu to the bare essentials ie: ftsop picture viewer/ wireless access/browser/usb, to free up the maximum disk space?

Any advice really appreciated, and if I need to re-post this elsewhere please let me know.

Regards

The GapToothedGypsy

---

### Post by nothingspecial on 2009-10-06
Have a look at [[COLOR="Magenta"]this[/COLOR]]("http://sites.google.com/site/masonux/")

---

### Post by jeneverboy on 2009-10-06
Would this masonux also be suitable for a desktop pc running:

-some sort of music player for mp3's  (like songbird)
-with samba on home network
-a kind of backup program in a home network?

I guess you can add every program which is in UBUNTU 9.04?

---

### Post by unmole on 2009-10-06
Most certainly. At it's core it STILL is ubuntu and you can add and remove software as you do in ubuntu.

---

### Post by louieb on 2009-10-06
Unfortunately stripping Ubuntu down to bare essentials is not well documented. 

Its much quicker to do a command line install or smaller that that a minimal install and build up adding just pieces you want.   
There a few how tos like this [**Create a complete, snappy and beautiful Ubuntu Desktop  **]("http://ubuntuforums.org/showthread.php?t=1209904&highlight=minimum+install")

---

### Post by stwschool on 2009-10-06
Crunchbang (another Ubuntu derivitive) is another option (very very light, tiny and lovely).

---

### Post by nothingspecial on 2009-10-06
> **jeneverboy said:**
> Would this masonux also be suitable for a desktop pc running:

-some sort of music player for mp3's  (like songbird)
-with samba on home network
-a kind of backup program in a home network?

I guess you can add every program which is in UBUNTU 9.04?

The whole point of masonux is to give you a bare minimum working system from which you can build your custom ubuntu install, adding as much or as little as you like.

---

### Post by louieb on 2009-10-06
Heres the thread  I was looking earlier check post #1 and post #121 ["Ubuntu-Desktop-Minimal"  ck post #121to]("http://www.uluga.ubuntuforums.org/showthread.php?t=1155961")

---

### Post by mikechant on 2009-10-06
> I am very much a ubuntu newbie (but have some unix skills) and have recently installed 9.04 on my eeePC 1005HA succesfully and I am very happy with the result.

However I have noticed that I have lost quite a bit of disk space for the install and OS. I want to use this netbook for temporary picture storage in the field only, so disk space is a premium.

The eeePC 1005HA appears to have a 160Gb hard drive. A full Ubuntu install fits in <10Gb (allowing reasonable space for software updates, temporary files etc.). 
So you should have 150Gb space for data. If that's not enough, then surely 155Gb still won't be enough (if you squeeze 5Gb from Ubuntu)?
Or is the real problem not lack of space overall but that the free space is not in the right partition?

Maybe you should post the output of the command 
```
fdisk -l
```
to show your partition setup
(-l is lower case letter L, not number one)

---

### Post by snowpine on 2009-10-06
+1 to Mikechant. :)

If you really need an extra gb or so, here are my suggestions:

1. Crunchbang Lite (as mentioned above)
2. Minimal Ubuntu + only the apps you need (see above)
3. SliTaz Linux: not based on Ubuntu, but the entire OS is only 30mb, and they even have an eee-specific version.
4. SD card for extra storage. ;)

---

### Post by GapToothedGypsy on 2009-10-07
Hi Guys,

Thanks for all your help, much appreciated.


Regards


The GapToothedGypsy

---

