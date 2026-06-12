---
title: "32 bit OS &amp; 4 GB or GiB ram?"
date: 2009-03-18
forum: New to Ubuntu
---

### Post by alanwalterthomas on 2009-03-18
I've spent nearly an hour reviewing articles & forums but I haven't found a clear & consistent answer to this:

** If I buy ram sold to me as 4x1GB sticks will it all be used (somehow) in a 32-bit OS? **

I've mostly seen: yes, it's all available to the computer; no, you only get ~ 3.2 GB; no you get less than 4 GB because devices like the video card use some of it.

I'm fine with the video card using some of the ram, leaving with 3.x GB for applications etc, because it's still used productively. (I assume that the same overhead would be subtracted if I had 2 or 3 GB & the video card takes care of mapping its own onboard ram, right?)

I thought it might be a GB Gib conversion issue, but a calculator told me 4.096 GB (10^n) = 3.8147 GB (2^n) which doesn't account for the ~ 3.2 GB figure I see everywhere.

Thanks,

---

### Post by Botbob89 on 2009-03-18
There is no clear and consistent answer simply because it changes depending on the machine you are going to use it on. The hardware you have differs greatly from person to person, and as this all affects matters such as this, there can be no one clear answer as everyone has different machines

---

### Post by lswest on 2009-03-18
To the best of my knowledge a 32 bit OS can access and use >3.2GB of RAM using a custom kernel (the server edition, for example, has one such kernel) that allows for the OS to use more memory than other 32bit OSes usually can.  Otherwise 64bit will use and be able to access more than 3.2GB of RAM using any kernel, since it's one of the "features" of a 64 bit OS.

I'm not sure what the kernel mod is called, but if you're comfortable with it I'd suggest just installing the server version of ubuntu and installing the stuff you usually use, otherwise I'll have a look and see if I can find the name of the specific kernel, I'll post back if I find it (unless someone here posts it before I find it).

Hope that helps,
Lswest

*EDIT* you can do what this person describes: [http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/](http://samiux.wordpress.com/2008/06/15/use-more-than-3gb-ram-on-32-bit-ubuntu-804/)  which is just installing Ubuntu as usual, then installing the server kernel using apt-get.

---

### Post by Weidbrewer on 2009-03-18
4GB is the theoretical max on 32-bit...however, this is total, any other RAM (such as the above mentioned graphics card) will come off of that total.  It has generally been my experience that buying over 3GB of RAM for a 32-bit machince isn't really cost effective.  For example, I bought 4GB of RAM for a machine, and the 32-bit partition only was able to use 3.2GB of it - so why buy an extra gig only to use 200MB of it?

If you want to effectively use 4-16GB of RAM, you'll need to use a 64-bit OS.  The other important part of that equation is that you will need equipment set up to use 64-bit software.  I hope that this helps.

---

### Post by philinux on 2009-03-18
> **Weidbrewer said:**
> 4GB is the theoretical max on 32-bit...however, this is total, any other RAM (such as the above mentioned graphics card) will come off of that total.  It has generally been my experience that buying over 3GB of RAM for a 32-bit machince isn't really cost effective.  For example, I bought 4GB of RAM for a machine, and the 32-bit partition only was able to use 3.2GB of it - so why buy an extra gig only to use 200MB of it?

If you want to effectively use 4-16GB of RAM, you'll need to use a 64-bit OS.  The other important part of that equation is that you will need equipment set up to use 64-bit software.  I hope that this helps.

Some background on memory limits. This is I'm afraid nor true "4GB is the theoretical max on 32-bit", 32 bit can and has addressed more with PAE [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension).

To the OP how much memory do you need, have you got some memory hungry app?

---

### Post by Weidbrewer on 2009-03-18
Good point.  I guess I should have said, "...under normal circumstances."

The main reason that I did not bring up PAE is that I figured it would open a whole different can of worms:

> The 32-bit size of the virtual address is not changed, so regular application software continues to use instructions with 32-bit addresses and (in a flat memory model) is limited to 4 gigabytes of virtual address space.

So I guess that brings us to the question of definition:  What do we mean by "using all of it"?  As you asked below, are we talking about one app that needs to access it all, or do we just mean using it all in general?

---

### Post by lswest on 2009-03-18
> **philinux said:**
> Some background on memory limits. This is I'm afraid nor true "4GB is the theoretical max on 32-bit", 32 bit can and has addressed more with PAE [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension).

Ah, PAE, that's what I was talking about :P  I am correct in thinking the Ubuntu server kernel provides it by default, right?  Been a while since I used Ubuntu (server or otherwise) as 32bit.

---

### Post by gn2 on 2009-03-18
AFAIK recent 32-bit server version can use 4gb per process up to a maximum of 64gb total.

---

### Post by sdennie on 2009-03-18
[ Ubuntu with 4GB+ of memory]("http://ubuntuforums.org/showthread.php?t=855511")

---

### Post by alanwalterthomas on 2009-03-18
Hi, thanks for the responses, but I still don't understand much w r t my original question.
I'm not interested in PAE. I'm trying to figure out how much ram a vanilla ubuntu can make use of, & if it's less than 4096 MB, why?
Where does 3.2 GB come from? I've read a couple theories, which is correct?
 - Vista uses an 800 MB page file for virtual ram (whatever that is), ppl use Vista, so that's where 3.2 GB comes from (so all the ram I buy would be used, just not shown because some of it's not available to applications)
 - Still a GB vs GiB issue where there are 3814.7 MB, of which 500 & change are devoted to things like video cards, leaving about 3.2 GiB. (again all the ram I buy is used)
 - Hardware addressing requires some of 4096 MB that can be allocated to either ram or other hardware addressing (so not all the ram I buy can be used because some addresses are allocated to non-ram use; should vary more, I keep seeing 3.2 GB)
 - The sum of RAM & swap file in use cannot exceed 4 GB (not sure what that would do)
 - The computer gods picked a number out of a hat & decided to limit 32 bit ram to 3.2 GB

So where does 3.2 GB come from? I've seen 3.5 too sometimes. Is 4 GB usable on *stock* ubuntu so long as my video card uses its own memory?

Side questions: Does ubuntu make use of "extra" ram? I.e. does the system keep working at the same speed until the last block of ram memory is used up & then slow to a craw when it needs to use swap for everything, or would doubling 2 GB ram do some good even if system monitor shows I rarely use more than 756 MB? Does (can) it precache like vista sometimes?

thanks

---

### Post by alanwalterthomas on 2009-03-18
sdennie, just read through your link, thanks, good to know
so I understand some of the 4096 MB will sit idle. However, I'm still curious to know/predict how much. 500+ MB sounds like a lot if it's not being taken up by the video card. Supposing the video card takes care of its own ram, what is it that takes up so much memory? I thought it would be more reasonable to use ~96 MB for whatever else is going on - what is going on?

---

### Post by LowSky on 2009-03-18
Just going to put this out there, I using Ubuntu 64  with 4GB of RAM (only 3.899 shows up, no idea why, anyway) and its running  just fine with like 16 apps open, including a HD Rip of a movie, And I'm only using 900 Mb of RAM


Try doing that in Windows Vista!

---

### Post by shazbut on 2009-03-18
Great (long) explanation of it all here:
[http://www.dansdata.com/askdan00015.htm]("http://www.dansdata.com/askdan00015.htm")
A bit of a history lesson too.

---

### Post by sdennie on 2009-03-18
> **alanwalterthomas said:**
> 
So where does 3.2 GB come from? I've seen 3.5 too sometimes. Is 4 GB usable on *stock* ubuntu so long as my video card uses its own memory?


No.  You must not have read my link.  In a 32-bit address space, various parts of the machine need to have addressable memory and that means that less of the physical memory is addressable.  Sometimes they need a lot (the video card for example).  The 3.2GB number is invented by people who don't understand the issue.  The amount of RAM you are able to use with a 32-bit non-PAE kernel will always vary from machine to machine but will ALWAYS be less than 4GB (probaby somewhere between 2.8G and 3.5G).

> 
Side questions: Does ubuntu make use of "extra" ram? I.e. does the system keep working at the same speed until the last block of ram memory is used up & then slow to a craw when it needs to use swap for everything, or would doubling 2 GB ram do some good even if system monitor shows I rarely use more than 756 MB? Does (can) it precache like vista sometimes?


Ubuntu (or more accurately, the linux kernel), handles RAM far, far more efficiently than Windows.  With 2GB of RAM, you probably don't need to have any swap.  With 4GB of RAM, you almost certainly don't need swap because the kernel will never use it.  Ubuntu uses "extra" RAM to cache the disk.  So, it will run faster the more RAM you give it.  With more than 1GB of RAM, for a desktop user, you'd be hard pressed to actually make it use swap.

---

