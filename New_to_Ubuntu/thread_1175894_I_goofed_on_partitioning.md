---
title: "I goofed on partitioning"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by dluzius on 2009-06-01
I wanted to set up a dual-boot system with half of my 500 Gig. HD allocated to WinXP, and the other half to Ubuntu 9.04.
But now when Grub takes me to Ubuntu, I keep getting an error message telling me I am out of space. I can't even retrieve email. Please help me correct this problem.
   Dave

---

### Post by jon6123 on 2009-06-01
which did you install first? where are you in your installation?

---

### Post by lindsay7 on 2009-06-01
Can you post a screen shot of gparted showing your drive?

---

### Post by dluzius on 2009-06-01
my  year old gateway came with winXP.
Now I am trying to install ubuntu 9.04
letting grub do the partitioning.

---

### Post by lindsay7 on 2009-06-01
if you can not post a screen shot,

type this in the terminal and post it here

sudo fdisk -l    That is the letter l not the number 1

---

### Post by dluzius on 2009-06-01
unable to use gparted at this time, but Windows tells me there are 4 partitions,
Recovery   4.34 GB
C:\459 GB
next partition 2.33 GB
next partition 173 MB

---

### Post by lindsay7 on 2009-06-01
I can not give you much more help, since there is not screen shot or fdisk -l data, but it looks like you did not partition your 500 gig drive 50/50 as you said. Looks like ubuntu installed on less the 3 gigs and that is your problem.  Delete the Ubuntu partition and redo it the way you want and reinstall.

Out!

---

### Post by LewRockwell on 2009-06-01
I agree to the re-installation determination

(assuming since you've already attempted an installation that you've done a back-up...so I'll go on)

run live CD and use gparted to resize your partitions the way you need them to be...you say you've got a 500gb...give windoze 100gb(primary partition), then 100gb primary partition for linux, then a 2gb swap partition, then make the rest of the drive an extended partition for later partitioning and usages...

now run your installation making sure that Ubuntu is installed on the correct partition.

if you have additional questions, ask/research BEFORE doing...

as always, we're here for ya but your mileage may vary depending on your driving habits...

---

### Post by dluzius on 2009-06-01
[IMG]http://home.comcast.net/~dluzius/Screenshot.png[/IMG]

---

### Post by LewRockwell on 2009-06-01
It's fdisk -"little L"

```

sudo fdisk -l
```

---

### Post by dluzius on 2009-06-01
Is gparted on the Live CD ?

---

### Post by cjv8888 on 2009-06-01
> sudo fdisk -l
where l is the small letter of L

---

### Post by lindsay7 on 2009-06-01
One more time please.


>  Re: I goofed on partitioning
if you can not post a screen shot,

type this in the terminal and post it here

sudo fdisk -l That is the letter l not the number 1
__________________

Looks like you used the letter I as in Island, and not the letter l as in land.

---

### Post by lindsay7 on 2009-06-01
May, if not install from Synaptic under System/administration, when you run it right click on the drive and "unmonut it" the drive has to be unmounted to work on it.

---

### Post by dluzius on 2009-06-02
Thanks for all the help. Gparted was the solution, and all seems to be running well. Thanks again.
    Dave

---

