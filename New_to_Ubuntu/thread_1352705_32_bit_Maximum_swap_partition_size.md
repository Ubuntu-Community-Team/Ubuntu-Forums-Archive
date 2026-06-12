---
title: "32 bit Maximum swap partition size"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by fox123 on 2009-12-11
I getting ready to install the 32 bit version of karmic. This Laptop has **3 GB's** of ram. What I want to do is setup a **6 GB swap partition**, To make sure that I have enough space put the computer to sleep without losing any of my work. Will Ubuntu recognize a swap partition this large? and is there anything special I need to do to set this up?

---

### Post by abeisgreat on 2009-12-11
> **fox123 said:**
> I getting ready to install the 32 bit version of karmic. This Laptop has **3 GB's** of ram. What I want to do is setup a **6 GB swap partition**, To make sure that I have enough space put the computer to sleep without losing any of my work. Will Ubuntu recognize a swap partition this large? and is there anything special I need to do to set this up?

It should work fine. I've had up to 5-6gb swaps before, never had an issue, try it, if it doesn't work, come back here :P

---

### Post by bumanie on 2009-12-11
> How large can my swap space be?
Currently, the maximum size of a swap partition is architecture-dependent. For i386, m68k, ARM and PowerPC, it is "officially" 2Gb. It is 128Gb on alpha, 1Gb on sparc, and 3Tb on sparc64. An opteron on the 2.6 kernel can write to a 16 Tb swap partition.
Hope that helps.

---

### Post by abeisgreat on 2009-12-11
> **bumanie said:**
> Hope that helps.

I could have sworn the, albeit outdated, standard was double ram in swap. Anything with more than a gb of ram following that rule passes that limit. Any idea why it's so low, or better yet, have a source for that quote?

---

### Post by fox123 on 2009-12-11
Thank you both.
 
I guess I'll set it up with a 2 GB swap partition and just hope for the best. :) 
Too bad you can't setup more then one swap partition to get around the 2 GB limit.

---

### Post by jacobs444 on 2009-12-12
unless you leave an absolutely ridiculous amount of programs running all the time, you should not ever go over the 2gb of swap. Actually I don't (don't quote me)  think that the swap is where the info is stored for hibernation. Swap is there in case you run out of ram, just like the page file in windows. I am pretty sure you won't have any issues with a 2gb swap. Personally I think that any larger is just a waste of HD space.

---

### Post by jacobs444 on 2009-12-12
to test this i turned off the swap.

sudo swapoff -a

and i suspended and hibernated the computer, so indeed linux does not use swap in the way you are thinking.

---

### Post by lswb on 2009-12-12
> **jacobs444 said:**
> to test this i turned off the swap.

sudo swapoff -a

and i suspended and hibernated the computer, so indeed linux does not use swap in the way you are thinking.

You have stopped the running OS from using swapping to disk but it still uses the swap partition for storage when it hibernates.

---

### Post by jacobs444 on 2009-12-12
ok, the point remains un-moot that 2gb is plenty of swap. I still think you are wrong, as when I install without swap, I still have no problem with suspend/hibernate, but thats not what we are here  for.

---

### Post by musarraf172 on 2009-12-12
> **jacobs444 said:**
> unless you leave an absolutely ridiculous amount of programs running all the time, you should not ever go over the 2gb of swap. Actually I don't (don't quote me)  think that the swap is where the info is stored for hibernation. Swap is there in case you run out of ram, just like the page file in windows. I am pretty sure you won't have any issues with a 2gb swap. Personally I think that any larger is just a waste of HD space.

You mast have swap for hibernation. You are right that swap is used when the system runs out of ram. But during hibernation the content of ram is written as image in swap area.

---

### Post by Bartender on 2009-12-12
It's been said over and over on these forums that you only need a bit more swap than RAM for hibernation.  If you have 3 GB of RAM, then 3.5 GB swap would be plenty.

---

### Post by JBAlaska on 2009-12-12
> **fox123 said:**
> Thank you both.
 
I guess I'll set it up with a 2 GB swap partition and just hope for the best. :) 
Too bad you can't setup more then one swap partition to get around the 2 GB limit.

What 2GB limit?? never heard of it.

And Linux can use multiple swap partitions even on separate drives.

If you have = >3GB ram, 1.5GB swap is plenty.

---

### Post by louieb on 2009-12-12
> **fox123 said:**
> Too bad you can't setup more then one swap partition to get around the 2 GB limit.

You can have more that one swap partition. The **free **command shows the total swap as the sum of both. 

> It's been said over and over on these forums that you only need a bit more swap than RAM for hibernation.  
+1 - thats been my experience too. The only PC I have ever hibernated had 1GB ram and 1.1GB swap.

---

### Post by Bartender on 2009-12-12
louie, thanks for the backup.  I don't really KNOW that you just need a bit more swap than physical RAM, just read it many times here at Ubuntu Forums.

Seems to me a lot of people are confusing the original swap function with the new one.  Swap was important back in the day when PC's came with 256 or 512 of physical RAM and could easily get busy enough to ask for more.  Way I understand it, that was the original reason for virtual memory (swap).  

Nowadays, with modern PC's rockin' 2GB or more of RAM, the traditional need for swap rarely comes up.  So swap's main reason for existence now seems to be allowing hibernation.

An interesting aside to this, for those who haven't checked - if you're dual-booting Vista and Ubuntu, go into Windows' Task Manager and check RAM usage.  At idle, Vista uses almost a gig of RAM.  Now get out of Vista and boot into Ubuntu, which uses about 350 - 400 MB RAM.

---

### Post by jacobs444 on 2009-12-19
> **musarraf172 said:**
> You mast have swap for hibernation. You are right that swap is used when the system runs out of ram. But during hibernation the content of ram is written as image in swap area.
  

you are correct, though it absolutely is not needed for suspend!

---

### Post by jacobs444 on 2009-12-19
> **Bartender said:**
> It's been said over and over on these forums that you only need a bit more swap than RAM for hibernation.  If you have 3 GB of RAM, then 3.5 GB swap would be plenty.

utterly ridiculous, you need a liitle more than the used amount of ram, read my original comments sans the hibernation, linux is retarded for using swap for this function.

---

### Post by audiomick on 2009-12-19
For those who are interested:
[https://help.ubuntu.com/community/HibernateWhatHappens](https://help.ubuntu.com/community/HibernateWhatHappens)

According to that

> the Hibernate message is actioned.. It checks...
...that there is enough swap (based on values previously read from /proc/meminfo) ...

so hibernate does use the swap space. The question is, what exactly is in /proc/meminfo ? Is it the total available swap, or that which is currently being used?


Also according to this
[http://manpages.ubuntu.com/manpages/hardy/man8/pm-hibernate.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pm-hibernate.8.html)

which applies to 8.04 LTS at least
>  pm-suspend
           Suspend is a state where most devices are shutdown, except for RAM.
           This state still draws power.


RAM is still alive in suspend, therefore it would not be written to the swap space. 

I don't know how much of that applies, but had to go and look after reading the discussion here...:)

---

