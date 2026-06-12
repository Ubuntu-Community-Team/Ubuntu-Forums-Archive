---
title: "How to RAID0 or mirror 2 1T data drives"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by vdhant on 2008-12-23
Hi guys 
I am brand new to ubuntu (and linux full stop) and am having a bit of a problem with my RAID.

I think i have just realised that my motherboards raid is not true raid and is a fake raid (very disappointing), but life moves on. 

Now I have 3 drives in total 1 36gb and 2 1T hdd. Ubuntu is installed on the 36gb drive and will have nothing to do with the mirror. The 2 1T drives are the 2 data drives that i want to mirror (1 being the master and 1 being the slave that mirrors the master). 

In the end i don't really mind if i use "fakeRAID" or software that mirrors from 1 drive to the other (meaning that they remain as 2 independent drives). But i just need some help with which direction i should go and what software I should use.

Cheers
Anthony

---

### Post by nhasian on 2008-12-23
i think you'll want to use software raid instead of fakeraid:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by vdhant on 2008-12-23
Thanks for the reply. I did have a look at this, but it seemed to be more focused on installing ubuntu on a raid rather than the raid just occurring on 2 separate data drives. Also didn't seem to cover RAID0 much, it seemed to mainly talk about 1 and 5.
Cheers
Anthony

---

### Post by albinootje on 2008-12-23
> **vdhant said:**
>  Now I have 3 drives in total 1 36gb and 2 1T hdd. Ubuntu is installed on the 36gb drive and will have nothing to do with the mirror. The 2 1T drives are the 2 data drives that i want to mirror (1 being the master and 1 being the slave that mirrors the master). 


Hmmm. This is a bit unclear to me.

What do you mean with Ubuntu "will have nothing to do with the mirror".
Do you mean that you don't want Ubuntu to use Linux's software-RAID on it ?

You also talk about RAID0 *and* mirror 2 1T data drives.
I assume that you mean RAID1 (mirror) instead of RAID0 ?

---

### Post by mrbiggbrain on 2008-12-23
> **albinootje said:**
> Hmmm. This is a bit unclear to me.

What do you mean with Ubuntu "will have nothing to do with the mirror".
Do you mean that you don't want Ubuntu to use Linux's software-RAID on it ?

You also talk about RAID0 *and* mirror 2 1T data drives.
I assume that you mean RAID1 (mirror) instead of RAID0 ?

i was about to say the same, RAID 0 has no fault tolerance, its purely performance... your looking for RAID 1, RAID 5 

but since your only useing 2 disks in the raid id assume raid 1 would be ur pick. and please remember that though some applications can get increased read speeds, some can not, and the slight decrease in write speeds can not be avoided, also when useing software raid, the processor has to handle all the functions a raid controler would.

im not firmilure with how linux handles raid controlers, but it might be worth picking up one, they usualy arnt that much for a good hardware raid controler.

---

### Post by Kellemora on 2008-12-23
Hi VDH

I know you don't want to hear this, but RAID is an accident looking for a place to happen.

If you want to mirror your working data drive to a backup storage drive, which is what I do, prefer mirror over a backup any day of the week.  Your best bet is to just use a program like rsync.
We run rsync at 10AM, Noon, 3PM, 6PM and 2AM.  Then at 3AM the backup mirror is copied to an off-site location.

RAID requires a raid controller to function.
On hardware RAID especially, if that controller fails, you've lost everything, because the likelihood of finding a new perfectly identical controller (unless you bought a backup while they were available) would be like finding a hens tooth AND a needle in a stack of straw, a zillion times harder than finding a needle in a haystack, hi hi........

On board RAID, fakeraid, is just as bad.  If your motherboard goes, there goes all your data with it!

Whereas if you just mirror one drive to the other, you can pull them and plop then into any computer and they would be readable!

RAID is touted as making your data safe!  When in reality, that statement is so far from the truth it's pitiful!

The only good purpose for RAID is FAST ACCESS to files, as on a File Server, but then the RAID should be fully backed up as well.

Also, RAID will be obsolete in about another year!

TTUL
Gary

---

### Post by speed32219 on 2008-12-23
Huh?

---

### Post by vdhant on 2008-12-23
Thanks for the reply Gary.
And yes i did mean RAID1, that was a typo, sorry for any confusion.

Quick question first, when you say "RAID will be obsolete in about another year" what is it being replaced with?

Also when you say "Whereas if you just mirror one drive to the other, you can pull them and plop then into any computer and they would be readable!", this is exactly what i want. How do you achieve this? Are you saying you do with by using "program like rsync" or is there another method that you where talking about in this context?

Lastly really really fast access isn't my goal here, my main objective is redundancy, hence why i want a mirror - or at least the same sort of effect that a RAID mirror gives (whether it&#8217;s through syncing or not doesn't really bother me all that much).

Cheers
Anthony

---

### Post by albinootje on 2008-12-23
> **vdhant said:**
>  Also when you say "Whereas if you just mirror one drive to the other, you can pull them and plop then into any computer and they would be readable!", this is exactly what i want. How do you achieve this? 
If one of the two (or more) disks would die while using software-RAID1, then you would still have your data.

Some time ago I read that someone had a hot- swappable software RAID-1 setup of at least 2 disks, where he could simply take out 1 disk to take home as a backup. Pretty funky :)

---

### Post by Kellemora on 2008-12-24
Hi VDH

RAID has a size limitation associated with it.
The workaround is RAID DR or DH or something like that.

Before I moved UP to Ubuntu and was running all Doze machines, we had what was supposed to be one of the better RAID 5 systems with Hot Swap and the whole bit.  It was very expensive also, like in the 6 to 8 grand range.  Priced at 8 grand, I got it for just over 6 grand is actually how that worked out.

And although we did backup up the RAID array to a Tape drive, we still ended up losing EVERYTHING including the backups.

So, needless to say, that left a very bitter taste in my mouth for RAID ever since.

But the key here is I learned something, a MAJOR FLAW in RAID itself.

RAID drives need a RAID controller!
I'll come back to this in a second.

If you have hard drives laying around, you can add them into virtually any computer and you will be able to read them, because the controllers are built into the hard drives themselves.  If you have redundant backups and a HD fails, you haven't necessarily lost your data.  Even if the controller fails you can find places who can recover your data.

Such is not the case with RAID systems.  They require the EXACT Controller in order to read the stripes across the disks.
Even with RAID 1, where one drive is mirrored to the other, RAID is using a Controller, be it hardware or software and in effect bypassing the on-board controller of the hard drive.  It still uses it, but in a different way.

In my case, the company that sold the RAID System with their name on it imported it from somewhere.  And since they used the same make an model number on different version, even they didn't know WHICH RAID Controller was on the different makes and models they sold.  You can read that as I was SOL as far as recovering any data.  We lost over 7,000 hi res images that could not be replaced as the originals were no longer available.

No problem, we had a backup!  Unfortunately, the backup set was defaulted to Restore to the original location, meaning the RAID System UNDER the Specific Controller the backup was made from.
We spent a couple of thousand dollars trying to recover our data and even the Very Best Forensics experts were unable to do so.

All was not lost though, I still had 5 very nice hard drives that were in perfect shape, just needed reformatted is all.

Back when using Windows, I had lost data previous to buying the RAID 5 System, due to a BUG in Retrospects Mirroring Program.

I prefer Mirror over Backup because you have a DUPLICATE of your original Drive C in Winders.  Not some incremental Backup Set that takes months to untangle.

But instead of Mirroring all of our Data, a Bug in an early Retrospect program decided to only place LINKS as a mirror back to the original HD, so when that HD failed and we checked the Mirror, it was nothing but LINKS back to the failed hard drive.
Of course we didn't know this, even though we had checked the mirror many times.  Because the Links worked, as long as the original HD was working, we saw the files we expected to see.

So NOW, we pull the plug (LAN) and physically check the mirrored drive to make sure it functioning properly.

If you have a Windows machine you can run Retrospect to back up all of your hard drives regardless of what is on them or what format they are in.

But since switching to Ubuntu, we use rsync to FETCH the files from the other computers and store on the mirror drives (file server).  Due to previous problems we NEVER PUT a file anywhere.
Meaning we Don't PUT a File from Computer A onto Computer B or onto the file server.  We only FETCH files for storage.  If we need a file from Computer A on Computer B, we go to Computer B and FETCH the file from Computer A.  This insures that all the file properties remain intact.  No LOCKS on the files requiring Manual release of each file.

The file server FETCHES files several times a day and then at night an off-site storage server for backup purposes, FETCHES the files from the file server.

rsync runs 1000 times faster than the Retrospect program for Winders!  Gives error logs of files it couldn't copy, which happens rarely.  But when it does, at least I KNOW about it.

There is also a DRAWBACK to mirroring files.  And then mirroring the backup to another backup.  So it's good to also have an UNTOUCHED file storage system where you manually copy a file for storage from a known good original.

Files can sometimes become corrupt, yet still work just fine or seem to.  An image may lose it's lower half but still checksum out OK.  You go to retrieve a file and find some corruption in it, so you go to the mirror to find the corrupt file was mirrored in it's corrupt state to the backup.  The backup was mirrored off-site to another backup and that one is corrupt to, because when a file changes, it mirrors those changes.  Files that don't change don't get moved after the first time.

Also, with RAID, you normally have both drives in the same computer or box.  So, if a power supply goes bad and fries your computer or box, you've lost both drives or all 5 if you're that heavy on drives.

Even if I have several drives in a single computer, such as the file server, each drive is on a separate card in the machine.  Or actually, two HD's to a card, but not used for the same purpose if on the same card.  Referring to IDE or SATA PCI cards here, not Controller cards.

You're best bet is to mirror to a drive on another computer, PLUS mirror those drives to an external, then mirror the external to someplace off-site over a LAN if you are close enough.  But redundancy depends upon how volatile your data is too.  If I lose product formula's and the like, I'll be out of business instantly.  Things like packaging labels can be redone, but that takes time.  Some of our labels came about from years of tweaking the designs as we saw the need.  When I look back at some of our earliest designs, I just shake my head and say I would be embarrassed to send such garbage out these days.

I also do desktop publishing of very complex pamphlets, like those travel brochures hawking all the tourist traps.  So needless to say, I have literally tons of client data and images that must all be kept sorted and readily available.

Sorry, I tend to ramble in my old age, hi hi........

You can do some on-line searches on RAID to find out it really is reaching the point of obsolescence.  Some claim within a year at the rate storage demands are going up.

Have a Merry Christmas!

TTUL
Gary

---

### Post by b0b138 on 2008-12-24
Check here. [http://ubuntuforums.org/showthread.php?t=1012493](http://ubuntuforums.org/showthread.php?t=1012493)

---

