---
title: "Startup Fix Yet??"
date: 2010-07-22
forum: New to Ubuntu
---

### Post by jazz53 on 2010-07-22
Is there a fix or update for 10.04 live cd?
Mine will not work on my new comp, and I am tired of trying the workarounds.
Workarounds are no help when trying to use a live cd as a problem solving tool.
a bullet proof startup is required.
Hopefully there is one, as I have found previous versions of Ubuntu helpful in the past.

TIA

---

### Post by tarps87 on 2010-07-22
What is the problem you are experiencing? We need more details

---

### Post by jazz53 on 2010-07-22
The same old problem many people are having.
Startup hangs, something to do with video drivers.
I have tried the "nomodeset" with no success
I have an ati 5700 series card
8gb ram, i7 processor, 2tb of hd, p55 mo bd
Some people have problems with intel video as well

---

### Post by jazz53 on 2010-07-22
I have read on the bugs page there is a ver of 10.4lts with the fix.
But I do not know where to get it. there was no link provided.

---

### Post by tarps87 on 2010-07-22
Have you tried using the fail safe mode and VESA graphics modes, I do not believe safe mode uses the VESA drivers so it will need to be selected additionally.

The issue is the live cd tries to use the graphic drivers for you card/motherboard instead of the fail safe as it is a live environment, if you are looking to install you could use the command line version, this has never failed me. On the other hand if you are looking for a problem solving tool I would suggest using a distro such as Puppy Linux, it is designed as a live cd or usb with an optional install added on not like Ubuntu which is a install cd with a 'trial' environment added on.

---

### Post by tarps87 on 2010-07-22
> **jazz53 said:**
> I have read on the bugs page there is a ver of 10.4lts with the fix.
But I do not know where to get it. there was no link provided.

Can you post a link to the bug please

---

### Post by jazz53 on 2010-07-22
OK tried puppy linux!

Same problem
I am beginning to think my new computer with an ATI 5770 video card does not like linux.
Going to try 9.10.
Frustrating as ,,,, U know!

---

### Post by jazz53 on 2010-07-22
Guess what,,,,Tried 9.10 and it works fine from the live cd!
No messing around, no workarounds , nothing.
It just works period.
I guess it is 10.04 and not my comp.
This is probably chasing away a lot of users. If I had not previously seen how valuable ubuntu can be, I would have thought "This is not ready for prime-time, sticking with Windows"
Some body please fix this.

---

### Post by QIII on 2010-07-23
No.  It is not Lucid, per se.  I'm using it to write this right now -- with an AMD/ATI card.

My Maverick testing machine also works fine.

It might very well be that with certain AMD/ATI cards there are issues.

I have several machines with AMD/ATI cards that work just fine.

There are some nVidia cards that have been problematic.

Remember that if it is a driver issue it is not Ubuntu at all.  OEMs write drivers, not OS developers.

That certainly does not invalidate your difficulty, since you are having difficulty.  I would just use Karmic for the time being since it works for you.  You might want to get a launchpad account if you don't have one and do a search to see if there are issues with your specific graphics card.  Also take a look for any issues affecting other hardware you may have.

I wouldn't rush to blame either Ubuntu or the card/driver combination.  This could be something that both parties are aware of and are addressing.

Edit:  Just found several complaints about that card not working in Karmic.  There are a lot of variable here.

---

