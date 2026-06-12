---
title: "How much RAM will I have if I install 32-bit instead of 64-bit"
date: 2010-10-14
forum: New to Ubuntu
---

### Post by Abdus on 2010-10-14
Hello

Right now I have 64-bit version of Ubuntu, but there are some applications I often use that refuse to work on 64-bit architecture. Also my system is old and I got some trash around, so my best idea to cope with these 2 problems is install all from scratch. I have 4GB RAM.

How much RAM will I lose after installing the newest Ubuntu/Kubuntu 32-bit version, if any?

I searched for answer a lot. I found numerous threads about it, but all of them contained answers like "it depends", "if", "maybe", or just explanations hard enough for me to get lost fast (I'm a user, I don't know how things work, I need them to work).

If I have to provide you some info about my hardware configuration, I gladly will. Just let me know what you need to give me an exact answer (if this is at all possible). I'll be very grateful. I need every bit of my RAM, I abuse it. :)

Thank you in advance.

---

### Post by jpyper on 2010-10-14
You will lose about 0.5GB or roughly 512MB due to the limitations of 32-bit CPU addressing. There are some computer BIOS that have a dirty 'extended RAM hack' that will allow the operating system to see the full 4GB of RAM, but from what I've read in various places over the years, it's not a very good solution for using on a system for normal use. I have not tested this myself. I have been running 64-bit operating systems for quite some time now. Your mileage may vary. Good luck.

-John

---

### Post by CharlesA on 2010-10-14
If it installs the PAE kernel (which it will do if you have an internet connection), you'll see all yer memory.

---

### Post by cascade9 on 2010-10-14
If your using a PAE kernel, you should have the same amount of avaible RAM under 32bit as under 64bit. That doesnt mean you will see 4GB, some is normally reserved for system use and for onboard stuff like sound, NIC, USB etc.  

On my system I get 3963MB out of 4096MB (4GB), but how much you will 'lose' depends on a lot of factors.

---

### Post by oldsoundguy on 2010-10-14
You won't lose any!

[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

unlike Windows, Linux will work with much more memory!

---

### Post by oldos2er on 2010-10-14
> **Abdus said:**
>  there are some applications I often use that refuse to work on 64-bit architecture. 

One wonders what those applications could be.

---

### Post by Abdus on 2010-10-15
Ha! Thank you gentle(wo)men! Future seems bright. I'll be definitely looking into the PAE thingy. So welcome back 32-bit system. :)


> **oldos2er said:**
> One wonders what those applications could be.

For example: ImageShack Uploader, Griffenfly Universal Slide Rule, various other non-Ubuntu-native apps that refuse to work on my machine, but are reported towork on 32-bit versions. I simply got tired of using poor substitutes only because my system is "wrong" (or because there's no 64-bit version, or because I lack some oddly named file on my system, or because... I want these to work. Period).


Thanks for help.

---

### Post by redbook4574 on 2010-10-15
> **oldos2er said:**
> One wonders what those applications could be.

Lacie 4L is one that does not work without a lot of faffing about.

Avast antivirus (checking files before passing to widows machines, my company insists on anti-virus software).

Thats just 2 off the top of my head.

---

### Post by coffeecat on 2010-10-15
w32codecs. There's a *really* obscure MS video codec (can't remember which) that's in w32codecs but not in the w64codecs package.

---

### Post by oldos2er on 2010-10-15
Imageshack-uploader works fine here, can you describe the problems you're having with it?

---

### Post by Abdus on 2010-10-16
> **oldos2er said:**
> Imageshack-uploader works fine here, can you describe the problems you're having with it?

Sure: it just fails to start. I tried to instal some kind of additional application that somehow allows 32-bit apps run on 64-bit machine, but it didn't help - IS Uploader still needs some more files (libraries?) that I don't have.

This is a perfect example of what I'm tired with on 64-bit system - constant searching for solutions, then fixing solutions and failing sa the result. :D

---

### Post by oldos2er on 2010-10-17
How did you install it?

---

### Post by Abdus on 2010-10-19
> **oldos2er said:**
> How did you install it?

I don't remember. Also this is really... just irrelevant. :) Fixing an application, or two, is not my goal here. They are like hydra heads - you fix two, four appear. This is what I want to escape from. I want it the easy way. Or at least as easy as it gets. From all I see 32-bit system will be easier to maintain for a user-level-user like me.

However I truly appreciate your will to help. Thank you. :)

---

