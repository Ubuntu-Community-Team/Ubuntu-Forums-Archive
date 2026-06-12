---
title: "how to install ubuntu onto windows partition"
date: 2010-11-23
forum: New to Ubuntu
---

### Post by xiongnu on 2010-11-23
hi, guys

I have a windows xp machine that crashes a lot(blue screen of death) and i've tried many different methods ( swap out memory, updating video drive, installing new fans, reinstall windows) to fix it in vain.  i am not sure whether it's a software compability issue or hardware problems.  

anyway, finally i'm fed up and decide to try ubuntu on it.  it has a 640GB sata hard drive, and is currently divided into 4 partitions (40G/100G/200G/300G respectively).  The os is on the 40G partition, with movies/games/mp3 music on the rest 3 partitions).  I'd like to try the dual boot configuration first, if it went well, then get rid of windows completely.  the dilemman i have is that i want to keep the files on the rest 3 partitions  instead of wipe everything clean.  but i heard that you can't install ubuntu onto one partition, you have to wipe the hard drive clean.  is that true?  

thanks

---

### Post by Hippytaff on 2010-11-23
No that's not true...when you install from live cd/usb, you will be given the option to manually assign partitions, wipe the disc, of boot along side windows.
 
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 
Wait...I think I misunderstood your question...though the manually assigned option during installation should allow you to leave those partitions in place :-)

---

### Post by QLee on 2010-11-23
Hippytaff,
Don't forget to consider whether or not all four of those volumes are primary partitions or not, could make a difference given the description of what the OP wants to do.

---

### Post by Hippytaff on 2010-11-23
> **QLee said:**
> Hippytaff,
Don't forget to consider whether or not all four of those volumes are primary partitions or not, could make a difference given the description of what the OP wants to do.
 
That's a good point.
 
Maybe have a quick read of this to clarify partitioning (Windows has to be installed on a primary partition etc) [http://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition](http://en.wikipedia.org/wiki/Disk_partitioning#Primary_partition)

---

### Post by Timo0060 on 2010-11-23
In my opinion, to install Ubuntu on your computer, just download wubi. I used it and what it does is it basically sets up the os already partitioned. It gives you the option for the hard drive size, i believe the largest is 30 gbs, but once it's done, at teh start up of your machine, you should be able to choose wether or not to run ubuntu, or xp. I did it and now i can run Kubuntu and windows 7 on my laptop, i have no problems with it. I hope that helped.

---

### Post by Hippytaff on 2010-11-23
> **Timo0060 said:**
> In my opinion, to install Ubuntu on your computer, just download wubi. 
 
I don't like wubi, it has a habit of going bad after a while, but it's ok for trying ubuntu out for a bit. That's just me though :-)

---

### Post by gs17 on 2010-11-23
> **Hippytaff said:**
> I don't like wubi, it has a habit of going bad after a while, but it's ok for trying ubuntu out for a bit. That's just me though :-)


I agree with Timo0060. If you want to only try out if ubuntu without changing partitions, WUBI is the way to go. You will get a good idea about if all of your hardware works smoothly with ubuntu. It will also look just like a dual-boot system. 

Also, I would suggest when you install WUBI, do it on a partition different from the one on which windows is installed. 

Good Luck

---

### Post by xiongnu on 2010-11-23
thanks for the replies, guys!

to clearify:
of the four partitions, only the 40GB C:/ is the primary partition. with windows xp installed onto this partition, the rest three are logical drives. The reason i want to keep windows is that i've many games installed,  and i don't want to lose the ability to play them.  otherwise i would just wipe windows clean.

I'm interested to hear more on 'wubi'.  i want to be able to access(read+write) the rest 3 partitions(NTFS file system) once i installed linux.  but according to the post, wubi only supports up to 30GB.  is that true?

---

### Post by Hippytaff on 2010-11-23
> **Hippytaff said:**
> ...but it's ok for trying ubuntu out for a bit.  :-)
 
Just wanted to clarify that ^
 
and this is a good wubi reference - [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by mike555 on 2010-11-23
If you don't already have four primary partitions just use a live cd to make another logical partition and do a real install to it .

---

### Post by Timo0060 on 2010-11-23
As far as I know, Wubi only suports 30gb, thats to my knowledge. It's the max amount I got, I believe. and xiongnu, it works really well because I was running Kubuntu in a virtual box, then I discoverd wubi, and before it was choppy adn slow, but now it's great. I like it a lot, but that's just my opinion. hope it helped, adn a lot of the time, you can google the answer, although the forums are a great place to find things out. Just thought i should mention that.

---

### Post by zipteye on 2010-11-24
If theres nothing on your logical drives that you want to keep then just delete them.
Then 'Shrink' your C: drive by about 5 gb.
 
Download Ubuntu and make a live disk. burn .iso image to DVD
Stick the disk in the cd/dvd drive.
Choose the install option.
Choose free space.
 
If I remember right, thats what i did.
Did it with Windows 7 though.

---

### Post by gs17 on 2010-11-24
> **Timo0060 said:**
> As far as I know, Wubi only suports 30gb 

The 30 GB limit is on how large your linux partition will look. It is not a limit on the actual size of the logical partition. Your linux partition will not be really be registered in the partition table, but only be a part of an already existing volume.

Finally, you could carve out a few GBs and install Ubuntu, but the problem with it is that you will soon realize that you need more space in your linux partition (to install any software etc). Then you have to learn either how to extend the linux partition etc. So, IMHO it is a good idea if you can shrink any of your drives to makes space of upto 30-40 GB. 

Anyways, I guess you have plenty of options to explore. And that will continue to happen as you go more and more into linux. 
Good Luck!

---

### Post by K25125 on 2010-11-24
I'd stay away from Wubi if I were you; It would cause a few problems if you wanted to remove Windows completely (I think you can install it on a second partition, but then why not just do it from USB?). Personally, I installed Ubuntu to try it out in just a small partition, ready to see what I could do with it; get familiar with the environment. Soon, I shrunk Windows down to the smallest possible size, and, eventually, deleted it in favor of Ubuntu with a Windows 7 virtual machine under VirtualBox.

Regarding the games, I've found Wine to work really well with some games, including Steam games (I've seen Garry's Mod work flawlessly, and it wouldn't be too much of a stretch to assume my other Source games, such as Counter Strike, would work too). If you want to check if a game works, there's a fairly large database at [http://appdb.winehq.org/]("http://appdb.winehq.org/") (including games and software).

The best way to see if this all works for you, though, is just to try it out :)

Good luck!

---

### Post by Timo0060 on 2010-11-24
Well I believe that K25125 is right if you want to remove windows completely, but if you're like me and you want both windows and Ubuntu, then Wubi would be a grreat start.

---

