---
title: "System Monitor Vs Top"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by piyushverma82 on 2009-09-10
I have a question about free memory , when i open system monitor's resources tab   it shows me 522 mb used but when i use 'top' command it shows 1709504k used.
I am confused..:confused:

---

### Post by doas777 on 2009-09-10
> **piyushverma82 said:**
> I have a question about free memory , when i open system monitor's resources tab   it shows me 522 mb used but when i use 'top' command it shows 1709504k used.
I am confused..:confused:

well, are you runing top with sudo? if not some processes won't be polled.
also do you know if either of those two values is the commit, and the other the phy used?
also one probably counts the disk cache and the other doesn't ( prolly top).
as admin?

---

### Post by LewRockwell on 2009-09-10
> **piyushverma82 said:**
> I have a question about free memory , when i open system monitor's resources tab   it shows me 522 mb used but when i use 'top' command it shows 1709504k used.
I am confused..:confused:

how much ram do you actually have installed?

what is the size of your swap partition(s)?

without those quantities, not only are YOU confused...but your original post did nothing besides confuse OTHERS...

.

---

### Post by earthpigg on 2009-09-10
enter free -m in a terminal.

example using myself:

```
[chris: ~]$ free -m
             total       used       free     shared    buffers     cached
Mem:          _3939_       3745        194          0        237       2953
-/+ buffers/cache:        _553_       3385
Swap:            0          0          0
[chris: ~]$ 

```

the first underlined number is how much ram you have.

the 2nd underlined number is how much is currently being used.

the first 0 after "Swap:" would be how large my swap partition is, if i had one (i dont).

---

### Post by wojox on 2009-09-10
Nevermind beat to it.

---

### Post by misfitpierce on 2009-09-10
The first line shows with buffers and program caches... Caches programs so they start faster but second line +/- buffers/cache shows whats actually being used atm and how much ram you actually have free if needed. Will take from cache etc if necessary and you need the ram... SO mainly only focus on the bottom line of info in free -m

---

### Post by piyushverma82 on 2009-09-10
Thank you all for the replies, now i get it
```
piyush@piyush-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       1629        375          0        294        867
-/+ buffers/cache:        466       1537
Swap:         2055          7       2047
piyush@piyush-laptop:~$ 

```

---

### Post by earthpigg on 2009-09-10
> **piyushverma82 said:**
> Thank you all for the replies, now i get it
```
piyush@piyush-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2004       _***1629***_        375          0        294        867
-/+ buffers/cache:        466       1537
Swap:         2055          7       2047
piyush@piyush-laptop:~$ 

```

ok. the underlined bold italic part is what top is telling you.

and that line really doesn't matter that much... its good that your system is using as much ram as possible as cache - will make things start quicker. 

the free +/- buffers/cache is what you need to really care about about.

worry a little if the free +/- buffers/cache line starts to get low.
worry a lot if free swap starts to get low -- find out what is using all your memory, and deal with it. it will be something in 'top' that you see taking some ridiculous MEM%.

make sense, now?

---

### Post by jondkent on 2009-09-10
There is a write up here ([http://littledaemons.wordpress.com/2008/05/20/ps-and-top-they-lie-to-you/](http://littledaemons.wordpress.com/2008/05/20/ps-and-top-they-lie-to-you/)) about why *top* can sometimes be a little confusing when it comes to memory use, which you may find useful in filling in any blanks.

---

### Post by Sir Jasper on 2009-09-10
Hi,

In the above display may I ask what is the significance of the 7 MB of Swap used?

I have my swap permanently off since when I used to have it on I only ever saw similar small usage of less than 10 MB. I have never yet come close to needing my swap file; even so, is there any advantage _in my particular case_ in turning it off?

My regards

PS I underlined ¨in my particular case¨ because whatever advice I receive may be far from generally advisable and where hibernation is used [I never use it] this would, I think, cause a problem.

---

### Post by earthpigg on 2009-09-10
> I have never yet come close to needing my swap file; even so, is there any advantage in my particular case in turning it off?

nah. the use of that hard drive space for other uses, yes. but that's it.

in my particular case, i chose not to use one because my hard drive is a 60gb ssd.

in order of importance:

1) 60gb isn't very much space. that 2gb i would have used for swap could make a difference down the road.

2) plenty of RAM... dont really need a SWAP with that much.

3) some say SSD's are more prone to failure if frequently written to. they are to new for us to really know for sure. i suspect that this is an ant hill that has been turned into a mountain by companies that do not manufacture SSDs and thus want to keep their products competitive.

if my hard drive was 250gb, i would have made a swap just for the heck of it.



and if anyone cares: i am very happy with my choice to use an SSD in my desktop as the primary hard drive. lightning fast! the fact that it is a 2.5" laptop SSD affects nothing. SATA is SATA. i have it duct taped to my case because i saw no purpose or need to purchase an enclosure (the justification for using an enclosure with a conventional hard drive does not apply). :D


edit: yes, i have a brand new and fairly high-end desktop computer held together partially with *duct tape*. an equivalent computer from apple.com would have been $2800. anyone care to guess how much equivalent parts themselves cost, minus Apple branding?

---

### Post by Sir Jasper on 2009-09-10
Hi earthpigg,

> **earthpigg said:**
> nah. the use of that hard drive space for other uses, yes. but that's it.

Thanks for your most interesting response and your signature. However, I honestly did not precisely understand your answer. Would you kindly clarify; my point is, if I only ever use about 5 MB of swap then is it likely to be better to have my swap on or off?

My regards

PS I am not tight for space and it is of no importance if my 1 GB swap partition is not used.

---

### Post by earthpigg on 2009-09-10
> if I only ever use about 5 MB of swap then is it likely to be better to have my swap on or off?

the best answer i can give is that it is likely to make *_absolutely no difference at all_*. :D

currently, that swap partition is acting as insurance for you.

if the sun and moon and stars align, and you ever use up all your RAM then you will notice your computer running very slowly and your hard drive activity LED going crazy because that hard drive partition is being used as RAM (hard drives go a **_lot_** slower than RAM). this will give you a chance to figure out WTF is using all your actual RAM and deal with it.

if you dont have that swap and it happens, your computer will simply lock up.

so, on the one hand: you state that you will _**never**_ use up all your RAM. ergo, no need for you to have a swap partition to act as 'insurance'.

on the *_other_* hand: if it aint broke, don't fix it.



my old computer has 4gb of RAM and a swap partition from when i first installed Ubuntu. i realized long ago that i didn't need it, but its not hurting anything so it's still there. ill probably get rid of it next fresh install.

this desktop has 4gb of ram and i didn't bother putting a swap partition on it.

my netbook has 1gb of ram but its hard drive space is very limited so it does not have a swap partition even though it probably should. ill probably add one next fresh install.


conclusion: your present swap partition is hurting **nothing** with its presense. getting rid of it wont **help** anything, either.

keep it or lose it. up to you.

i'd keep it in your shoes, but get rid of it on my next fresh install.

in an age where 6gb of RAM and 500gb hard drives are the norm, swap partitions are rapidly becoming a harmless vestige -- but good to have around for users that need them.

---

### Post by Sir Jasper on 2009-09-11
Hi earthpigg,

Thank for the clarification and your further detailed and helpful reply.

I have now turned my swap back on (just as a free insurance policy).

My regards

---

