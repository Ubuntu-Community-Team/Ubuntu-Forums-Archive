---
title: "4gigs of ram = &amp;amp;quot;safe graphics mode&amp;amp;quot;"
date: 2009-01-03
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-01-03
So I just recently got a new laptop (w00t w00t) and upon moving my HDD into it (in a manner of speaking, I cloned it over) I can only boot into "safe graphics mode" when ever I have my second 2 gig stick of ram in (meaning 4 gigs) it boots fine with a single stick... I am not sure if it is an an issue with having 4 gigs or an issue with having more than two (several other threads on these boards and online suggest it is the first) is there any way I can get my full four gigs working?... I am running Ubuntu 8.10 32bit.

Please Help,
~Jeff

---

### Post by sydbat on 2009-01-03
What type of system are you moving it from? It could be enough of a hardware change that your cloned system cannot recognize the new hardware?? You might have to do a clean install first, then move your data over.

Also, a 32 bit OS will only detect/use about 3.5 of the 4 GB you have. I would suggest changing to the 64 bit Ubuntu to access all your RAM. (at least try it via the Live CD to make sure your laptop will work fine)

---

### Post by taurus on 2009-01-03
Does the second stick of RAM have the same spec as the first?  Does the BIOS recognize both sticks, 4GB?

---

### Post by beastrace91 on 2009-01-03
I moved from one Asus laptop to another (so I was hoping it wouldn't be to big of an issue) the largest change was that I went from an ATI to an Nvidia and I use envyng to handle that driver change... I am really trying to avoid a full format as I just got everything finally where I like it after 6 formats (give or take) in 2 weeks...

As for a 64bit OS aren't there issues with compiling most apps on that? (As most are designed for the more common 32bit OS)

~Jeff

---

### Post by beastrace91 on 2009-01-03
> **taurus said:**
> Does the second stick of RAM have the same spec as the first?  Does the BIOS recognize both sticks, 4GB?

Same specs. Bios can see both (and so can windows...)

~Jeff

---

### Post by taurus on 2009-01-03
Try to swap the slots of the RAM.  Also, at the GRUB menu, do the memtest.

---

### Post by sydbat on 2009-01-03
It's the "I haven't had any problems" answer. I know some people have had problems getting certain things to work in 64 bit, but I (knock on silicone) have not. It depends on what you want to run, I think, that matters...

---

### Post by beastrace91 on 2009-01-03
> **taurus said:**
> Try to swap the slots of the RAM.  Also, at the GRUB menu, do the memtest.

Like switch the slot each stick is in?... And how do I run a memtest @ grub menu?  (and how do I get to the grub menu?)

~Jeff

---

### Post by taurus on 2009-01-03
Yes, switching the slots.

When you first turn on your computer, do you see the GRUB menu?  You can also run the memtest from the LiveCD if you have one handy.

---

### Post by beastrace91 on 2009-01-03
I will try switching the slots (although it seems kinda redundant) as for grub I see the "loading grub" and then it gives a 2 count, am I suppose to press something at that screen to get the grub menu? And I always have a live CD with me :) (in a manner of speaking, my flash drive is a bootable Ubuntu 8.10 disc) Is it easier to test it using that?

~Jeff

---

### Post by taurus on 2009-01-03
Press the ESC key when you see that word GRUB on the screen.  You have three seconds to do that.

---

### Post by beastrace91 on 2009-01-03
Ok last stupid question on my part... what is the command once I am at the grub console to run the memtest?

~Jeff

---

### Post by beastrace91 on 2009-01-03
Nevermind it is the "displaymem" command I am assuming? Running that shows 4 gigs of ram...

~Jeff

---

### Post by beastrace91 on 2009-01-03
Also swapping the ram slots gets me the "safe graphics mode" still same as before.

~Jeff

---

### Post by beastrace91 on 2009-01-03
Downloading a 64bit live CD now to see if that will let me use my 4gigs... if it works I guess I will reformat again.

~Jeff

---

### Post by beastrace91 on 2009-01-03
64bit operating system looks to be the solution... although it is a shame Ubuntu cannot just clock back the amount of memory used like windows does...

~Jeff

---

### Post by beastrace91 on 2009-01-03
EDIT:

I am now more than a little upset... the 64bit live CD and then once it was a fresh install worked great with the 4 gigs of ram. How ever AFTER updating everything (apt-get update and apt-get upgrade) I am now getting the "safe graphics mode" issue in the 64bit operating system as well! What did the update do that I can undo to cause it to basically revert?... This is really becoming a large headache very quickly :(

~Jeff

---

### Post by beastrace91 on 2009-01-04
Good to know Ubuntu won't boot properly with 2+ gigs of RAM, guess I will have to be formatting back to Xp now.

~Jeff

---

