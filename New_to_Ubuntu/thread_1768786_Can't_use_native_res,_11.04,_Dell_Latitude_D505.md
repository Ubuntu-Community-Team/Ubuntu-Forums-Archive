---
title: "Can't use native res, 11.04, Dell Latitude D505"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by Markeh21 on 2011-05-27
Well, I'm a beginner. Hi.

Anyway, back onto the reason I posted.

I've got a Dell Latitude D505 laptop, with these specs:
Pentium M 725 @ 1.6GHz
Intel 855 integrated graphics
512MB RAM
40GB HDD
DVD-ROM/CD-RW
Intel 2200 802.11b/g
15" LCD - native res of 1400x1050

Now, I've just had this laptop today, was given to me by a friend who didn't want it. So I thought about putting Ubuntu on in place of the rather bloated XP installation on it already.

So I burnt myself a 11.04 disk (my other 10.04 LTS disk was that badly scuffed from overuse it stopped working), and proceeded to install. Installation went without a hitch, but the screen is at 1024x768. It's a bit annoying as I know it's capable of a higher res.

I did do all the updates that were available as of today, and one of them was something to do with the Intel 855GM chipset (it also mentioned xorg - graphics drivers perhaps?), but alas, I can still only select 1024*768.

This is the only thing I've never been able to sort in Ubuntu (I had a similar problem trying to get an ATI X600 Pro to display 1280x1024, but never fixed it before it expired and released its magic smoke), so it's a bit of an annoyance but I'm hoping its something simple.

Any suggestions?

---

### Post by lykwydchykyn on 2011-05-27
Are you sure it can go that high?  Does Windows let you go that high?

I had a D505 for about 3-4 years, I don't remember being able to get above 1024x768 on either OS, though I could be mistaken.  It certainly didn't get up to 1400X1050.

---

### Post by Markeh21 on 2011-05-27
I'm fairly sure that the 15" models can reach that resolution.
Having said that, I'm not sure now.

I'm 99% sure the resolution was 1400x1050 when it was on XP, but I can't check obviously.

OK. I fail. It's an XGA screen. I was under the impression that only the 14" models were XGA (that'll teach me for believing the marketing rubbish Dell put out).

---

### Post by lykwydchykyn on 2011-05-27
After some searching, it seems you may be right.  I must have been at 1280x1024, but it seems some have gotten 1400x1050.

Back in the day, we'd install 915resolution from the repos and it would allow higher res.  Sadly it's no longer in the repos, and hasn't been since a few versions back.

You might be able to install it from here:
[http://915resolution.mango-lang.org/](http://915resolution.mango-lang.org/)

Though I can't say what it would do with natty's Xorg and intel drivers.  You'll have to try and see.

EDIT: ok, hold on; it seems that 915resolution was folded into the driver.  So it'd be redundant to install it on Natty.

Check the "usage" part on that page, and there may be some things you can add to an xorg.conf file to enable those modes.

---

### Post by travlemon on 2011-07-26
I am strangely having the complete opposite problem.  I have a Latitude D505, and Ubuntu ONLY lets me have the 1400x1050 resolution.  When trying to switch to other resolutions, none are displayed except for 1400x1050.

I booted to a live cd of Mandriva, and it seems to show all of the resolutions available, and defaults to 1024x768.  I assume this is just a driver issue.

Does anyone know how to fix that? I'm not quite sure how to get a better driver for an Intel graphics card, as I usually try to make sure my Linux machines have Nvidia.  The smaller resolution would be nice, as things run a bit choppy at such a high resolution on a not-so-powerful video card.

---

### Post by RevNomad on 2011-09-13
My Dell has stopped showing any resolutions other than 1024*768. Ubuntu was running slow so I installed Xbuntu. Might this have screwed things up?

---

