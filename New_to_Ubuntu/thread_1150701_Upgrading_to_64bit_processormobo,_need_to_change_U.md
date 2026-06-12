---
title: "Upgrading to 64bit processor/mobo, need to change Ubuntu also?"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by shaggy_mutt on 2009-05-06
Hi there!

I seem to recall Ubuntu coming in regular and 64 bit versions. My computer is currently running an Athlon 2000+ but I wouldn't mind being able to run Ubuntu faster, and it looks like even Phenom2's are down to a few hundred dollars.

My questions:
1. Am I right to assume that this would make day-to-day tasks quicker on the computer? (opening programs, etc) ... as opposed to this being a performance increase that I wouldn't see unless I'm doing something like games or math-intensive software?

2. Apart from the hardware aspects of upgrading, how do I handle the change from regular to 64bit in Ubuntu? I'm currently running Intrepid and will be upgrading to Jaunty shortly, but I'm holding off until I know whether I need to do something special during the upgrade process. How do I go from 32bit Ubuntu to 64bit?

3. Can anyone recommend a good AM3 compatible motherboard that is NOT made in mainland China? Taiwan, Singapore, etc. are OK.

Thanks in advance!

---

### Post by Kareeser on 2009-05-06
3. ASUS

2. There's currently no way to upgrade straight from 32-bit to 64-bit. You'll have to download the 64-bit ISO and cleanly install onto the hard drive.

---

### Post by halitech on 2009-05-06
I recently changed from an old P4 1.8 to an AM2 5200+ and really noticed a speed increase in opening programs. Its more noticeable when doing CPU intensive work but even on every day things its faster.

You don't *need* to do anything, 32bit version will run on 64bit hardware but may not take full advantage of all the speed. You will need to do a complete reinstall of Ubuntu to upgrade.

Cant speak on the AM3 boards specifically but I bought the Sapphire 690v board (AMD made) that will handle the AM2+ and Phenom chips (from what I can remember of what the sales rep told me)

---

### Post by arapa on 2009-05-06
There are certain application that will benefit from 64 bit but you may not notice any performance improvements. 

A big reason for running 64 bit is so you can use more than 4 Gigs of RAM. The 32 bit architecture is limited to less than 4.

There is a advantages/disadvantages of 64 bit sticky here...

[http://ubuntuforums.org/showthread.php?t=765428]("http://ubuntuforums.org/showthread.php?t=765428")

---

### Post by shaggy_mutt on 2009-05-06
Oh neato!

So all ASUS is still made in Taiwan? Great news if that's the case.

And if there wouldn't be a noticeable improvement in speed with 64bit (I mainly just web surf, write emails, etc) then I'll probably stick with 32bit for now.

Thanks, guys! Great forum.

---

### Post by joey-elijah on 2009-05-06
> **shaggy_mutt said:**
> Oh neato!

So all ASUS is still made in Taiwan? Great news if that's the case.

And if there wouldn't be a noticeable improvement in speed with 64bit (I mainly just web surf, write emails, etc) then I'll probably stick with 32bit for now.

Thanks, guys! Great forum.

For the basics like websurfing and e-mails and less than 3GB RAM then you won't notice a massive difference with a 64bit OS than a 32bit OS. You will notice a MAHOOOSIVE improvment  going from a solo core to a dual/tri/quad core phenom though - Especially if you do any encoding/converting or mean multi-tasking. 

If you have 4GB RAM and a Video Card with memory then you would be better off using 64bit Ubuntu - tbh there's very little reason not to for most people - it's FUD that keeps them clinging to legacy OSes.

---

### Post by powel212 on 2009-05-06
As stated above you **do not need to** change from 32 to 64Bit when you change your chip. And yes to make the change you will have to make a fresh install with a 64Bit version of the OS.

I have an asus,(P5K), board and I love it. 
Gigabyte boards are also made in Taiwan and they are rock solid.

I run an intel chip and it is lightning fast and super reliable. 

I run 64Bit Ubuntu and when I switched I noticed a speed improvement in all aspects of computing. Yes it is worth it.

I would recommend taking a hard look at real world processor performance though. Compare what you have to what you want. As well check what you want against other manufacturer's chips. CPU's are historically cheap now and you will likely be satisfied with whatever you buy but I personally see little difference in chips priced at $250 and those priced at $500-700

Also check this forum link:
[http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)

Pay particular attention to the speeds of AMD chips. I will reserve my own opinion but the above linked forum pretty much speaks clearly of the best performance to value products out there.

Good luck and have fun.

---

### Post by NightwishFan on 2009-05-06
I upgraded to 64-bit when I read a description of the 32-bit mode in 64-bit AMD CPUs. They referred to it as "legacy mode".


I updated right away.

As for the new hardware, I think Ubuntu will sort it out. If you **want** 64-bit, then you will need to reinstall.

---

### Post by Keithhed on 2009-05-06
I agree with Joey, you will notice a massive difference going from a single to dual or quad core with a higher clock speed.  I was using 64 bit Jaunty for a couple weeks, but I couldn't fix the buggyness that I experienced. (Most users probably don't experience too much trouble, but I couldn't shake them).

So, I installed the 32 bit Jaunty and everything has been dandy :) 

As far as general use and "feel" of using the OS. I can't tell any difference in 32 and 64 bit on day to day use.  I don't use any apps that are optimized for 64 bit.  :( 

And unlocking the last .8GB of memory is not signifigant for me as I can't seem to push it past 1GB (even with multiple apps running)

Now, don't take this as 64 bit bashing.  I would be using 64 bit right now if I didn't experience so much trouble.  And i'm sure I'll be back to 64 at some point :)

I hope I helped you in your decision :)  Sorry for the rambling

---

### Post by NightwishFan on 2009-05-06
> **Keithhed said:**
> I agree with Joey, you will notice a massive difference going from a single to dual or quad core with a higher clock speed.  I was using 64 bit Jaunty for a couple weeks, but I couldn't fix the buggyness that I experienced. (Most users probably don't experience too much trouble, but I couldn't shake them).

So, I installed the 32 bit Jaunty and everything has been dandy :) 

As far as general use and "feel" of using the OS. I can't tell any difference in 32 and 64 bit on day to day use.  I don't use any apps that are optimized for 64 bit.  :( 

And unlocking the last .8GB of memory is not signifigant for me as I can't seem to push it past 1GB (even with multiple apps running)

Now, don't take this as 64 bit bashing.  I would be using 64 bit right now if I didn't experience so much trouble.  And i'm sure I'll be back to 64 at some point :)

I hope I helped you in your decision :)  Sorry for the rambling

No problem. Perhaps you might be able to fix your issues as well, there is a whole section in this forum for 64-bit users.

As for RAM usage. You want as much ram as you can get.

64-bit allows more ram to be allocated for any process. Combined with something, such as preload, you will max out the performance of your system to the point where practically every action will be instantaneous.

64-bit also allows for faster processing of CPU intensive processes, it is like adding a few more lanes to a highway to lessen traffic.

There is also security features built into 64-bit, at least on AMD processors as far as I know.

Overall, you gain a benefit from its use, even with a lesser system. As I posted before, who wants to use a legacy system.

---

### Post by oldos2er on 2009-05-06
If you're buying 64-bit hardware, why not use 64-bit software to take full advantage of it?

---

### Post by shaggy_mutt on 2009-05-06
Don't get me wrong; I'll probably upgrade to 64bit eventually. My concern (I'm sorry if I was unclear about this) was whether installing 64bit hardware would cause 32bit Ubuntu not to work at all in the meantime. From reading the replies, this sounds like something that I don't have to worry about. So thanks!

I'll be shopping for an asus or Gigabyte mobo and once everything's all buttoned down, I'll probably make the leap to 64bit at some point when I have some free time and nothing to do.

Thanks again for treating my noob question with TLC! I really appreciate the expertise that you've all shared.

---

### Post by cwmoser on 2009-05-06
I have an AMD 64 X2 6000+ cpu based PC.  I was running 32-bit Ubuntu 8.04 and recently upgraded to 64-bit Ubuntu 9.04.  I noticed a significant increase in speed and responsiveness.  

This new Ubuntu 9.04 64 bit OS really rocks -- I can't stop praising how good it is.  Go with 64-bit.

Carl

---

