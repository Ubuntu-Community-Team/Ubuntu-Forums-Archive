---
title: "Preparing for Jaunty..."
date: 2009-04-14
forum: New to Ubuntu
---

### Post by Whisp3r on 2009-04-14
I'm gearing up for the big day in a couple weeks. I figured Jaunty will be a good stretch of my ever growing skills. Does anyone have a HOWTO or reference for ripping out 8.10 (I've only had it a couple weeks, so not worried about data loss), without destroying my GRUB install? I'm dual booted to XP, and afraid if I just cut out 8.10, it'll muck up GRUB. I would just upgrade, but I would like to take advantage of ext4. Thanks!

---

### Post by Lazy-buntu on 2009-04-14
I installed Jaunty 64-bit over my 8.10 32-bit install (freshly formatted ext4) just a few days ago. You should be able to boot into the live CD, format your 8.10 install, and install 9.04 in its place. By reinstalling that, you can reinstall grub and you shouldn't see a difference.

---

### Post by Whisp3r on 2009-04-14
So just grab the iso on a CD, and install it right into the current 8.10 partition after reformatting? I'll give 'er a shot. Thanks! :)

---

### Post by Lazy-buntu on 2009-04-14
When you get to the part about resizing/modifying partitions: look for your ext3 partition, right click it, do edit, then format as ext4 (with "/" as your mount point without the quotes). Your swap partition shouldn't need to be formatted. Then, continue your install as usual.

---

### Post by Whisp3r on 2009-04-14
Awesome. Thank you! :)

---

### Post by Lazy-buntu on 2009-04-14
If you're really eager, install the beta. I took the plunge, and I couldn't be happier. What's amazing is I tried 64-bit for the first time on top of a beta, and I have had zero problems.

I'm really impressed by the boot time and the log-in screen. Even the notification window has been jazzed up a bit.

Make sure you update after the installation if that's what you plan on doing. There's a couple hundred megabytes of updates.

Good luck! :guitar:

---

### Post by raymondh on 2009-04-14
Whisp ... I, too, am gearing for the official release.  Since I "wanted to re-visit my installation, gparted and tweaking skills (or lack of it)", here's what I did.... (from 8.10)

1. Backed up / moved my files to an external HD.
2. Wiped out 8.10
3. Expanded XP
4. Defragged
5. Did a fresh install of beta 9.04 but this time with a separate home partition and in ext4
6. Moved files back in

When Jaunty if officially released, I may choose to either upgrade thru the network of just do a re-install again.  If I do, it'll be on just the / portion.

Again, this was the long route.  I had a lot of time to spare and it was fun re-learning :) In fact, I am now preparing for UNR 9.04 which will be on top/over Jaunty.

I'm quite sure you can use the installer (manual) to write over the 8.10 install and choose ext4 as the format.  Make sure you choose the right partition though, and BACK UP.

I'm sure the WIKI will show the way.

Enjoy.

---

### Post by alphacrucis2 on 2009-04-14
I wouldn't recommend ext4 unless you are just wanting to play. The jury is still out on how well ext4 recovers from crash/power loss situations. Mind you it does make a significant speed improvement for disk operations.

---

### Post by sirjoebob on 2009-04-14
I will definitely be moving to ext4. I don't keep much important data on my laptop that isn't backed up elsewhere so file integrity risks are worth it for that pure, raw, unadulterated SPEED!!!

---

### Post by nwadams on 2009-04-14
> **alphacrucis2 said:**
> I wouldn't recommend ext4 unless you are just wanting to play. The jury is still out on how well ext4 recovers from crash/power loss situations. Mind you it does make a significant speed improvement for disk operations.

I guess we'll just have to run some stress tests on the above ;)
where's karmic pre-alpha when we need it. ):P:lolflag:

---

### Post by GoingDown on 2009-04-15
> **raymondhenson said:**
> 
When Jaunty if officially released, I may choose to either upgrade thru the network of just do a re-install again.  If I do, it'll be on just the / portion.

Just for the curiosity, why you would do reinstall when going from 9.04 beta to 9.04 final? sudo aptitude update && sudo aptitude dist-upgrade should be enough. 

I am currently running Ubuntu 9.04beta which I upgraded from 8.10 which I upgraded from 8.04, no problems. So why all the hassle of reinstalling?

---

### Post by barney385 on 2009-04-15
> **GoingDown said:**
> Just for the curiosity, why you would do reinstall when going from 9.04 beta to 9.04 final? sudo aptitude update && sudo aptitude dist-upgrade should be enough. 

I am currently running Ubuntu 9.04beta which I upgraded from 8.10 which I upgraded from 8.04, no problems. So why all the hassle of reinstalling?

Yeah. I was wondering that too...

---

### Post by kansasnoob on 2009-04-15
If you already have Intrepid just wait and upgrade!

It's good!

And there are easy "work-arounds" for things you don't like.

---

### Post by raymondh on 2009-04-15
> **GoingDown said:**
> Just for the curiosity, why you would do reinstall when going from 9.04 beta to 9.04 final?

LOL.

If I'm lazy, it'll be a network upgrade.  If I'm bored, I may re-install over my / partition because it's my first time to separate / and /home. I wanna see what happens when I do re-install on / :) 

Really, it's for personal experience.  That way, when I do use the forum, I could really say "been there, done that...no problem" :)

---

