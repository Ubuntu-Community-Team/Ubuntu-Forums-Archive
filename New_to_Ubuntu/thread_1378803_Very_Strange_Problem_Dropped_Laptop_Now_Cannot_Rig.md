---
title: "Very Strange Problem Dropped Laptop Now Cannot Right-Click"
date: 2010-01-11
forum: New to Ubuntu
---

### Post by gigi1234 on 2010-01-11
Ok this is really weird problem. I am dual-booting 8.04 with Vista on a Dell XPS m1330 laptop. Last night I was running Ubuntu and the laptop got dropped on the floor. Now the mouse won't left-click (even if I plug in an external mouse). But everything works fine in Vista and I also have a Crunchbang Linux installed on a pendrive that boots and runs perfectly. I have a bunch of files on the Linux side that aren't backed up. I can access them through the Crunchbang pendrive but copying them all to an external drive will be a drag. Can anyone suggest how I might try to fix this problem? Or suggest what might be causing the problem? I guess I am assuming that dropping the laptop has caused a disk error. Thanks in advance!

---

### Post by JC Cheloven on 2010-01-11
> **gigi1234 said:**
> Ok this is really weird problem. I am dual-booting 8.04 with Vista on a Dell XPS m1330 laptop. Last night I was running Ubuntu and the laptop got dropped on the floor. Now the mouse won't left-click (even if I plug in an external mouse). But everything works fine in Vista and I also have a Crunchbang Linux installed on a pendrive that boots and runs perfectly. I have a bunch of files on the Linux side that aren't backed up. I can access them through the Crunchbang pendrive but copying them all to an external drive will be a drag. Can anyone suggest how I might try to fix this problem? Or suggest what might be causing the problem? I guess I am assuming that dropping the laptop has caused a disk error. Thanks in advance!
A weird one, indeed :confused:
Have you checked in system-preferences-mouse so see if it helps at all?
Does the mouse works also from live cd? If so, it should be a disk error problem.

First I'd save my personal files elsewhere using a live cd. Then you could try some tweaking. For example reinstalling ubuntu without formatting the partition. Hopefully the bad sector will be left unused...

---

### Post by gigi1234 on 2010-01-11
I can't check the system preferences because I can't do anything with the mouse. It is the left click that doesn't work. I have been trying to use the pendrive operating system to access and save the files I need, but I keep getting "access denied" messages. 

I'll try the live cd and see what happens. 

Is there any way to check the system preferences from the command line in rescue mode?

---

### Post by gigi1234 on 2010-01-11
The live cd works fine. But I still can't copy the files because I don't have permission. Is there any way I change the file permissions in rescue mode? I am a little rusty on the command line as I haven't had any problems in awhile. Any hints about how to proceed would be much appreciated!

---

### Post by JC Cheloven on 2010-01-11
In principle, a live session will be exactly the same booting ubuntu from pendrive or from live cd. No diference to be expected.

From live, you get "acces denied"when trying to access your disk from nautilus, right? 

Does it happens also when trying to access the vista partition? If not, then the filesystem in the ubuntu partition may be "in use" due to a bad shutdown (nothing to do with permissions in this case). Try booting from your ubuntu partition for the sole purpose of shutting down correctly. crtl-alt-del will do for that, you don't need the mouse. 
Otherwise, you can indeed set access permisions in the live session using the chmod command, but i'm affraid it won't help.

I was also about to suggest you the smartmoontools package and follow this: [http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html) 
You could install it in a live session (w/internet), but I'm unsure if it supports ext4 by now.

---

### Post by sandyd on 2010-01-11
in crunchbang, open a terminal and type in
```

sudo fdisk -l
#make note of your ubuntu partition
fsck -y /dev/sdax #replace "dev/sdax" with the ubuntu partition

```
that will immediately initiate a disk check on the ubuntu partition, provided it isn';t mounted.

---

### Post by gigi1234 on 2010-01-11
running fdisk as suggested results in:

fsck 1.41.3 (12-Oct-2008)
e2fsck 1.41.3 (12-Oct-2008)
fsck.ext2: No such file or directory while trying to open /dev/sdax

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;


I don't know what this means.

---

### Post by gigi1234 on 2010-01-11
I am able to access the Ubuntu partition. And I can copy some files but not others. For some reason some files and folders are restricted while others are not. 

I will have to go to bed soon but please check back on this thread because I am gonna need more help I think. This problem is beyond my skills I have a feeling. 

I am going to try to boot in rescue mode and copy the files from the command line. 

Maybe that will work?

Thanks for helping!

---

### Post by JC Cheloven on 2010-01-11
So now you can access the files? Did you boot and shutdown, or simply it's about a random behaviour?
If in the live session some folders are accesible while others don't, you can do as an emergency measures: 
1) run nautilus as root (gksudo nautilus) or 
2) run a command like "chmod -R 777 <path_to_folder>", where <path_to_folder> is to be replaced by the path to a parent folder of the unaccesible files, something as /media/mydisc/myfolder

As for what you did with Carlee's advice: Either fsck doesn't support ext4 (the man pages aren't clear on this point) or you've take literally "sdax", which was meant to be replaced by something as "sda2". Either way, the manpages of e2fsck explicity say "ext4 support", so try from live session:
```
sudo e2fsck -p <yourdevice>
```
where <yourdevice> is /dev/sda2 or whatever your ubuntu is in. This will repair your device in quiet mode (no questions to you).

---

### Post by gigi1234 on 2010-01-12
oh DUH! In my panic I am not thinking at all. 

I ran the fsck and got this:

/dev/sda7: recovering journal
/dev/sda7: clean, 231331/2244608 files, 4959250/8952213 blocks

so...?

I can access some of the files using the Crunchbang pendrive OS. And I have saved some of them but some of them have permissions on them that won't allow me to copy them. I have no idea what to about it!

---

### Post by JC Cheloven on 2010-01-12
> **gigi1234 said:**
> 
I can access some of the files using the Crunchbang pendrive OS. And I have saved some of them but some of them have permissions on them that won't allow me to copy them. I have no idea what to about it!
Have you tried what I suggested in #9 (first lines) about running nautilus as root or using chmod? How was it?

---

### Post by gigi1234 on 2010-01-12
Great, the gksudo nautilus idea worked and I recovered all my files onto an external drive. Now I wonder, can I reinstall Ubuntu? 

I don't really understand the implications of having bad sectors. 

I also ran the e2fsck -p /dev/sda7 as suggested. But the system is still acting weird. I can boot up and sometimes open my external drive from the desktop but then the whole system freezes and I can't do anything. 

Ctrl+Alt+Delete does not work in this case to shut down.

---

### Post by JC Cheloven on 2010-01-12
> **gigi1234 said:**
> Great, the gksudo nautilus idea worked and I recovered all my files onto an external drive. Now I wonder, can I reinstall Ubuntu? 

I don't really understand the implications of having bad sectors. 

I also ran the e2fsck -p /dev/sda7 as suggested. But the system is still acting weird. I can boot up and sometimes open my external drive from the desktop but then the whole system freezes and I can't do anything. 

Ctrl+Alt+Delete does not work in this case to shut down.

Well, some progress. Nice! 

And fsck ,or e2fsck for that matter, reported "clean" status, which is good, although I'm not very confident about what it did (I don't think it made a surface exploration). Anyway:

IMO it's not worth to put more effort in your damaged ubuntu install. Let's do a fresh one, [COLOR="Blue"]deleting and reformatting the partition first,[/COLOR]  and see how it goes. Perhaps you have not bad sectors but simply wrong sectors. 

Of course, before doing the new install, you may want to do some checking on the partition using smartmonntools or badsectors. See here:
[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

Note: Bad sectors aren't so bad if they're not used. AFAIK there are mechanisms to let the OS know if a sector is bad, so that it won't be used. I'm not an expert though, and I wouldn't rely on that whole disc any more if you experience further problems.

---

### Post by gigi1234 on 2010-01-12
Hey thanks for all your help! I really appreciated it. I had been wanting to upgrade to 9.10 so this problem just pushed me over the edge. I did the installation using the same partition I had been using and it seemed to go fine, works fine. 

Thanks again!

---

