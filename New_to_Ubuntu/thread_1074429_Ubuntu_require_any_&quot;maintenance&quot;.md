---
title: "Ubuntu require any &quot;maintenance&quot; ?"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by Delawaredave on 2009-02-19
Installed Ubuntu.  Loved it.  Quick on older hardware - much faster than Windoze.

**_However_**, as I use Ubunut, **I swear the system is "slowing down"**.   I swear Windoze does the same.

Is there any cleanup or disk defrag or any mainteance that I'm not doing with Ubuntu ?

Thanks !

---

### Post by Captain_tux on 2009-02-19
Are you **absolutely sure** it's Ubuntu? Other than guessing, what tools have/are you running to measure metrics?

Could it perhaps be the network connection (either ethernet or wifi) or whatever browser you're using?

How about RAM? How much do you have?? And what are the systems specs???

What apps are you simultaneously running?

---

### Post by Delawaredave on 2009-02-19
Your questions are excellent and scientific.   Unfortunately, I don't have any answers or specs.  

All I know is "nothing changed" since I first installed Ubuntu.  I don't know how to add programs or utilities, etc

Browser is Firefox - I guess that changed a little since original install - going to version 3 from 2.x  

**So there is no "regular mainteance" things I need to be doing with Ubuntu ?**

**Do you know easy way to get info on installed memory and processor ? ** It is an old computer - I have no idea what memory or hertz it has.

**[COLOR="Red"]Thanks ![/COLOR]**

---

### Post by abn91c on 2009-02-19
from synaptic install **[COLOR="Blue"]hardinfo[/COLOR]**, it will tell you everything about your system, after installation in the menus it will be called System Profiler and Benchmark

---

### Post by tarps87 on 2009-02-19
This will list all the specs of you machine:
```
lshw
```

This will list the programs/process and there memory usage
```
top
```

The only maintenance I do is cleaning out the package cache
```
sudo apt-get autoclean
```
This removes all the packages that were downloaded when installing programs

To add programs go to applications -> add/remove (This will require internet access)

---

### Post by PocketDog on 2009-02-19
and no, defragging isn't necessary because fragmentation doesn't occur. (unless your drive is more than 95% full, in which case defragging will be about as useful as cleaning a burning house)

---

### Post by tarps87 on 2009-02-19
> **PocketDog said:**
> ... about as useful as cleaning a burning house

But what if disturbing the dust suffocates the fire ;)

---

### Post by lukjad on 2009-02-19
> **Delawaredave said:**
> Installed Ubuntu.  Loved it.  Quick on older hardware - much faster than Windoze.

**_However_**, as I use Ubunut, **I swear the system is "slowing down"**.   I swear Windoze does the same.

Is there any cleanup or disk defrag or any mainteance that I'm not doing with Ubuntu ?

Thanks !
Let me put it this way. Two years ago, my I installed Ubuntu 6.06 Dapper Drake on her computer. She never installed anything else, and it still runs as fast and steady as ever. I, on the other hand have tweaked and tested, upgraded and installed, and sometimes my computer goes funny. So, it really depends on what is done to the system.

For me, when my system really starts to mess up, I do one of two things. I either try moving some hidden files from my home folder, or I just upgrade/reinstall.

---

### Post by az on 2009-02-19
> **Delawaredave said:**
> 
**_However_**, as I use Ubunut, **I swear the system is "slowing down"**.   I swear Windoze does the same.


How much free space is left on your drive.  If your disk is more than 90 per cent full, you will experience poor performance.

---

### Post by thedavis on 2009-02-19
You can install and use "htop" is more pretty than "top" :)

---

### Post by egalvan on 2009-02-19
> **tarps87 said:**
> But what if disturbing the dust suffocates the fire ;)


=D>

24 years on the force.
And all that time, we were using water.

:lolflag:

---

### Post by Delawaredave on 2009-02-19
Thanks for everyone's help !  Below are specs - I know it is not a screamer... Have a great day !
Sony Vaio running ubuntu
1500 Mhz
512 Mb memory

---

### Post by tarps87 on 2009-02-19
> **Delawaredave said:**
> Thanks for everyone's help !  Below are specs - I know it is not a screamer... Have a great day !
Sony Vaio running ubuntu
1500 Mhz
512 Mb memory

I can see any reason for it to slow down, there are a few things you might want to check
Does it slow down while you are using it or is it slower the next time you boot?
Did you perform a standard install/have you got a swap partition?
If so what is its usage?
If you are not sure about the sawp partiton and usage you can post the output of this command and I will have a look
```
swapon -s
```

Those specs should be fine I have a HP laptop with the same spec running Ubuntu 8.10 with no problems

> **egalvan said:**
> =D>

24 years on the force.
And all that time, we were using water.

:lolflag:

#-o :lol:

---

### Post by Delawaredave on 2009-02-19
Here's output from swapon -s command below.  I have no idea about my partioning.  I can't answer disk space - I can't understand where Ubuntu is installed.  Originaly had Windows on, dual boot - and I guess it still is there - someday I've got to figure out how to take off. 

Filename				Type		Size	Used Priority
/dev/sda7                               partition	1510068	145916	-1

Thanks !!!

---

### Post by sydbat on 2009-02-19
Dumb question, but...how is Ubuntu installed? Wubi? As a clean dual boot (in it's own partition and everything)?

If wubi, that might be the problem, as Ubuntu is installed as a program in Windows and the NTFS file system will defrag more with use. At least AFAIK.

---

### Post by tarps87 on 2009-02-20
> **Delawaredave said:**
> Here's output from swapon -s command below.  I have no idea about my partioning.  I can't answer disk space - I can't understand where Ubuntu is installed.  Originaly had Windows on, dual boot - and I guess it still is there - someday I've got to figure out how to take off. 

Filename				Type		Size	Used Priority
/dev/sda7                               partition	1510068	145916	-1

Thanks !!!

This output shows that you do have a swap partition and it sound like you ran the default install so the partitioning should be fine. As asked in the post above did you install it through windows or by booting using the cd? If you booted using the cd I am out of ideas on why it would be slowing down.

The command:
```
sudo fdisk -l
```
will show you what your partitioning looks like, you can also install gparted for synaptic (add/remove and search for gparted)
You shouldn't need to worry about the partitioning but it may be useful to know later

---

### Post by Delawaredave on 2009-02-20
Many thanks.  I did find I often have a tab in Google Reader open - with several hundred unread news posts - I think this doesn't help.

One thing that "did change" since install was I added some FF extensions - I'm going to disable (I assume that's as effective as uninstally from memory standpoint).

Thanks again!

---

### Post by 3rdalbum on 2009-02-20
Gnome's bootup does slow down over time; but I'm unaware of any solutions except a switch to KDE :-P  Gnome does have a thing that's a little like the Windows registry; maybe after you've got a fair few program settings in it, the process of reading or writing it could slow down?

---

