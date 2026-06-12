---
title: "formatting stops at 33%, and good cd tests bad"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by grumol on 2009-06-01
howdy i'm not getting much response over on the thinkpad forum, and when i did a google search on 33% and installs freezing, i get all these references to the ubuntu forum -- so here goes --

 my old ibm 600e(6gb hd) has xubuntu and puppy on it, which i like -- when the second 600e(12gb hd) came in the mail today, i new it was coming with windows98(not se), so i decided to remove it and install the same systems -- ok, so i may have jumped in too quick, but i deleted the two partitions, c and d, with fdisk -- now, when i try to install xubuntu, i get to the partitioner, it computes guided, starts to format ext3 on the first partition, and freezes at 33% -- i know this is a good cd, as i used it to install xubuntu on the other 600e -- also, if i try fluxbuntu, or ubuntu alternate, they all freeze at the same spot

now, maybe something's up with the Simple 12gb hd -- i noticed that when it still had win98, drive c was only 2gb, drive d, extended, was 10gb, and empty 

-- subsequently, i burnt the xubuntu alt., and it also froze, tested bad -- so i tested the cd on the old 600e, tested good --  so i ran scandisk on the new 600e, and also spinrite, which said no problem with the hd -- i then pulled the problem hd, swapped it into the old 600e, and then the cd tested fine

tried formatting the hd with parted magic, ok, and even tried to then install win2k -- no good, at least not if the hd is in the new 600e -- i can install any os if the hd is swapped into the other 600e

figured start fresh, so put the hd into the old 600e, ran dban, fine -- put the hd back into the new 600e, still won't install an os -- run dban with the hd in the new 600e, now it won't run, says probable bad sectors(even after spinrite said no problem

anyway, as the signature says, i don't know much, any help is appreciated

bob

---

### Post by wpshooter on 2009-06-01
Have you tried pulling the CD drive from you OLD machine and putting it in the NEW machine and see if you can not then install the Ubuntu O/S ?

Also, why are you using Xubuntu instead of just Ubuntu ?  How much memory does each of your machines have ?  If they have as much as 512K I would not be using Xubuntu but would opt for Ubuntu 9.04 instead.

P.S. - I would get & use [www.killdisk.com](www.killdisk.com) to WIPE the hard drive(s) before installing Ubuntu, it is probably all you need for this function (instead of DBAN) and will probably be much faster.

---

### Post by grumol on 2009-06-01
not enough resources for ubuntu

bottom line, its not the cd drive, because i have 2 other drives, and none of them will load an os onto this 12gb hard drive, unless i remove it and put it into the other 600e, then no problem 

also, other than the odd partitioning, there was no problem with this new 600e when it arrived -- i just didn't want windows on there, and i've never had this kind of problem with my other computers not loading a linux distro

---

### Post by wpshooter on 2009-06-01
Are the BIOS on both machines at the latest and greatest version ?

Have you tried setting the BIOS to the default/fail safe values and then try the installation ?

---

### Post by LewRockwell on 2009-06-01
if I recall correctly, those machines might have had a selection in the BIOS for "large drive support" so you'll need to investigate that.

---

### Post by Terrain on 2009-06-01
> **grumol said:**
> not enough resources for ubuntu

bottom line, its not the cd drive, because i have 2 other drives, and none of them will load an os onto this 12gb hard drive, unless i remove it and put it into the other 600e, then no problem 

also, other than the odd partitioning, there was no problem with this new 600e when it arrived -- i just didn't want windows on there, and i've never had this kind of problem with my other computers not loading a linux distro

That method of partitioning was actually pretty common in the days of Win98 and 98SE. 

It sounds like the hdd might have some sort of a proprietary mark on it, what I mean is, take the advice of the person above me who suggested wiping the hard drive using some tool other than what comes with the install CD you are trying to use. I would even go so far as to check out the manufacturer's website and see if they have any tools. It was not uncommon years ago for hdd manufacturers to have their own proprietary drive management suites.

---

### Post by egalvan on 2009-06-01
OK, you have two Thinkpad 600E, supposedley identical.

You have no problems with your "old" TP,
but have problems with your "new" TP.

> because i have 2 other drives, and none of them will load an os onto this 12gb hard drive,** unless i remove it and put it into the other 600e, then no problem**

It seems the only commonality with the problems is the TP....

If they are the same model number, then they should be identical.

Check the BIOS version...

Run a memory test (it's on the LiveCD),
for at least a couple of hours...

If all is OK,
then use the newer drive on the "old reliable" TP to install Xubuntu,
then transfer the drive to the "new" TP.
All should be well.

I really don't think these are old enough to be messed up with the 4GB or 8GB hard drive limit...

but if so, it's not difficult to work around this...
a seperate GRUB and boot partiton under the limit will cure it completely... 
See Herman's Linux pages for exact info...

home page...
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)


GRUB-specific pages...
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

on this page, look specifically for the
"How to make a separate GRUB partition"
and
"How to make a separate /boot partition"
guides.


Good luck.

ErnestG

---

### Post by wpshooter on 2009-06-01
> **Terrain said:**
> That method of partitioning was actually pretty common in the days of Win98 and 98SE. 

It sounds like the hdd might have some sort of a proprietary mark on it, what I mean is, take the advice of the person above me who suggested wiping the hard drive using some tool other than what comes with the install CD you are trying to use. I would even go so far as to check out the manufacturer's website and see if they have any tools. It was not uncommon years ago for hdd manufacturers to have their own proprietary drive management suites.

I agree.

Again, try WIPING that hard drive with [www.killdisk.com](www.killdisk.com)

I have seen instances when if not give the proper parameters in the proper sequence to DBAN program that you will think the drive has been WIPED and it actually has NOT been.

---

### Post by egalvan on 2009-06-01
> **wpshooter said:**
> I agree.

Again, try WIPING that hard drive with [www.killdisk.com](www.killdisk.com)

I have seen instances when if not give the proper parameters in the proper sequence to DBAN program that you will think the drive has been WIPED and it actually has NOT been.

I've been using DBAN for almost two years, and have never had a failure with the default options....(boot and nuke)

I've wiped literally hundreds of drives...

The only failures are with hard-ware defective drives.

Are the default settings slow? They can be...
So I use an older computer as a dedicated Nuker...
Boot it and let'er Nuke ;)

The drives can then be donated with no worries.


P.S.
if you can reliably reproduce that failure mode, I think that the 
DBAN folks would be VERY interested in that information.

---

### Post by grumol on 2009-06-01
lots of good advice, and i really appreciate it 

i'm leaning towards the "proprietary mark" theory -- its a Simple 12gb hd, maybe i can look into that -- although the woman i bought it from used it a little bit, before that i could tell that it hadn't been used since about 2001, mostly for office use, technical stuff(over my head, i'm sure) -- lots of ancient software

i'm writing this on the old 600e, without any hd, using puppy in ram -- after looking for any Simple info, i'm going to do the dban on a higher level on the problem hard drive, using the old 600e, since if i run it in the new 600e, it says no can do, due to bad sectors

but re:proprietary mark, not sure then why when i put it in the old 600e, its fine -- seems like any "mark" would travel with the hd??

and i'm about to put the old 6gb hd from the good 600e into this new 600e to see what happens, and then see if i can install xubuntu

my signature needs updating -- the "old" 600e is 360mhz/256mb/6gb, and the "new", 300mhz/198?mb/12gb

---

### Post by egalvan on 2009-06-01
> **grumol said:**
> 
i'm leaning towards the **"proprietary mark" theory **-- its a Simple 12gb hd, maybe i can look into that --

but re: proprietary mark...then why when i put it in the old 600e, its fine -- **seems like any "mark" would travel with the hd?**?

Yes indeed, if the problem was the hard drive, then it would travel with the drive...


> and i'm about to put the old 6gb hd from the good 600e into this new 600e to see what happens, and then see if i can install xubuntu


I see this as a "Very Bad Idea"...

BACK IT UP FIRST!

if the "new" laptop is indeed having problems with the hard drive,
you may be putting the working drive in jeopardy.

**BACK IT UP FIRST!**

Of course, if you have no data worth saving, then it's OK to experiment.

Otherwise,

[COLOR="Red"]BACK IT UP FIRST![/COLOR]

---

### Post by grumol on 2009-06-01
i want to thank you guys, and particularly egalvan -- no i hadn't checked the memory -- turns out all i needed to do was reseat the existing memory, then, no problem -- wasn't the hard drive after all 

all this was just to check the machine out, before i really mess it up -- the 500mhz cpu came in the mail today, and i needed to get a baseline in case it doesn't function after changing cpus

thanks again

---

