---
title: "Slower system in Ubuntu with many apps?"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by Castor68 on 2009-03-21
[FONT="Verdana"]I'm very happy about Ubuntu.  A friend of mine told me two years ago about it.... but, you know... I was an absolute MS user with zero knowledge about others OS. My big frustration was the freezing of the system when I ran many programs. I found Ubuntu very stable about this. So, I'm here, learning to use it.

I have an old Compaq S5100NX with a 2.6 GHz Celeron, hard disk of 120 GB  and 1024 GB in RAM. Ubuntu 8.10 runs very fast currently. Basically, my question is: if I download a lot of Ubuntu applications, e.g., for movies, MP3 players, etc., etc..... will it become slower?.  In XP, the most things I downloaded to my hard disk, slower, slower and slower in the start up, opening the programs and shutting down the system.
[/FONT]

---

### Post by ivanvajar on 2009-03-21
Don't worry about slowdowns with Ubuntu :-)

Intel Celeron 2,4GHz, 1GB RAM Maxtor 80GB, WD 160GB

---

### Post by binbash on 2009-03-21
No but apt-get may be a little slower

---

### Post by Castor68 on 2009-03-21
Thank you ivanvajar. I'm very new in all these things, but I'm doing my best to learn. Also, I got to improve my english because isn't my first language.

Is there a way to boost my system?. I mean, through Ubuntu, because the PC is old and it got the maximum of his capacities, specially no more space for RAM. Also, is the 130 GB barrier in HD the same problem in Ubuntu?. In Windows is a BIOS matter and I think is the same in Ubuntu.

---

### Post by egalvan on 2009-03-21
> **Castor68 said:**
> , but I'm doing my best to learn.
 ,I got to improve my english because isn't my first language.

Is there a way to boost my system?. , through Ubuntu, PC is old and it got the maximum of his capacities, specially no more space for RAM.

Ways to improve your machine..

check for an up-dated BIOS on the HP/Compaq website...

machine specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047837&lc=en&dlc=en&cc=us&product=363427](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00047837&lc=en&dlc=en&cc=us&product=363427)

mobo specs:
[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=363427&docname=bph07845](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&product=363427&docname=bph07845)

note: the 845 chipset should support 2GB RAM (2x1GB sticks)

Up-grade the CPU from a Celeron to a full Pentium 4 (Northwood core preferable).
The motherboard you have sets the limits.
And the speed gains may not be worth the price... to you.
($40 got me a P-4, 2.8GHz with 1Meg cache, with 800Mhz bus.
this replaced the Celeron 2.6GHz with 128Meg cache and 400Mhz bus.
Yes, the speed gained was noticeable, and worth the $40... for me.
I needed a BIOS update for this to work.)

A faster hard drive (boot drive) will also give some performance gains... 
jumping from an old 4200RPM to a newer 7200RPM is noticeable when booting or starting software.
Of course, a 10kRPM Raptor :) will really make a difference, but that's pricey...

>  Also, [B]is the 130 GB barrier in HD the same problem in Ubuntu?. 
In Windows is a BIOS matter and I think is the same in Ubuntu.[/B]

In Linux, it is still a problem, but easier to solve than in MS-Windows.

Check out this link, it talks of your exact situation...
(and remember, if you add a second (or more) hard drive for non-initial-boot only, Linux won't care how big it is, it will "just work"
no extra work needed in this case.)


[http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition](http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition)

---

### Post by Castor68 on 2009-03-21
**egalvan**: thank you.

You forgot to tell me how to improve my english hahahahaha....

So. When I had the MS XP in my Compaq, I checked out their web site to get a BIOS update but nothing. I just found a update for something related to the BIOS language ???? ... Also, the mobo has a maximum of 1GB, not more than that.

I'm thinking about the processor upgrading. For now, no budget for it. Crisis.. you know. Maybe in a few weeks. 

Right now, I have many apps open in Ubuntu. Listening a CD, chating, here in the forum, downloading a GNOME file and no problems. Days ago, all these things were impossible. Freezed for sure.

---

### Post by Castor68 on 2009-03-21
You mean .... Can I add a second 350 or 500 GB hard drive (as slave) and no problems?

---

### Post by Kevbert on 2009-03-21
Once Jaunty is released (in April), try that, as one of the improvements is boot speed.  The other thing you might like to try is Xubuntu, as that is faster for PCs with limited resources.  One thing that will drastically slow down the system is compiz (desktop effects - the rotating cube).

---

### Post by hypocratus on 2009-03-21
You shouldn't have any problems adding a second large hard drive. I just added a 300 GB IDE hard drive two weeks ago to a 933 Mhz system that someone gave to me to get rid of it. Outside of a malfunctioning IDE cable, which I replaced it works great. The only time you have to worry about that 130 GB limit is for the partition that is booting.

---

### Post by egalvan on 2009-03-23
> **Castor68 said:**
> **egalvan**: thank you.
You are more than welcome.

> 
You forgot to tell me how to improve my english hahahahaha....

Well, it's understandable, so it's pretty good as is..

> When I had the MS XP in my Compaq, I checked out BIOS update but nothing.
 I just found a update for something related to the BIOS language ???? ...

yeah, i couldn't find a BIOS update either... you may be stuck with what you got...

>  Also, the mobo has a maximum of 1GB, not more than that.

The mobo manufacture (ASUS) show a 2GB limit on that board..
Intel show a 2GB limit on that chip set...
HP/Compaq **recommend** 1GB max...
It's highly likely that 2GB will work,
but the only way to tell is to try...

> I'm thinking about the processor upgrading. For now, no budget for it.
 Crisis.. you know. Maybe in a few weeks. 


Yep, money does not grow on trees...

> Right now, I have many apps open in Ubuntu.
 Listening a CD, chating, here in the forum, downloading a GNOME file and no problems.

This indicates a stable system, and that you have enough RAM
(CAN one ever have enough RAM???)

>  Days ago, all these things were impossible.** Freezed for sure**.

Well, it's good that the weather warmed up enough to allow the electrons to flow faster and smoother... :)

ErnestG

---

### Post by billgoldberg on 2009-03-23
> **Castor68 said:**
> [FONT="Verdana"]I'm very happy about Ubuntu.  A friend of mine told me two years ago about it.... but, you know... I was an absolute MS user with zero knowledge about others OS. My big frustration was the freezing of the system when I ran many programs. I found Ubuntu very stable about this. So, I'm here, learning to use it.

I have an old Compaq S5100NX with a 2.6 GHz Celeron, hard disk of 120 GB  and 1024 GB in RAM. Ubuntu 8.10 runs very fast currently. Basically, my question is: if I download a lot of Ubuntu applications, e.g., for movies, MP3 players, etc., etc..... will it become slower?.  In XP, the most things I downloaded to my hard disk, slower, slower and slower in the start up, opening the programs and shutting down the system.
[/FONT]

No, unless you run them all at the same time :p

---

