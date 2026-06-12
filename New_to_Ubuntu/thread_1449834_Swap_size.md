---
title: "Swap size"
date: 2010-04-08
forum: New to Ubuntu
---

### Post by kakashi_12 on 2010-04-08
I'm making a new system. 64 bit Quad core at 2.4 Ghz. 6 GB ram. Should I go with 32 bit or 64 bit Ubuntu? How big should I make my swap partition? Some other forums I read said equal to the size of your ram and some say twice the amount of your ram. Which is it really? Can I make it a logical partition? Cause I'll be doing a quad-boot, taking up all my available primary's.

---

### Post by Didius Falco on 2010-04-08
> **kakashi_12 said:**
> I'm making a new system. 64 bit Quad core at 2.4 Ghz. 6 GB ram. Should I go with 32 bit or 64 bit Ubuntu? How big should I make my swap partition? Some other forums I read said equal to the size of your ram and some say twice the amount of your ram. Which is it really? Can I make it a logical partition? Cause I'll be doing a quad-boot, taking up all my available primary's.

To enable use of all 6 gigs of your ram, you should go 64 bit. The 32 bit hits a 4 gig limit, and why have ram unavailable for use?

Also, with 6 Gigs of ram, unless you are doing very memory-intensive tasks (like editing huge chunks of video, for example), you don't need to double the size of your ram for your swap file. I'd match it in size, but only to be on the cautious side, and because HD space is so very cheap these days.

You can make it a logical partition, no problems there. Also, if you are booting more than one linux distro/version, you only need one swap file that can be used by them all.

Have fun!!

Regards,

Didius

---

### Post by warfacegod on 2010-04-08
Go with 64, you'll get some performance boosts over 32.

Swap size depends on what you are going to do with your system. I don't have a swap space at all and my system runs slightly faster without it (P4 2.8 Ghz Hyper Thread w/ 2 GB RAM Toshiba Satellite). If you are going to be using Suspend/Hibernate (I forget which uses swap), I'd go with a swap that is slightly bigger than your RAM. If you are going to be doing video encoding, doubling the size might work out well.

Those are pretty much the only uses for swap. If you aren't going to do either then don't even bother making a swap partition.

You can get around the 4 primary partition thing by putting your Swap on another drive. You'll need to mark it as Extended no matter what drive you put it on.

---

### Post by kakashi_12 on 2010-04-08
thanks a lot. no, my other boots will probably be win. but thanks for the info, good to know. thank you.

---

### Post by phillw on 2010-04-08
> **kakashi_12 said:**
> Can I make it a logical partition? Cause I'll be doing a quad-boot, taking up all my available primary's.

Unlike, say, Windows Ubuntu is quite happy to live on an extended partition. Make your last available primary partition (you can have only 4) an extended one. Once in the extended partition you have many partitions in there :-)

Regards,

Phill.

---

### Post by tad1073 on 2010-04-08
> **Didius Falco said:**
> To enable use of all 6 gigs of your ram, you should go 64 bit. The 32 bit hits a 4 gig limit
Didius

he can use 32 bit with a PAE kernel which will give him 5.9gb's out of 6gb's, where as, the 64 bit gives 5.8gb's out 6gb's, but either way, 64 is the way to go...

---

### Post by undecim on 2010-04-08
With 6GB of ram, I wouldn't even create a swap partition unless you need to use hibernation. In which case I would match the size of your ram.

Also, 64 bit is excellent. I haven't had any issues with it, and stuff generally runs faster.

---

### Post by Kirk M on 2010-04-08
> **kakashi_12 said:**
> I'm making a new system. 64 bit Quad core at 2.4 Ghz. 6 GB ram. Should I go with 32 bit or 64 bit Ubuntu? How big should I make my swap partition? Some other forums I read said equal to the size of your ram and some say twice the amount of your ram. Which is it really? Can I make it a logical partition? Cause I'll be doing a quad-boot, taking up all my available primary's.

The following is an excellent thread about partitioning for an Ubuntu/Linux MInt install which includes a good explanation about swap partitions and whether or not you need one and what size it should be.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=11872](http://forums.linuxmint.com/viewtopic.php?f=90&t=11872)

**Note:** The first several posts mention ext3 in reference to the root and home partitions instead of ext4. Just substitute ext4 where it mentions ext3 and you're good to go.

Also, this is a thread on the Linux Mint forums but Mint is an Ubuntu derivative and the subject applies to both OS's. Besides, were all one big happy family, right? =D>

---

### Post by kakashi_12 on 2010-04-08
Two more questions then...
 
1. What is the difference between ext3 and ext4? I always used ext3 in the past only cause I was told to. I'm assuming ext4 is for 64 bit??
 
2. Where can I download 64 bit Ubuntu (either 8 or 9 will work)? I can't find it anywhere.

---

### Post by tad1073 on 2010-04-08
> **kakashi_12 said:**
> Two more questions then...
 
1. What is the difference between ext3 and ext4? I always used ext3 in the past only cause I was told to. I'm assuming ext4 is for 64 bit??
 
2. Where can I download 64 bit Ubuntu (either 8 or 9 will work)? I can't find it anywhere.

ext4 is a new file system

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by oldfred on 2010-04-08
On the link to Ubuntu downloads click on alternatives.

Ext4 when it first came out was an upgrade to ext3 touted as much faster. It was also less reliable in the beginning. In fixing the issues it now is only a little faster but reliability has improved to the point where I saw google was converting to ext4.

You mentioned multiple windows installs. If you want to directly boot each not thru the one with the boot flag:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by kakashi_12 on 2010-04-08
> **oldfred said:**
>  
You mentioned multiple windows installs. If you want to directly boot each not thru the one with the boot flag:
To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
 
I'm not sure what you're talking about. boot flag and "directly boot each not thrue the one". ???? ....
But I've done dual booting before a few times, so I don't think I'll have any problems.

---

### Post by phillw on 2010-04-08
> **tad1073 said:**
> ext4 is a new file system

ext4 *was* a new file system, it has been the default since 9.10; there is a new file system coming along as ext4 was an 'extension' of ext4 from ext3. You may see it raise it head with 10.10, or possibly a bit later.

You can have a read of it over here -->  [https://btrfs.wiki.kernel.org/index.php/Main_Page](https://btrfs.wiki.kernel.org/index.php/Main_Page)

Some are already running it.

Regards,

Phill.

---

### Post by HermanAB on 2010-04-08
Note that if you want to use Suspend, then your Swap partition has to be twice the size of your RAM.

---

### Post by jms1989 on 2010-04-08
deleted

---

### Post by jms1989 on 2010-04-08
> **HermanAB said:**
> Note that if you want to use Suspend, then your Swap partition has to be twice the size of your RAM.

That is only true for hibernation and you should never have your swap twice as big, its wasteful. A couple hundred megs bigger than what your system has is more than acceptable for hybernation. I suspend my machine with 8gb of ram and 2gb of swap. I don't hybernate it.

EDIT: If you find yourself using your swap then you really should upgrade your ram. Utilizing the hdd for swap is extremely slow, in my opinion, so I'd advise its use for emergency resort and hybernation if you want.

---

### Post by egalvan on 2010-04-08
> **Kirk M said:**
> The following is an excellent thread about partitioning for an Ubuntu/Linux MInt install
 which includes a good explanation about swap partitions and whether or not you need one and what size it should be.

[http://forums.linuxmint.com/viewtopic.php?f=90&t=11872](http://forums.linuxmint.com/viewtopic.php?f=90&t=11872)]

Agreed, it's a good tutorial, but as in many things Internet, it is now a bit dated...
the original article dates from two years ago,
the last update show a year ago...
that's a long time in Linux-Land...

The essential ideas are good, but some of the details are dated...

> 
Considerations before you install

Postby Fred on Sun Apr 27, 2008 10:48 am

Things that could/should influence your partitioning layout:

1) Partitions closer to the outside of the hard drive disk,,,  are faster than partitions on the inside of the hard drive disk,.

2) Smaller partitions are faster than larger partitions.

1) Back in the Paleolithic days of 8" and 5" drives, this was good advice.
3" drives still see some benefit,
but smaller drives see almost none.

2) Again, modern File System allocation algorithms have reduced the size advantage...

> 
3) Swap partitions don't need to be any larger than 2X your system ram. 
And, **the sum of system ram and swap shouldn't exceed 4 Gig. **
 If it does, reduce the swap partition size to get back to 4 Gig. or less.
 If you have 4 Gig. on a 32 bit system like Mint, make a very small swap partition anyway,
 as the kernel expects to have a swap partition available.
 **Not having a swap partition slows the kernel down in certain situations.**
 For this purpose, there is no need for the swap partition to be over 256 KB at most.

3) The 4Gig RAM/swap size limits on Linux evaporated with the 2.6 kernel.
Some 2.4 kernels had also removed this limit.
Not so true in Windows-land, so the FUD myth stayed around in Linux-Land
 (yes, **SOME** 32bit Linux and **SOME** 32-bit hardware are limited to 4G, but this was more the exception.)

The need to have *some* swap is very kernel dependent.

> 
4) If you have more than one hard drive, split your swap partition up between all your drives,
creating a small swap partition on each drive.
Linux will recognize and combine them all and your swap will be much much faster **when you need it**.
It is almost like a raid 0 set-up. Swap will strip across drives.

4) Splitting swap across multiple hard drives has always been beneficial,
especially on drives that live on separate channels.
**If it's used.**

> 5) **Journaled file systems** like ext3 are much** better at maintaining read/write data integrity**
in case of power failure or some other unexpected crash or failure.

5) Absolutely true, and still valid.
And an excellent reason to use a journaled file system for everything that is important.

> 6) Journaled files systems also represent more overhead to the kernel
and take more space on the hard drive for the file system structure itself.
 There is no advantage to using a journaled file system on a partition that will rarely be written to.
/boot is a good example of this.
It is almost never written to, so if you use a separate /boot partition, it should be ext2 and not ext3.

6) Again, all true, but space considerations are not the same with TERA-byte drives than they were with MEGA-byte drive...
and, again, the algorithms have improved, with data safety a prime objective.

> 7) If you use a separate /boot partition, it doesn't need to be more than about 256 MB.
 This still leaves plenty of space for extra kernels and boot notes.

7) Linux kernels are pushing this limit :P
Seriously, just keep track of number of older kernels,
or give /boot more room from that TERA-byte of space :)



> 8) Your data should be isolated from your main install to protect it and easily enable upgrades and reinstalls.


8) So VERY true. I've been doing this since Day One (circa 1979)
And have never stopped isolating data.

> **Note:** The first several posts mention ext3 in reference to the root and home partitions instead of ext4.
 Just substitute ext4 where it mentions ext3 and you're good to go.

Yep, progress marches on.

> 
Also, this is a thread on the Linux Mint forums but Mint is an Ubuntu derivative and **the subject applies to both OS's**. 
Besides, were all one big happy family, right? =D>

GNU/Linux is a big family, and the subject applies almost equaly well to all of it.  :)

---

