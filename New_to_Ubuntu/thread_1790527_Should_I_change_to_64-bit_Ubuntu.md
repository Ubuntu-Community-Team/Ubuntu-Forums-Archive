---
title: "Should I change to 64-bit Ubuntu?"
date: 2011-06-25
forum: New to Ubuntu
---

### Post by Bearly Able on 2011-06-25
Sorry if this is a daft question but if I don't ask, I won't learn!

I've been using 32-bit Ubuntu, but I'm about to get a new PC which will (apparently) support 64-bit.  Two questions, really.  Is there a real advantage to using 64-bit Ubuntu?  If so, can I still transfer over my home directory from my current machine, or will there be a problem with the configuration files?

I don't use the machine for video editing, on-line gaming or anything else that requires a lot of processing power.

Thanks for any guidance.

Lesley

---

### Post by robertc36 on 2011-06-25
64-bit allows you to have more memory, 32 will only see up to 3gb.
Use deja dup to back up to an external drive and then install it on the new system and restore.

---

### Post by sanderd17 on 2011-06-25
If you have more than 3GB of RAM, 64-bit has a real advantage. If you have 3GB or less, 64-bit has a very slight (not noticeable) advantage.

Switching from 32-bit to 64-bit doesn't change anything to your file system or your configuration files. So that should give no problems.

---

### Post by Matt__ on 2011-06-25
64bit operating systems are consistently faster at such tasks as recoding video/audio, 3d rendering and even javascript/flash running in Firefox.

Of course the larger the amount of RAM you have the better. At 4Gb the gains are positive but not earth shattering so go for 8Gb or more if you can.

I'm currently running the PAE kernel 11.04(supports up to 64Gb ram) and it dosnt seem to make any significant difference at all, but with possible issues of 64bit support for apps and only 4gb ram I wont be going 64bit just yet.(though the likes of java and flash seem to be playing nice with 64 now from what I hear)

[32bit vs PAE vs 64bit]("http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1") benchmarks. (old post but still worth reading)

[Ubuntu help 32 vs 64]("https://help.ubuntu.com/community/32bit_and_64bit")

---

### Post by corncob on 2011-06-25
When I got my new computer I installed 64 bit Natty because I thought that was the thing to do with a 64 bit machine.  However, I did have trouble getting my Canon printer to work.  It said 'wrong architecture' when I tried to install the driver.  I finally got it working but had to take it off the network and connect it directly to the computer.

---

### Post by Paqman on 2011-06-25
> **Lesley Lutomski said:**
> 
Is there a real advantage to using 64-bit Ubuntu?


Yes, any computationally intensive tasks will run significantly faster. Everything else will run at the same speed as 32-bit, or marginally faster.

You could ask "Is there any advantage to running 32-bit on a 64-bit machine?" to which the answer is no. If you've got a 64-bit machine, use 64-bit.

Having said that, the difference is not big. You could use either and it wouldn't make much difference if you're not doing any video re-encoding or the like. But why throttle the machine down if it's capable of more?

---

### Post by Alwimo on 2011-06-25
Flash is terrible in 64-bit. It has a lot of visual glitches. That is the reason I am using 32-bit.

---

### Post by Paqman on 2011-06-25
> **Alwimo said:**
> Flash is terrible in 64-bit. It has a lot of visual glitches. That is the reason I am using 32-bit.

The normal setup is to use 32-bit Flash on the 64-bit system anyway. You don't need to switch your whole system to 32-bit just to get 32-bit Flash, just install [flashplugin-installer]("apt:flashplugin-installer"), which is also part of [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras") anyway.

---

### Post by cchhrriiss121212 on 2011-06-25
For my machine 64bit flash is significantly better than 32. In terms of performance, 64 uses around 10% CPU, whereas 32 uses up to 50%. I am using the 10.2 "square" 64bit plugin found here:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
That is reason enough to use 64bit for me.

---

### Post by Alwimo on 2011-06-25
> **Paqman said:**
> The normal setup is to use 32-bit Flash on the 64-bit system anyway. You don't need to switch your whole system to 32-bit just to get 32-bit Flash, just install [flashplugin-installer]("apt:flashplugin-installer"), which is also part of [ubuntu-restricted-extras]("apt:ubuntu-restricted-extras") anyway.
Oh, that is a big surprise! Thank you for that information. :)

---

### Post by nothingspecial on 2011-06-25
> **Paqman said:**
>  If you've got a 64-bit machine, use 64-bit.



Unless, like me who has both 32 and 64 bit machines, you stuck the 32 bit disc in and didn't notice until you'd installed and configured everything.

I can't be bothered to do it all again.

---

### Post by SeijiSensei on 2011-06-25
I second cchhrriiss121212's recommendation of Adobe's "Square" beta for 64-bit Linux.  It's worked flawlessly for months here.

---

### Post by Bearly Able on 2011-06-25
Thanks guys for all your replies.  I guess I'll give 64-bit a try then.

---

### Post by Bearly Able on 2011-07-04
Just to say I've been running my new machine with 64-bit Ubuntu for about 5 days now, and everything seems to be working "out of the box" - great!  Thanks again to all who replied.

---

### Post by iclestu on 2011-07-04
> **Lesley Lutomski said:**
> Just to say I've been running my new machine with 64-bit Ubuntu for about 5 days now, and everything seems to be working "out of the box" - great!  Thanks again to all who replied.

good that its working but have you noticed any noticeable performance improvement over that period?

---

