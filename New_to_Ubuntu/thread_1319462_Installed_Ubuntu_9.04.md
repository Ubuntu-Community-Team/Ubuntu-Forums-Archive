---
title: "Installed Ubuntu 9.04"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by Wovaki on 2009-11-08
Hello,

I just installed Ubuntu 9.04 yesterday on my laptop. This was the first time I installed Ubuntu by partitioning my HDD. I used 8.10 before via a Wubi install.

Now I'm coming up with some problems. First when I start up my computer and choose Vista, my computer keeps wanting to do a disk check, but it automatically cancels itself. And if I try to schedule a disk check it starts and cancels two of them when I start up.

When inside Vista, my clock is screwed up, and it wont sync with the internet time.

I was also wondering how I can get the boot menu to only show two options, like when you install with Wubi, either Vista or Ubuntu...not 3 different Ubuntu and 2 different Vista, and how can I get Vista to be my default OS?

I would really like to have Ubuntu installed as a dual boot on my laptop, but everything is just screwing up, so how can I get rid of Ubuntu, and just go back to Vista?

Thanks

---

### Post by twright on 2009-11-08
Most of those options seem to be issues with Vista - I can only recommend manually setting it to run a disk check (via the checkdsk command in Windows) and seeing what happens (uninstalling Ubuntu would not make one blind bit of difference). Otherwise you might want to check on a site knowing more about Windows for these issue.

I would not disable the other items on the boot menu - you will need these if you ever need to restore/repair either system.

I also recommend upgrading to the latest version of Ubuntu (9.10) when/if you have time.

Good luck :-)

---

### Post by Paqman on 2009-11-08
> **Wovaki said:**
> 
Now I'm coming up with some problems. First when I start up my computer and choose Vista, my computer keeps wanting to do a disk check, but it automatically cancels itself. And if I try to schedule a disk check it starts and cancels two of them when I start up.


It's normal for Windows to perform a disk check of it's partition after that partition has been shrunk (as it would be during installation of Ubuntu) but this doesn't sound good. Did you defrag the NTFS partition before shrinking it? And how full is the partition? Are you able to boot up into safe mode? 

> 
When inside Vista, my clock is screwed up, and it wont sync with the internet time.

Again, possibly some corruption on the Windows partition.

> I was also wondering how I can get the boot menu to only show two options, like when you install with Wubi, either Vista or Ubuntu...not 3 different Ubuntu and 2 different Vista, and how can I get Vista to be my default OS?

To remove the multiple version of Ubuntu, simply uninstall any kernels you aren't using. Go to System > Admin > Synaptic and search for "linux-image", then uninstall all but the latest version.

You have two entries for Vista because you actually have two partitions for it: a recovery partition and a live partition.

> 
I would really like to have Ubuntu installed as a dual boot on my laptop, but everything is just screwing up, so how can I get rid of Ubuntu, and just go back to Vista?


If we're able to fix the corruption on your Vista partition, you'll be able to have both, so let's try and go down that route. One obvious (if rather heavy handed) solution is to reinstall Vista from your recovery partition or a backup.

---

### Post by Wovaki on 2009-11-08
> **Paqman said:**
> Did you defrag the NTFS partition before shrinking it? And how full is the partition? Are you able to boot up into safe mode?
Yes, I did defrag my hard drive before installing Ubuntu. I gave 50GB to Ubuntu, and I still have over 100GB free on my Windows partition.

I haven't tried booting into safe mode, but I will try.


> To remove the multiple version of Ubuntu, simply uninstall any kernels you aren't using. Go to System > Admin > Synaptic and search for "linux-image", then uninstall all but the latest version.
I don't have multiple versions installed, there is just 3 different boot options for Ubuntu. When I did the Wubi install there was 2 options total: Vista, and Ubuntu. I could press a button to give me more options, which gave 2 or 3 options for Ubuntu and 2 for Vista. I would prefer something more like that.

> If we're able to fix the corruption on your Vista partition, you'll be able to have both, so let's try and go down that route. One obvious (if rather heavy handed) solution is to reinstall Vista from your recovery partition or a backup.
If I do have to reinstall from my recovery partition (that's the only option for reinstalling Vista for me) will it bring my system back to the same state as when I bought it?

Thanks!

---

### Post by phillw on 2009-11-08
> **Wovaki said:**
> Hello,

I just installed Ubuntu 9.04 yesterday on my laptop. This was the first time I installed Ubuntu by partitioning my HDD. I used 8.10 before via a Wubi install.

Now I'm coming up with some problems. First when I start up my computer and choose Vista, my computer keeps wanting to do a disk check, but it automatically cancels itself. And if I try to schedule a disk check it starts and cancels two of them when I start up.

When inside Vista, my clock is screwed up, and it wont sync with the internet time.

I was also wondering how I can get the boot menu to only show two options, like when you install with Wubi, either Vista or Ubuntu...not 3 different Ubuntu and 2 different Vista, and how can I get Vista to be my default OS?

I would really like to have Ubuntu installed as a dual boot on my laptop, but everything is just screwing up, so how can I get rid of Ubuntu, and just go back to Vista?

Thanks

As mentioned, it does point to Vista. Did you use the Vista interface to re-size your hard-drive. If you didn't, there can be issues.

Phill.

---

### Post by phillw on 2009-11-08
> I would really like to have Ubuntu installed as a dual boot on my laptop, but everything is just screwing up, so how can I get rid of Ubuntu, and just go back to Vista?Having ubuntu living there, may just save your data from windows. So, be patient, We'll try to rescue photos / emails / music etc.

Hmm, tar ..... ahh well, if needs must.

Phill.

---

### Post by lavinog on 2009-11-08
Is your clock off by a couple of hours?
The clock issue is most likely due to ubuntu setting your clock to UTC.  Windows will not set the clock using a ntp server if it results in a drastic change.

To disable this behavior in ubuntu:
press alt-f2
```

gksudo gedit /etc/default/rcS

```


```

#
# /etc/default/rcS
#
# Default settings for the scripts in /etc/rcS.d/
#
# For information about these variables see the rcS(5) manual page.
#
# This file belongs to the "initscripts" package.

TMPTIME=0
SULOGIN=no
DELAYLOGIN=no
**UTC=no**
VERBOSE=yes
FSCKFIX=no

```
Change the UTC line to = no

---

### Post by Wovaki on 2009-11-08
> **phillw said:**
> As mentioned, it does point to Vista. Did you use the Vista interface to re-size your hard-drive. If you didn't, there can be issues.

Phill.

No, I had originally used a third party partitioning program to make a extra drive, but when I went to install Ubuntu I couldn't select the pre-partitioned drive unless I did the advanced options...and I don't know what I'm doing there so I got rid of that partition then used the Live CD to partition my drive for me.

> **phillw said:**
> Having ubuntu living there, may just save your data from windows. So, be patient, We'll try to rescue photos / emails / music etc.

Hmm, tar ..... ahh well, if needs must.

Phill.

I did do a complete backup before installing Ubuntu, so I can do a complete reinstall of Vista without any loss.


@Paqman

It seems I can no longer boot Vista at all now...when I tried to boot into Vista it went to the welcome screen but would not load up, I manually rebooted the computer and I was able to select safe mode, but it only got so far as to loading some of the windows files then it stopped.

I'm currently in my Ubuntu boot.

---

### Post by phillw on 2009-11-08
> **Wovaki said:**
> No, I had originally used a third party partitioning program to make a extra drive, but when I went to install Ubuntu I couldn't select the pre-partitioned drive unless I did the advanced options...and I don't know what I'm doing there so I got rid of that partition then used the Live CD to partition my drive for me.



I did do a complete backup before installing Ubuntu, so I can do a complete reinstall of Vista without any loss.


@Paqman

It seems I can no longer boot Vista at all now...when I tried to boot into Vista it went to the welcome screen but would not load up, I manually rebooted the computer and I was able to select safe mode, but it only got so far as to loading some of the windows files then it stopped.

I'm currently in my Ubuntu boot.


::DEEP SIGH::

There are too many variables for me, not knowing how you did your initial partitioning, etc.

I know Vista has issues when a 3rd party system is used, instead of the in-built utility.

IMHO, if you have a backup of everything, I'd recommend 'nuke-ing'  the drive, get vista back on from it's restore partiton & following some rules for dual booting that work. The ones I tell people to follow are over here --->  [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

Yes, it is sledge hammer to crack a nut, but I still feel it is your vista area that is having a problem, so I'd like a clean slate.  IMHO

Phill.

---

### Post by Wovaki on 2009-11-08
Alright...then after I do reinstall Vista, what's the best way to dual boot Ubuntu?

I had Wubi before, but I would rather give Ubuntu its own partition. But I really don't want to go through all this again.

---

### Post by phillw on 2009-11-08
> **Wovaki said:**
> Alright...then after I do reinstall Vista, what's the best way to dual boot Ubuntu?

I had Wubi before, but I would rather give Ubuntu its own partition. But I really don't want to go through all this again.

follow the apc link I posted above, their instructions are really good, with screen-shots etc.

Phill.

---

### Post by Wovaki on 2009-11-08
Alright I will reinstall Vista, and then reinstall Ubuntu.

I will let you know how it goes, thanks a lot!

---

### Post by alzie on 2009-11-08
If Vista will do it (I have no vista experience) partition your drive at reinstall.  Just trying to avoid headaches before the fact

---

### Post by yanceypd on 2009-11-08
If you haven't done anything yet.  Try fixing the Master Boot Record of Vista with the System disk.  Select repair the computer. Select dos prompt 
first entry Bootrec.exe /fixmbr
second       Bootrec.exe /fixboot

Then if it will run use computer manager to remove the Ubuntu partition.
Reinstall Ubuntu by moving the slider for partition size.  Was white for a couble of versions.  

Other folks here;) may have code that would help yo but I'm too old for that.

---

### Post by Wovaki on 2009-11-09
Hello,

I reinstalled last night, and everything seems to be working fine now. I have both Vista and Ubuntu going now, and Vista seems to be alright.

When I reinstalled it didn't touch the Ubuntu partitions, so in Vista I just deleted those partitions and they became free space, I then installed Ubuntu using the free space so Ubuntu didn't have to partition anything, just format the free space.

The only thing is in the tutorial it automatically selected all the free space, but on my computer it didn't. I had about 50GB of free space and I had to slide the slider over to use it all up, but if I went to far it would have partitioned Vista again, so I just slid it until all the free space was used.

So hopefully everything is alright. :)

Now I can update to 9.10 (I'm using 9.04) via the Update Manager and it wont touch my Vista partition or anything right? I wont have to go through any of this partitioning stuff again, it will just update like it normally does?

A little off-topic, but how do I get the Update Manager to stop poping up all the time? I liked it better when it went to the notification area like it did in 8.X

Thanks a lot!

---

