---
title: "jaunty check disk"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-09
I have three hard drives 
/, /home, mnt/music
it seems that it check disks every few boots,
i know it will check the boot disk every 20 something boots but the other two seem to be checked more often.
if i access mnt/music or /home is it considered a boot?
i have not counted how many boots in between but it seems like once every few days.
How does this work with multiple drives?

---

### Post by NightwishFan on 2009-05-09
Are any of the disk configured to use EXT2? If so, then they tend to be checked more, I would assume.

Separate partitions I think are treated individually, so the mount count is unique for each one.

---

### Post by DarinB on 2009-05-09
All are ext 3
and how do find out what the mount count is????

---

### Post by DarinB on 2009-05-09
How do i check mount count for 2nd and 3rd hardrives

---

### Post by DarinB on 2009-05-09
this is my mount count, i do not know what is considered a mount for the non boot drives. And how do increase the max so it doesn't come up so fast.
And how often should it really be done?????

this is my /home
darin@darin-desktop:~$ sudo tune2fs -l /dev/sdb1 | grep -i "mount count" 
Mount count:              24 
Maximum mount count:      33 
darin@darin-desktop:~$ 

this is my /
darin@darin-desktop:~$ sudo tune2fs -l /dev/sda5 | grep -i "mount count" 
Mount count:              17 
Maximum mount count:      24 
darin@darin-desktop:~$ 

this is my /mnt/music
darin@darin-desktop:~$ sudo tune2fs -l /dev/sdc1 | grep -i "mount count" 
Mount count:              2 
Maximum mount count:      36 
darin@darin-desktop:~$

---

### Post by Didius Falco on 2009-05-09
> **DarinB said:**
> this is my mount count, i do not know what is considered a mount for the non boot drives. And how do increase the max so it doesn't come up so fast.
And how often should it really be done?????

Darin,

Type this in a terminal: ```
man tune2fs
``` and all will be revealed about how to change the mount count.

As to how often it should really be done - I'm content to leave it at the default settings. But then, when it comes to my PC, I'm a belt and suspenders type...

Regards,

Didius

---

### Post by DarinB on 2009-05-09
thanks tons of info but i am still not sure how to compose the command to change it, where can i find example of a change. also the man page talks about a file check on next reboot.
i wonder if i would not be better off setting a time interval like once a month and stagger it a day apart for each drive, but then again an example would be good.

---

### Post by durand on 2009-05-09
There is a program on these forums to do this graphically. I'll see if I can find it.

---

### Post by durand on 2009-05-09
Found it, here you go: [http://ubuntuforums.org/showthread.php?t=295262](http://ubuntuforums.org/showthread.php?t=295262)

You may also be interested in this: [http://micrux.net/?p=52](http://micrux.net/?p=52)

---

### Post by DarinB on 2009-05-09
does bonager work on 9.04????

---

### Post by Elfy on 2009-05-09
> thanks tons of info but i am still not sure how to compose the command to change it, 

```
sudo tune2fs -c *number* /dev/sdxy
```

Set number as you wish, replace sdxy with partition, eg

tune2fs -c 35 /dev/sda1 would set interval to 35 for sda1. I do similar on one of my machines to stagger the checks on data partitions

---

### Post by DarinB on 2009-05-09
how would i set it up as a timed event like the interval from the man pages

---

### Post by durand on 2009-05-09
Bonager might work, try it.

---

### Post by Elfy on 2009-05-09
> **DarinB said:**
> how would i set it up as a timed event like the interval from the man pages

sudo tune2fs -i  40 /dev/sdc5
tune2fs 1.40.8 (13-Mar-2008)
Setting interval between checks to 3456000 seconds

that set's it to 40 days - no idea about weeks or months I'm afraid

---

### Post by DarinB on 2009-05-09
i know this sounds stupid but do i have disable the -c so the don't conflict. 
and why did you tell me the seconds for was that just as a joke

---

### Post by Elfy on 2009-05-09
lol - no I just pasted the output it gave me.

> do i have disable the -c so the don't conflict. 

Not sure about that - I only ran the command to see how it worked for you.

---

### Post by DarinB on 2009-05-09
well it worked so here it is i kept the spacing the same. i wonder if i can reset the mount count to 0 so i can see how much time goes by??????
 

darin@darin-desktop:~$ sudo tune2fs -l /dev/sdb1 | grep -i "mount count" 
Mount count:              26
Maximum mount count:      77
darin@darin-desktop:~$  sudo tune2fs -l /dev/sda5 | grep -i "mount count" 
Mount count:              19
Maximum mount count:      68
darin@darin-desktop:~$ sudo tune2fs -l /dev/sdc1 | grep -i "mount count" 
Mount count:              4
Maximum mount count:      80
darin@darin-desktop:~$

---

### Post by Didius Falco on 2009-05-09
> **DarinB said:**
> well it worked so here it is i kept the spacing the same. i wonder if i can reset the mount count to 0 so i can see how much time goes by??????
 

darin@darin-desktop:~$ sudo tune2fs -l /dev/sdb1 | grep -i "mount count" 
Mount count:              26
Maximum mount count:      77
darin@darin-desktop:~$  sudo tune2fs -l /dev/sda5 | grep -i "mount count" 
Mount count:              19
Maximum mount count:      68
darin@darin-desktop:~$ sudo tune2fs -l /dev/sdc1 | grep -i "mount count" 
Mount count:              4
Maximum mount count:      80
darin@darin-desktop:~$

From the AutoFsck Wiki:

> Reset the mount count on each partition: ```
sudo tune2fs -C 1 /dev/sda1
``` (for example) 
Note that the latter command won't work (and isn't needed) on partitions that fsck doesn't handle (e.g. swap or Windows partitions). *~ncoghlan*

Here is a link to to that Wiki - it mostly deals with using AutoFsck, obviously, but you might find more useful information reading through it.

Regards,

Didius

---

### Post by DarinB on 2009-05-10
wouldn't the -c reset the max mount count not the ones already mounted?
maybe if i force a check on all of them then they would be at zero, next boot? AND then i can see how long it takes to get to the max i reset it to.

---

