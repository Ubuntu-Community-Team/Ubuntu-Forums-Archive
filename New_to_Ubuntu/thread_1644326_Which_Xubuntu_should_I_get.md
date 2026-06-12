---
title: "Which Xubuntu should I get?"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by GaaraOfDSand on 2010-12-13
Hi all,

I've been using xubuntu for a few years now, but I always used the 32-bit version for my pentium 4. 

I am going to buy a new computer very soon (Hopefully this week it will be ready) and it has an i7 860 processor.. I've done some research and I've learned that it is a 64-bit processor, I went to the Xubuntu download page and it only has AMD64 or the x86 versions (which as far as I know is the 32-bit)..

The question is; Which one should I download so that I get the maximum performance out of the new PC?

Thanks and seasons greetings..

---

### Post by cascade9 on 2010-12-13
AMD64. Yes, it works fine on intel 64bit CPUs. 

Though no doubt there will be the usual 'dont use 64bit, it has problems' (not in my experience) and 'flash sucks on 64bit' (not if you use the 64bit flash version it doesnt) posts. 

BTW, for maximum perfromance try doing a minimal install then add Xfce4. It does make a difference. ;)

---

### Post by GaaraOfDSand on 2010-12-13
wow thanks for the very quick reply..

Well normally I install xubuntu cause it's lighter than ubuntu as for the programs it uses (IMO) but as a desktop environment I always use Fluxbox! In the previous post by 'performance' I meant full RAM recognition and stuff because someone told me that if I use the 32-bit version only 3.xgb ram would be recognized and I figured since I'm paying for 4gb ram, I might as well use them. =b

So I'll get the amd64 thanks.. And yes I am somehow worried because I have heard that 64bit isn't as good as 32bit, but if I really can't get the hang out of it, I'll just revert back to the 32bit sacrificing approx 800mb of ram, 3.2gb DDR3 isn't bad at all.

---

### Post by migs73 on 2010-12-13
My only advice on the matter would be to check there are no issues with drivers for your peripherals etc in 64bit. That is the only thing that keeps me in 32 bit (drivers for my Brother printer a bit rubbish when forced for 64bit).

BTW if you do a fresh install of 32 bit, it will see you have >3gb of RAM and automatically install the PAE kernel which will allow usage of all your 4gb RAM (it will see about 3.8gb after system overheads, but 64bit would see the same).

---

### Post by cascade9 on 2010-12-13
> **GaaraOfDSand said:**
> Well normally I install xubuntu cause it's lighter than ubuntu as for the programs it uses (IMO) but as a desktop environment I always use Fluxbox! In the previous post by 'performance' I meant full RAM recognition and stuff because someone told me that if I use the 32-bit version only 3.xgb ram would be recognized and I figured since I'm paying for 4gb ram, I might as well use them. =b

Last I checked, xubuntu wasnt really that might 'lighter' than ubuntu. There was some work being done on that so things might have changed. 

> **migs73 said:**
> BTW if you do a fresh install of 32 bit, it will see you have >3gb of RAM and automatically install the PAE kernel which will allow usage of all your 4gb RAM (it will see about 3.8gb after system overheads, but 64bit would see the same).

Yes, PAE will let you use 4GB (well, 3.somethign after system reserved RAM anyway).

---

### Post by GaaraOfDSand on 2010-12-13
Oh, so the ram isn't even an issue?

What about the cpu then? Will it affect it if I use 32-bit instead of 64? To be honest, I'd rather use 32bit than 64.. 

Does ubuntu have the Hyper Thread (HT) ability? If yes, which version?

Sorry for asking all these questions, but since you guys are so helpful, I thought I would. =b Good I'm so proud of this community, joined like 2 years ago, and still impressed!

I love you guys. :D

---

### Post by cascade9 on 2010-12-13
> **GaaraOfDSand said:**
> What about the cpu then? Will it affect it if I use 32-bit instead of 64? To be honest, I'd rather use 32bit than 64.. 

Does ubuntu have the Hyper Thread (HT) ability? If yes, which version?

It wont really affect the CPU to run 32bit, though apart from dodgy perpherials (like migs73 has) or uncommon programs that only have 32bit versions I'd much rather run 64bit. It helps a lot with heavy processing. For me, thats things audio ripping, video ripping, transcodes. 

Why would you rather use 32bit? 

Ubuntu will use hyperthreading (32bit and 64bit AFAIK)........not that you'll notice much difference if it didnt work or was turned of in the BIOS.

---

### Post by migs73 on 2010-12-13
> **cascade9 said:**
> It wont really affect the CPU to run 32bit, though apart from dodgy perpherials (like migs73 has) 

:lol: My peripherals aren't dodgy........only the drivers!!

Yes, CPU intensive operations will benefit from 64bit.

Mike

BTW although all your RAM will be recognised and be usable by the system with PAE, your processes will only be able to address 3.whatever GB at a time as they themselves are 32bit.

---

### Post by GaaraOfDSand on 2010-12-13
In the past I've read that 64-bit had problems with flash (I'm sure there's a RIGHT way of installing it) 

And since I'm asking all these questions I am a n00b, but if all of you are saying 64bit is better, than I'll try it and see how it goes.. And like I said before, if worse comes to worst, I'll just go back to 32bit!

So AMD64 it is! Thank you all.

Happy Holidays! :)

---

### Post by cascade9 on 2010-12-13
LOL...I just posted this on a different thread, so I'll just put it here as well. 

The 64bit version of flash- 

[http://labs.adobe.com/technologies/f...ayer10/square/]("http://labs.adobe.com/technologies/flashplayer10/square/")

If you dont want to manually install, try the 'flash aid' plugin. (written by "lovinglinux" who is a member here) 

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)

> **migs73 said:**
> :lol: My peripherals aren't dodgy........only the drivers!!

Opps, sorry :)

---

### Post by GaaraOfDSand on 2010-12-13
> **cascade9 said:**
> 
If you dont want to manually install, try the 'flash aid' plugin. (written by "lovinglinux" who is a member here) 

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)


If no flash is installed like let's say a fresh install, will that still work and install flash on it's own?

---

### Post by cascade9 on 2010-12-13
As far as I know, yes, flash-aid will find and install the right version for your system. 

I cant be 100% sure because I always install flash manually on 64-bit systems.

---

### Post by ibizatunes on 2010-12-13
pentiums 4 are 32bit only, it wouldnt allow you to install x64 bit!

---

### Post by migs73 on 2010-12-13
> **ibizatunes said:**
> pentiums 4 are 32bit only, it wouldnt allow you to install x64 bit!

the i7 860 he states he is going to buy will run 64bit though!!!!

> I am going to buy a new computer very soon (Hopefully this week it will be ready) and it has an i7 860 processor.. I've done some research and I've learned that it is a 64-bit processor

---

### Post by cascade9 on 2010-12-13
@ ibizatunes- you missed where GaaraOfDSand said they were going to buy a new computer? 

> **GaaraOfDSand said:**
> I've been using xubuntu for a few years now, but I always used the 32-bit version for my pentium 4. 

I am going to buy a new computer very soon (Hopefully this week it will be ready) and it has an i7 860 processor.. .

Also, some Pentium 4s are 64bit capable.

---

### Post by GaaraOfDSand on 2010-12-13
> **cascade9 said:**
> As far as I know, yes, flash-aid will find and install the right version for your system. 

I cant be 100% sure because I always install flash manually on 64-bit systems.

I'll install Flash-Aid and see what happens with no flash installed. If it won't do anything, I'll do it manually and see if there's any updates. =)

You've all been very helpful.

---

### Post by cascade9 on 2010-12-14
No problem. 

Good luck with your new system ;)

---

### Post by GaaraOfDSand on 2010-12-14
> **cascade9 said:**
> 

Good luck with your new system ;)

Thanks, tomorrow or the day after, the pc should be ready built. :D

I'll mark this thread as Solved. :popcorn:

---

### Post by GaaraOfDSand on 2010-12-17
> **cascade9 said:**
> LOL...I just posted this on a different thread, so I'll just put it here as well. 

The 64bit version of flash- 

[http://labs.adobe.com/technologies/f...ayer10/square/]("http://labs.adobe.com/technologies/flashplayer10/square/")

If you dont want to manually install, try the 'flash aid' plugin. (written by "lovinglinux" who is a member here) 

[http://flash-aid-extension.blogspot.com/](http://flash-aid-extension.blogspot.com/)



Opps, sorry :)

I tried what you suggested (flash-aid) with no previous flash install, it worked wonders, even when I'm on youtube the cpu usage is not 100% like it was on my 32-bit P4 2.66GHz. All of the 8 cores run less than 20% and some of them even at 0% while watching a clip, so thanks for this add-on I didn't know about it.

I thought I'd let you guys know how everything worked out since you were all so helpful and so far 64-bit worked flawlessly. 

Thanks again. :)

---

### Post by migs73 on 2010-12-17
Glad it all worked out for you.

8 cores.....I can watch youtube vids with only 60-70% CPU usage on my single core 32bit AMD Sempron (1.8GHz).

I can only dream of 8 cores!!!

---

### Post by Paddy Landau on 2010-12-17
> **cascade9 said:**
> Last I checked, xubuntu wasnt really that might 'lighter' than ubuntu.
Correct. There is a new version, which is aiming to get official recognition from Canonical soon. I use it on an ancient computer and it makes a big difference. [Lubuntu]("http://lubuntu.net/").

---

### Post by GaaraOfDSand on 2010-12-17
> **migs73 said:**
> Glad it all worked out for you.

8 cores.....I can watch youtube vids with only 60-70% CPU usage on my single core 32bit AMD Sempron (1.8GHz).

I can only dream of 8 cores!!!

You are right, but flash games like bejeweled on facebook, that worked really slow and 100% cpu usage

> **Paddy Landau said:**
> Correct. There is a new version, which is aiming to get official recognition from Canonical soon. I use it on an ancient computer and it makes a big difference. [Lubuntu]("http://lubuntu.net/").

I did use LXDE before it's a good wm and I really hope it does get recognized..

---

### Post by cascade9 on 2010-12-18
Glad it worked for you GaaraOfDSand. ;) 

> **migs73 said:**
> Glad it all worked out for you.

8 cores.....I can watch youtube vids with only 60-70% CPU usage on my single core 32bit AMD Sempron (1.8GHz).

I can only dream of 8 cores!!!

With flash I've found that on multicore systems, it wont just load one core, but will 'bounce' from core to core. 

> **Paddy Landau said:**
> Correct. There is a new version, which is aiming to get official recognition from Canonical soon. I use it on an ancient computer and it makes a big difference. [Lubuntu]("http://lubuntu.net/").

IMO they would do a lot better to make Xfce less bloaty rather than going to Lxde. With debian, Lxde is far closer in resources used to Xfce than with xubuntu/lubuntu.I admit my bias, Lxde leaves me cold.

---

### Post by Paddy Landau on 2010-12-18
> **cascade9 said:**
> I admit my bias, Lxde leaves me cold.
OK, but I'd rather have a computer boot in less than a minute and work reasonably well than feel like toffee (which, in turn, was significantly better than the Windows that came with the machine).

---

### Post by cascade9 on 2010-12-18
> **Paddy Landau said:**
> OK, but I'd rather have a computer boot in less than a minute and work reasonably well than feel like toffee (which, in turn, was significantly better than the Windows that came with the machine).

The biggest junker I have boots in less than a minute with sidux Xfce, a P3-866/256MB/i810 video /20GB setup....Though to be honest, I havent booted it in a while, I've been using a p4 that I really need to get over to my mum LOL.  

Yes, sidux doesnt exist anymore, I just dont update the machines I use without a net connection for media playing.

---

