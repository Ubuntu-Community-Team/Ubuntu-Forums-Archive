---
title: "New PC, which file system and 32bit vs 64bit?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by edmicman on 2010-03-10
I've been using Ubuntu since 8.04, I'm currently running 9.10 on an old Dell Inspiron laptop.  I'm upgrading to a Thinkpad T500 and plan on doing a fresh install.  I've got two questions:

Should I go 64-bit, or 32?  I'm thinking 64, but what kinds of problems might I run into?

Should I go with EXT4 or EXT3?  I thought ext4 was the default for a new install, but I remember seeing there were some problems that were being ironed out?  All the posts I find seem to be older and talk about staying with ext3, but that 4 is coming along and should be stable.  But most of those are older posts, too.

So what is the current state at this point?  Thanks!

---

### Post by Tikkyca on 2010-03-10
Well i use 32bit,you can use 32bit or 64bit,but you need to have 64bit proccessor to use 64bit,also you can use 32bit with 64bit proccessor,but if you have 32bit you can only use 32bit,not anything later,the 64bit version handles large amounts of random access memory-ram then the 32bit.

---

### Post by MelDJ on 2010-03-10
for the filesystem: [http://ubuntuforums.org/showthread.php?t=1133719](http://ubuntuforums.org/showthread.php?t=1133719)
i would recommend jfs though

---

### Post by Ferb on 2010-03-10
I have been using 64 bit for a couple of years now the only "problems" is that sometime I have to compile software or "force" 32 bit deb file. Can't realy help you with ext 3/4 question.

---

### Post by Paddy Landau on 2010-03-10
I've had no problems whatsoever with ext4 on two different computers both using Jaunty (one Ubuntu, one Xubuntu).

I know that I used to see lots of complaints on this forum about 64-bit, but these days I don't see any. So, I'm guessing that 64-bit is safe.

If you make separate root (/) and /home partitions, then it won't be a big deal to reinstall 32-bit if you find that the 64-bit gives you problems.

But, as always, ensure that you have a full backup before any reinstall. And if you use encryption for your /home, then take a full unencrypted backup (the encryption is still very user-unfriendly when dealing with problems)!

---

### Post by derrick81787 on 2010-03-10
There were problems with ext4 before Karmic because of an issue with an earlier Linux kernel.  As far as I know, those have been fixed.  I know that I use ext4 and haven't seen any problems.

I would recommend ext4 because ext2,3, and 4 are usually the default file systems for Linux OSes, and ext4 is supposed to be faster and generally better.  You can look around if you want, but I was under the impression that the issues with ext4 have been fixed and were basically due to issues with earlier kernels.

- Derrick

---

### Post by blur xc on 2010-03-10
Here's what I've done on a few laptops- ext4 for /, ext3 for /home, and 64bit.  The only minor issue was finding the 64bit flash player on Adobe's website, and finding out what the proper folder was to stick it in to make it system wide.  ~/.mozilla/etc..../plugins/ only makes it work for that specific user, and I think that's dumb.

BM

---

### Post by Penguin Guy on 2010-03-10
I have tried both 32-bit and 64-bit, ext3 and ext4, and as far as I can tell there is no difference. Once you've made a big decision like those, there's no going back - you'll have to do a fresh install to change it. So I would advise going for the latest stuff (64bit and ext4).

P.S. I am assuming you are relatively computer-savvy, but just incase you should know that [COLOR="Red"]not all computers can run 64-bit[/COLOR].

---

### Post by Paddy Landau on 2010-03-10
One more thing to consider. I understand that the Thinkpad T500 comes with Windows, which makes me suppose that you want to dual-boot.

You probably know already that you can easily access your Windows partition (NTFS) from Ubuntu.

However, to access your Ubuntu partition from Windows, you'll need a suitable driver. If this is important for you, then ext3 is what you need, as you can get an [ext3 driver for Windows]("http://www.ext2fsd.com/"); but you cannot (yet) get an ext4 driver for Windows.

If it's not important for you, then ext4 is fine.

---

### Post by mikee55 on 2010-03-10
I think 64bit is for intense apps such as Video conversion. I haven't used 64bit Linux, but in Windows, I found more apps I needed, more I'd be using 32bit. Still, I believe its all about the speed that the CPU accesses and utilises Memorey . I may be wrong. 

I'm using ext 4, Karmic 32bit on a 64bit old system and have no issues.

Maybe a Poll thread should be made?

Mike:popcorn:

---

### Post by rejuvenate on 2010-03-10
to select 64 or 32....it mainly depends on your level of requirement as such 64 bit will be only useful when your processor is 64bit and RAM is more than 4-6GB then only it will be having significant difference and compare to 32 bit very few 64bit applications are there..so you can have 32 bit otherwise....

---

### Post by mbzn on 2010-03-10
Maybe this will help with the 64/32bit issue,
[http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)
As for ext4 i converted about a year ago, and never had any problems with ext4, as for the ext4 reader for windoze(i dont use it) it might be something to consider.

---

### Post by Paddy Landau on 2010-03-10
> **mbzn said:**
> Maybe this will help with the 64/32bit issue...
The link says, "All modern Intel chips support 64-bit out of the box..."

Hmm... How do I tell whether my computer has a 32-bit or 64-bit chip? It only has 1Gb RAM, so I'm guessing that it's too little to run 64-bit anyway.

---

### Post by QIII on 2010-03-10
This will probably get moved to "Recurring Discussions" in short order.

Here is my spiel:

Use 64 bit OSes if your hardware supports them.

1.  While there used to be a dearth of 64 bit applications, they have become de rigeur in recent years.  Most software developers have ported or are porting applications to 64 bit.

2.  64 bit OSs address significantly more RAM.  More than any motherboard you can buy commercially will physically hold.  A 32 bit OS, which nominally supports 4GB, actually only gives you something on the order of 3.27GB, depending on the size of the memory hole.

3.  The entire industry has effectively moved to 64 bit.  32 bit systems, for as long as they hold out before frying, will continue to need 32 bit OSes.  Remember, in the not to distant past (I've been at this a long time) we went from 8 to 16 bit architecture and then from 16 to 32 bit architecture.  The hangers-on to the previous architecture soon found themselves left far behind.

While there are still people who use horses and buggies, other faster means of transportation are somewhat more desirable.

1GB of RAM is a bit anemic (IMO) for running either 32 or 64 bit OSes.  But that would not preclude the use of a 64 bit OS.  I'd add more.

You can look up your processor on the web and find out pretty easily if it is a 64 bit processor.  What is it?  Maybe someone can tell you off the top of their head.

---

### Post by blur xc on 2010-03-10
> **Paddy Landau said:**
> The link says, "All modern Intel chips support 64-bit out of the box..."

Hmm... How do I tell whether my computer has a 32-bit or 64-bit chip? It only has 1Gb RAM, so I'm guessing that it's too little to run 64-bit anyway.

Here's a dumb little script I wrote, just for fun, that answers this very question-

```
#!/bin/bash

if [ "`uname -a | grep i686 -o`" = "i686" ]
then
    echo Your computer is running 32bit Linux
    if [ -z "`grep ' lm ' /proc/cpuinfo`" ]
    then
        echo and your cpu is only 32bit capable.
    else
        echo but your cpu is 64bit capable.
    fi
else
    echo Your computer is running 64bit Linux
fi
```Of course, it will only work if you already have some Linux distro installed and running.

BM

---

### Post by albert s on 2010-03-10
and it works too,    ;)


if [ "`uname -a | grep i686 -o`" = "i686" ]
> then
>     echo Your computer is running 32bit Linux
>     if [ -z "`grep ' lm ' /proc/cpuinfo`" ]
>     then
>         echo and your cpu is only 32bit capable.
>     else
>         echo but your cpu is 64bit capable.
>     fi
> else
>     echo Your computer is running 64bit Linux
> fi
Your computer is running 32bit Linux
but your cpu is 64bit capable.

---

### Post by J V on 2010-03-10
ext4 is great now (especially with noatime) and if you have 64bit hardware, go for it!

---

### Post by Paddy Landau on 2010-03-11
> **QIII said:**
> 1GB of RAM is a bit anemic (IMO) for running either 32 or 64 bit OSes.  But that would not preclude the use of a 64 bit OS.  I'd add more.
1Gb certainly was anaemic when I used to have Windows. But it's fantastic for Ubuntu.

> **blur xc said:**
> Here's a dumb little script I wrote, just for fun, that answers this very question
Cool! I always thought I had 32-bit, but now I find...
[FONT=Courier New] Your computer is running 32bit Linux
but your cpu is 64bit capable.[/FONT]
I checked /proc/cpuinfo and it shows both CPUs (I have dual-core) as 64-bit.

What does the flag 'lm' mean? Or, where can I find documentation on /proc/cpuinfo?
* EDIT* I found a great answer to the [number of processors, cores & virtual processors, and the meaning of lm]("http://www.brandonhutchinson.com/Understanding_proc_cpuinfo.html").

It would be a nice addition to have this shown on the System Monitor, and when loading the Live CD just before installing. Hmm... I think that I'll add this onto the brainstorm.
* EDIT * I've created a brainstorm. I'll post here again if it gets accepted.

> **J V said:**
> ext4 is great now (especially with noatime) and if you have 64bit hardware, go for it!
I shall certainly try when I upgrade to 10.04! If it doesn't work, no big deal.

---

### Post by Paddy Landau on 2010-03-11
> **J V said:**
> ext4 is great now (especially with noatime) and if you have 64bit hardware, go for it!
I believe that some programs depend on noatime, so relatime is better than noatime.

---

### Post by oldos2er on 2010-03-11
> **rejuvenate said:**
> to select 64 or 32....it mainly depends on your level of requirement as such 64 bit will be only useful when your processor is 64bit and RAM is more than 4-6GB then only it will be having significant difference and compare to 32 bit very few 64bit applications are there..so you can have 32 bit otherwise....

 64-bit Ubuntu runs great on 2GB RAM; tasks such as video and audio encoding are noticeably faster than on 32-bit.

 The 64-bit repositories seem to me to be just as full of apps as the 32-bit ones. The only 32-bit + nspluginwrapper "kludge" I need these days is for acroread.

---

