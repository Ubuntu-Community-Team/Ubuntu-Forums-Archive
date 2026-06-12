---
title: "&quot;Hard Disk failure is imminent!&quot;  oh dear, help! :("
date: 2010-07-16
forum: New to Ubuntu
---

### Post by Rave Gloves on 2010-07-16
Could this be an os problem or is my hard disk going to die?.

I thought my disk was dodgy but i couldn't find the check disk option that there was on the older versions. 
Help :(

---

### Post by the.phantom on 2010-07-16
my guess


be looking for a new hard drive NOW ! and get what you need off of it now !!!!

i had the S.M.A.R.T system give me that error and 5 mimn later hard drive died

---

### Post by ubunterooster on 2010-07-16
use clonezilla to copy all of the data to a larger (or equal sized) drive

[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by Rubi1200 on 2010-07-16
I suggest you get hold of a LiveCD and quickly save anything important.

---

### Post by Rave Gloves on 2010-07-16
I only got this laptop back 2 days ago from being fixed D:
Luckily i did a clean install when i got it so there is nothing important on this.
I was thinking about buying a solid state drive, Anyone got one and can suggest a good one?

250 gig is fine, im not really looking for 1tb hard drives or anything. i will never need all that.

---

### Post by ubunterooster on 2010-07-16
Mine is one of the best I could get: [http://www.amazon.com/Patriot-Torqx-Solid-State-PFZ256GS25SSDR/dp/B002AL7CLC/ref=sr_1_3?ie=UTF8&s=electronics&qid=1279330427&sr=8-3](http://www.amazon.com/Patriot-Torqx-Solid-State-PFZ256GS25SSDR/dp/B002AL7CLC/ref=sr_1_3?ie=UTF8&s=electronics&qid=1279330427&sr=8-3)

---

### Post by Rave Gloves on 2010-07-16
> **ubunterooster said:**
> Mine is one of the best I could get: [http://www.amazon.com/Patriot-Torqx-Solid-State-PFZ256GS25SSDR/dp/B002AL7CLC/ref=sr_1_3?ie=UTF8&s=electronics&qid=1279330427&sr=8-3](http://www.amazon.com/Patriot-Torqx-Solid-State-PFZ256GS25SSDR/dp/B002AL7CLC/ref=sr_1_3?ie=UTF8&s=electronics&qid=1279330427&sr=8-3)

Didn't think they were that expensive, think i'll go for a normal hard drive, what's better about SSD's, ive heard they have a limit to how much you can write over them?

---

### Post by ubunterooster on 2010-07-16
Speed, pure raw speed, especially in reads, writes are far better than a normal HDD but nothing compared to the reads

---

### Post by SoFl W on 2010-07-16
> **Rave Gloves said:**
> 250 gig is fine, im not really looking for 1tb hard drives or anything. i will never need all that.

yeah... I remember when I thought...
a 160K floppy was a lot of space
a 5 meg hard drive was a lot of space
a 60 meg hard drive was a lot of space
a 250 meg hard drive was a lot of space
a 9 gig hard drive was a lot of space
....

---

### Post by linuxman94 on 2010-07-16
> **SoFl W said:**
> yeah... I remember when I thought...
a 160K floppy was a lot of space
a 5 meg hard drive was a lot of space
a 60 meg hard drive was a lot of space
a 250 meg hard drive was a lot of space
a 9 gig hard drive was a lot of space
....

:lolflag:

---

### Post by Rave Gloves on 2010-07-16
> **SoFl W said:**
> yeah... I remember when I thought...
a 160K floppy was a lot of space
a 5 meg hard drive was a lot of space
a 60 meg hard drive was a lot of space
a 250 meg hard drive was a lot of space
a 9 gig hard drive was a lot of space
....

well i suppose tb hard drives are pretty cheap now :P might as well go overkill....

---

### Post by Ranko Kohime on 2010-07-16
> **Rave Gloves said:**
> well i suppose tb hard drives are pretty cheap now :P might as well go overkill....
Overkill?  I've already filled 2 of the damn things.  I bought a pair, one for backups, and the other to use as my online storage disk.

I recently had to start deleting stuff off the online disk because it FILLED UP.  :D

The backup drive is nearly full as well.

1080p and FLAC are the enemies of gigabytes.  :lolflag:

---

### Post by heatblazer on 2012-09-22
I had that message too but not in Fedora or any other distros. I`ve tested the HDD for over a month and nothing happened. Strange... Still consider:
dd if=/dev/sd(x) | gzip -c > the_dying_drive.img
gunzip -c | dd of=/dev/sd(x)
But I am not 100% sure Ubuntu is right about that hdd failures.

---

