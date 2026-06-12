---
title: "Removing Ubuntu and Installing XP. Help?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by victorcrane on 2009-02-24
Hey folks, worry not, I'm not abandoning ubuntu, I like it very much... however. 

I've just given my old laptop to my wife after using it with ubuntu for the last six or eight months. She has no clue how ubuntu works and since she uses xp at work she'd like it on the laptop but my good god no matter what I try I can't get it to install. All I get is a blue screen error telling me a problem has been detected and windows has closed to prevent damage to the system. Then it has a lot of numbers presumably relevant to someone in the know...

I was told the problem will be the hard disc and the way that ubuntu configures it, so I formatted the entire thing with killdisk and started again, set my partitions etc... same blue screen.

I was then advised the problem lies in the mbr of the disk and until that was reset I'd never get windows to run on it so I ran fdisk/mbr in the hope that this may help. Nope, still that damn blue screen. 

Lastly in desperation I dug out my old xp system recovery cds and for the first 45 minutes things looked perfect... until.... BLUE SCREEN! Hooray! 

A lot of guys seem to be suggesting and I quote 'If you ran ubuntu and you want to use windows, remove the hard disk and throw it in the bin, buy a new one and start again'. I'm starting to think they may be right. 

Any ideas? 

:shock:

---

### Post by furialis on 2009-02-24
You could try using the LiveCD to run gparted and wipe the entire disk. I've also heard about the dd command - although that doesn't seem noob friendly.

---

### Post by taurus on 2009-02-24
What's the spec of your old laptop?  The easiest way is to boot your laptop with Ubuntu LiveCD.  Then, use gparted (System -> Administration -> Partition Editor) and delete all the partitions on your harddrive.  You probably have to unmount the swap partition (click on it with the right button and pick swapoff) first before you can delete it.  Now, create a new partition that takes up the whole disk space and format it to ntfs.  Reboot and replace Ubuntu LiveCD with your bootable windows cd and proceed from there.

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> Hey folks, worry not, I'm not abandoning ubuntu, I like it very much... however. 

 my good god no matter what I try I can't get it to install. All I get is a blue screen error telling me a problem has been detected and windows has closed to prevent damage to the system. Then it has a lot of numbers presumably relevant to someone in the know...



[B]A lot of guys seem to be suggesting and I quote 'If you ran ubuntu and you want to use windows, remove the hard disk and throw it in the bin, buy a new one and start again'. I'm starting to think they may be right. 
[/B]
Any ideas? 
:shock:

Total, absolute, unfounded, paranoid FUD.

**F**ear **U**ncertainty **D**oubt


I have been installing, un-intalling and wiping drives since approximattly 1980, and I have NEVER had a disk that was "ruined" by an Operating System.

The closest this came was the "Byte of Death" that certain MS system software would set that would cause a drive to seem "dead".
A low-level wipe fixed it, no problem.


If you **TRULY** want to wipe a drive, download and use dban,
aka Darik's Boot and Nuke.

dban.org

this will wipe the drive. 

If the drive is un-usuable after this, it is NOT the operating system at fault.
It is HARDWARE.

---

### Post by TpyKv on 2009-02-24
I've had similar problems before and had to do a low level format to completely wipe the drive...

Find out who the hard drive manufacturer is - this can be identfied by the first few digits of it's serial number... which you can see in BIOS...

Mine is a Seagate drive, so I need the "seagate tools for dos" application... which is another live CD.... give this a try if you have no luck with Gparted Live ...

[http://downloads.sourceforge.net/gparted/gparted-live-0.4.1-2.iso?use_mirror=dfn](http://downloads.sourceforge.net/gparted/gparted-live-0.4.1-2.iso?use_mirror=dfn)

 - burn this ISO to a CD and give it a try, just delete everthing so your hard drive is one big unpartitioned space!

---

### Post by Therion on 2009-02-24
> **victorcrane said:**
> A lot of guys seem to be suggesting and I quote 'If you ran ubuntu and you want to use windows, remove the hard disk and throw it in the bin, buy a new one and start again'. I'm starting to think they may be right. 
Oh please.  That's one of the more ignorant things I've heard in a long time.  

Hard drives are magnetic platters.  

They hold magnetic charges.  

That's ALL they do.  Oh, and they spin!  Almost forgot that part.

One OS or another, or another, or another altogether...  It makes no difference.  You really need to find yourself a better avenue for your technical support.

But all that aside, try using Darik's Boot and Nuke to wipe the drive.  [http://www.dban.org/download](http://www.dban.org/download)

If nothing works, then yes, your drive may be failing.  It's failing however, was no more precipitated by installing Ubuntu than it was by running Windows on it.

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> 
'If you ran ubuntu and you want to use windows, remove the hard disk and throw it in the bin, buy a new one and start again'. I'm starting to think they may be right. 
Any ideas? 

I forgot to mention the hundreds of thousand of DUAL BOOT machines out there happily running Linux AND MS-DOS/Windows.


As Therion said, get a better class of "tech support" :)

---

### Post by theozzlives on 2009-02-24
My laptop came with Vista, got rid of that piece of ****! Put Ubuntu on, then a year later decided to dual boot XP. Only problem I had was XP and a SATA drive. If you have SATA change it to ATA and that'll fix your problem.

---

### Post by victorcrane on 2009-02-24
> **Therion said:**
> Oh please.  That's one of the more ignorant things I've heard in a long time.  

Hard drives are magnetic platters.  

They hold magnetic charges.  

That's ALL they do.  Oh, and they spin!  Almost forgot that part.

One OS or another, or another, or another altogether...  It makes no difference.  You really need to find yourself a better avenue for your technical support.



I apologise sincerely for my ignorance of this matter causing you so much offense. I'm perfectly aware of how a hard drive operates, but that doesn't mean I know every last detail, and I've always found it better to ask a question than to bumble randomly through these situations. Snobbery and arrogance are not terribly endearing qualities. 

If you have nothing constructive to offer then perhaps you may hold your peace rather than trawling the pages of a help forum intended for novices, trying to make yourself feel superior. How terribly clever you are.

---

### Post by rustutzman on 2009-02-24
Make sure your BIOS isn't set for virus protection. That pretty much locks the mbr from change.

Russ

---

### Post by victorcrane on 2009-02-24
Dban - I gave it a shot, just got the following...

Dban finished with non-fatal errors. 
This is usually caused by disks with bad sectors. 

Should I give up yet? ;)

---

### Post by Therion on 2009-02-24
> **victorcrane said:**
> I apologise sincerely for my ignorance of this matter causing you so much offense. I'm perfectly aware of how a hard drive operates, but that doesn't mean I know every last detail, and I've always found it better to ask a question than to bumble randomly through these situations. Snobbery and arrogance are not terribly endearing qualities. 

If you have nothing constructive to offer then perhaps you may hold your peace rather than trawling the pages of a help forum intended for novices, trying to make yourself feel superior. How terribly clever you are.
Chill, friend.  That clearly wasn't directed at you, but rather at your "tech support" people.  Further, the comments were neither snobbish nor arrogant.  What you were being told was, and is, ignorant.  Sorry, but that's simply what it is.  Again, the comments were not being directed at you, quite clearly, but at those who were spouting such nonsense.

Check my post history.  Yeah, I'm so totally into feeling superior around here.

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> I apologise sincerely for my ignorance of this matter causing you so much offense. I'm perfectly aware of how a hard drive operates, but that doesn't mean I know every last detail, and I've always found it better to ask a question than to bumble randomly through these situations. Snobbery and arrogance are not terribly endearing qualities. 

If you have nothing constructive to offer then perhaps you may hold your peace rather than trawling the pages of a help forum intended for novices, trying to make yourself feel superior. How terribly clever you are.


None of here were "offended" by YOUR "ignorance".
ALL of us were "ignorant" of Linux and other computer stuff at one time or another.
Some of  us tried hard to learn.
Then pass that learning to others.
Freely.

We ARE amused by the level of ignorance in supposed "experts" that hand out "advice" such as that was given to you re: Ubuntu install ruining a hard drive.

As for "nothing constructive"...
let's see,
several posts suggested a live cd to erase that drive,
one mentioned 'dd'
two mentioned dban (my preferred 'erase' software, as it will wipe ANY drive connected in ANY fashiion.)

So yes, you got good, varied advice.
We also 'laughed' at the "tech-support" you had received.

At this point, you can try the cost-free advice we gave,
or toss the drive and buy another.

ErnestG

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> Dban - I gave it a shot, just got the following...

Dban finished with non-fatal errors. 
This is usually caused by disks with bad sectors. 

Should I give up yet? ;)


On the hard drive, yes.

It's got enough errors that it is now un-reliable.
dban is very good at this.

Pull the magnets out of it and have some fun.
Use the platters as optical/mechanical flats, have more fun.

Obtain another drive to install XP.

But this was NOT caused by installing another Operating System.

---

### Post by victorcrane on 2009-02-24
> **Therion said:**
> Chill, friend.  That clearly wasn't directed at you, but rather at your "tech support" people.  Further, the comments were neither snobbish nor arrogant.  What you were being was, and is, ignorant.  Sorry, but that's simply what it is.  Again, the comments were not being directed at you, quite clearly, but at those who were spouting such nonsense.

Check my post history.  Yeah, I'm so totally into feeling superior around here.

Fair do's, having read back my post I appear a bit of a prick, sorry about that, I've just spent the entire day becoming more and more frustrated with this and so many people have treated me like an idiot today I perhaps misread your intentions. 

I hate when things don't work.

---

### Post by victorcrane on 2009-02-24
> **egalvan said:**
> On the hard drive, yes.

It's got enough errors that it is now un-reliable.
dban is very good at this.

Pull the magnets out of it and have some fun.
Use the platters as optical/mechanical flats, have more fun.

Obtain another drive to install XP.

But this was NOT caused by installing another Operating System.

Ah... tits. Oh well at least now I know, many thanks to all who have suggested anything, I did try each and every one. It seems xp must be more fussy than ubuntu as I've just thrown the cd in to reinstall it out of my own curiosity and it's going along just fine. 

;)

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> It seems xp must be more fussy than ubuntu as I've just thrown the cd in to reinstall it out of my own curiosity and it's going along just fine. 
;)

My experience is the exact opposite...

MS-Windows has always been much more lax about hard errors than Linux.

Try TpyKv's advice and obtain the diagnostics from the drive manufactorer.
You may, and I emphasis MAY, be able to re-map the bad sectors.

But be aware that it may die totally, without warning.

You have to weigh what your time and trouble are worth,
versus what a replacement drive will cost.

As for me, I would only use it as a "play" drive...
One to play around with, maybe try different Linux's... :)



And I hope you read ALL the warnings about dban...
it WILL wipe any drive attached to your machine.
it does give warnings, and a small measure of "are you sure?",
but all-in-all, a very powerful 'wipe' program.
Do NOT play with it on a machine that has anything valuable.

---

### Post by victorcrane on 2009-02-24
> **egalvan said:**
> My experience is the exact opposite...

MS-Windows has always been much more lax about hard errors than Linux.

Try TpyKv's advice and obtain the diagnostics from the drive manufactorer.
You may, and I emphasis MAY, be able to re-map the bad sectors.

But be aware that it may die totally, without warning.

You have to weigh what your time and trouble are worth,
versus what a replacement drive will cost.

As for me, I would only use it as a "play" drive...
One to play around with, maybe try different Linux's... :)



And I hope you read ALL the warnings about dban...
it WILL wipe any drive attached to your machine.
it does give warnings, and a small measure of "are you sure?",
but all-in-all, a very powerful 'wipe' program.
Do NOT play with it on a machine that has anything valuable.


Yeah the dban warnings were pretty clear to say the least, it seemed similar to the killdisk utility i tried earlier in the day. Not to worry, I really don't think I can justify spending any more time on it, it already ate a whole six hours of today and I'll never get them back, to think of the fun I could have been having with my tesla coil... Maybe I can convince the good woman to become a convert... hmmm...

I guess I may indeed turn it into some kind of ornament, there are people selling them stripped down to bare bones on ebay for just this purpose which made me laugh, guess you really can sell anything to pretty much anyone. ;)

---

### Post by egalvan on 2009-02-24
> **victorcrane said:**
> to think of the fun I could have been having with my tesla coil..

Yes, they are fun... :)

I guess I may indeed turn it into some kind of ornament, there are people selling them stripped down to bare bones on ebay for just this purpose which made me laugh, guess you really can sell anything to pretty much anyone. ;)[/QUOTE]

Well, the magnets in hard drives are very powerful. Lots of fun.
Many small screws.
One, two, or more platters that can be optical/mechanical flats.

A motor capable of 7,200 RPM.

A magnetic actuator capable of millisecond-long movement.

so yeah, dead hard drives can be a source of "stuff"

---

### Post by MasterNetra on 2009-02-24
I personally have easily reinstalled XP after Ubuntu (for various reasons, nothing that is Ubuntu's Fault) and it went cleanly each time. (Even if XP itself didn't stay clean :p) So i would have to agree that its probably a hardware problem. Things break.

---

### Post by Therion on 2009-02-24
> **victorcrane said:**
> ... I've just spent the entire day becoming more and more frustrated with this and so many people have treated me like an idiot today I perhaps misread your intentions. 

I hate when things don't work.
No harm, no foul.  I do call 'em the way I see 'em but I would never belittle another user.  Too, I can relate to your building sense of frustration over something like this.  Been there many times.  If it makes you feel any better (it won't) I've got a perfectly good Western Digital 150GB Raptor SATA hard drive (10K RPM) sitting on a shelf because Linux distros just hate it.  

Sweet, huh?  

Think it didn't take about a full head of hair and a case of good beer to figure THAT one out?  Then there were the tears of frustration and anger as I forced myself to replace it.

*C'est la vie!*  

Cheers!  And good luck with your hard drive issue.

---

