---
title: "special device /dev/scd0 does not exist"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by spuddyfodno on 2009-11-29
Hi after my winXP loaded laptop decided to that circular boot thing that XP loves so much and also after bumping into the infamous 34 minute re-install hang. I used the ubuntu live CD to recover most of the stuff on the hard disk. Great I thought this is easy, I'll try a hard disk install.

Oops, it just doesn't want to know about the CD/DVD drive on the laptop, which is odd cos it was working fine from the CD boot. 

Yeah well i knew it was too good to be true, so what's the trick then do I have to slaughter a chicken at midnight under full moon or is this this just never going to work?

here's the error I get:

-Unable to mount cdrom0

mount: special device/dev/scd0 does not exist.-

As you might have guessed I'm new to the Linux/Unix thing so I haven't got bloody clue what's going on. Anyway if anyone's got any useful crumbs they can throw my way I'd very grateful






Thanks Spud.


*UPDATE*

No replies I see, well if anyone's interested, I tried a SUSE install today and It seem to work seamlessly although  I do get a mount notice. So I reckon there's one of two things wrong:

The drive needs to be mounted manually and I just don't see it because of my general Linux ignorance 

or

The hard disk install fails to copy the necessary hardware support, which probably means a descriptor file of some sort.


I have searched around and this does seem to be a common problem with dual function drives even amongst seasoned Linux users so I'm guessing it's the later.

---

