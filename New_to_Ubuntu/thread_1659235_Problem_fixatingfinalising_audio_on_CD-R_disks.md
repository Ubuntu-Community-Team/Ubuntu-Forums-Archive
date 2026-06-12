---
title: "Problem fixating/finalising audio on CD-R disks"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by Swaphead on 2011-01-03
Hi guys,

I have a LITE-ON ATAPI DVD A DH20A4P DVD/CD burner.
I am using the LUBUNTU 10.10 distro.

I can burn ISOs and data files to DVDs, DVD-RWs, CD-Rs, and 
CDR-RWs, no problem.

I can also copy music CDs to CD-RW discs and audio CD-RW discs.
(I'm not sure what the difference is - just that the "audio" discs also work in CD recorder machines) All play fine in my hi-fi.

The problem comes if I try to copy a music CD to a CD-R.

I have tried GnomeBaker, Xfburn and also Pburn in Puppy Linux. 
I get exactly the same results:
There are no reported errors with the burn and
I can play the disc on the computer, and as far as the burn software is concerned, the disk has been finalised,
(it won't let me add tracks) BUT if I put it in a hi-fi CD player it shows as "not finalised". 

I think all of the above burners are using WODIM.

Are there any simple solutions, or am I condemned to using CD-RW
discs which are 2 or 3 times more expensive?

btw I'm loathe to try Brasero because I used it with UBUNTU 8.10
and all it gave me was a stack of coasters.

---

### Post by spearfish on 2011-01-03
I think your ISOs work because they have a TOC (Table of Contents) in the Lead-In area on the disk.  When a CD is finalized, the TOC is written to the Lead-In area on the CD.  An ISO would have this because the location of the files are already known.

A fresh CD has nothing in the lead-in area.  When you burn some music on a CD and then pop the CD into your car stereo, the CD player tries to find the TOC in the lead-in area.   For whatever reason there is nothing there on the disk.  It may just be the program you are using.

I found this article interesting:

[http://www.cdrfaq.org/faq02.html#S2-19](http://www.cdrfaq.org/faq02.html#S2-19)

Sorry it doesn't solve your problem, but it was useful to learn what is going on.

I wonder if the problem is something simple, like going into the "advanced" settings on your burner-program and checking the "finalize CD" box?  Try searching for some settings.  The option may just be hidden in a menu somewhere.

---

### Post by Swaphead on 2011-01-04
Thanks, Spearfish.

I've bookmarked the CDRFAQ page - it's a mine of information.

When I do the burns I show the message file. In all cases
(writing audio AND data discs) there is a message about fixating
taking place and no errors are reported.

I cannot find any finalize option for Xfburn with CDs or with DVDs.
Gnomebaker gives a choice for DVDs but not for CDs.
Pburn in Puppy IIRC has options for just about everything!

I have a Philips CD player and an ancient single-speed CDR recorder - neither can play the CD-Rs I burn on the PC, but are fine with the audio CD-RWs I burn on the PC and of course any commercially-produced music on CD and anything burned on the CD-recorder (same batch and make of discs as used on the PC).

I've just tried one of the "failed" CD-Rs in my DVD player(very cheap but newish) and - would you believe it? - it plays!!
The DVD player will NOT play unfinalised CD-RWs ( have tested this) -
So it looks as though fixation did occur after all.  :confused:

There are too many variables here for a non-techie like myself
to ponder: I will stick to VERBATIM CD-RWs and leave well enough alone until such times as my hi-fi gear gives up the ghost.

Cheers
Geoff

---

