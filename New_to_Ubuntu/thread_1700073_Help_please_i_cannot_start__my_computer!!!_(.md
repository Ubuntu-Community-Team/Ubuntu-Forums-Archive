---
title: "Help please i cannot start  my computer!!! :("
date: 2011-03-04
forum: New to Ubuntu
---

### Post by kroki on 2011-03-04
I was installing the ubuntu version 9.10 but it got stucked (besides it was already too slow).... so i was stupid and didn't think: i restarted the computer from the pc button.
now i cannot enter it only appears: rom SCSI..Not Found      and other things i can't read  because they are cut by the screen
:confused:pleaase help.. i have really important documents :(((((((((

I don't have the ubuntu cd, 'cause it was already installed :(

---

### Post by davidmohammed on 2011-03-04
Sounds like you've only got a partial installation.

You'll need to get a ubuntu CD to help yourself.


How far through the installation did you get?

When booting, press the shift key - does it display "grub"?  If so, try choosing the recovery mode - what options can you use?

---

### Post by kroki on 2011-03-04
the orange bar was missing a bit to finish, but it said that the installatation was completed. :(
maybe that's why i thought i could restart it

i don't have the recovery mode or anything, before i have the message : rom SCSI..Not Found              boot device (don't relly know if it's a "b" in boot 'cause the screen doesn't let you see),
i have press home hey to boot then it says many other things with R:(

sorry for my ignorance but i'm so new in this, and the things that says are to fast

---

### Post by davidmohammed on 2011-03-04
ok 

power off your PC.

Power it back on.  Press the shift key just after powering it on.  This is called "booting".


In your first post you said you were installing 9.10 - but then you finished the post saying that you dont have a ubuntu CD.  I'm confused - how are you installing ubuntu if you do not have a CD?

---

### Post by kroki on 2011-03-04
thank you for telling me what booting is, i really had no idea;-)

yeah i don't have the cd 'cause in my computer it was already installed ( by a friend but then he took the cd with him)
i was installing it from the ubuntu system, just upgrading the version

i press the shift key, but it doesn't react

before the message: rom SCSI..Not Found

it says:

Novell Netware Ready Firware v1. 00 (940809)
copyright....

-ROM-ADR: 000D 870D 89A2
...

this last message lasts like 6 seconds or so

---

### Post by davidmohammed on 2011-03-04
press and hold the shift key.

the first picture looks worrying - hopefully I'm wrong, but I think it means your hard-drive is either not accessible to be booted from, or has died...

When booting you should see "Press F2" or something similar to enter the bios.

Press the Function key to do this - common Function keys are F2, F8 and F10.

Have a look in the bios at the boot order - is your hard-drive "enabled"?  Some bioses show a disabled hard-drive with an exclamation mark (!) before the hard-drive name.

---

### Post by kroki on 2011-03-04
while trying i pressed shift and hold it (i think), i don't really know what i did now but now it says:

press home key to boot from local drive.

I'm pressing the right key and i think it  is (the one that says "home" on it), but  i still have no answer... :(, :(
can the hard-drive die just because i restarted it when the new version of ubuntu was being installed :confused:

thank you for helping me

---

### Post by ikt on 2011-03-04
> **kroki said:**
> can the hard-drive die just because i restarted it when the new version of ubuntu was being installed :confused:

Hard drives can die at any time and at any moment :)

I hate to say it but the computer sounds realllly old, like old old, a scsi cdrom, ancient! 

Are you able to go into the bios, to see if the hard drive is still being detected?

---

### Post by kroki on 2011-03-04
yeah it's an old computer, but it was working quite well. I was using windows, but then decided to use ubuntu (i forgot my password, so with youtube tutorials i could get a new one) , when i entered it was really slow so then i thought of upgrading to the next version (9.10).. it got stucked (the orange bar) but below it said that it was completed. I restarted it  because it didn't answer, and got the problem.

shall i try to boot again? (i'll  restart it-- now it doesn't move from : "press home key to boot from local drive."):(:confused:

---

### Post by davidmohammed on 2011-03-04
restart it - press the function key requested to get into your bios.  Have a look to see if your hard-drive is recognised.

---

### Post by samigina on 2011-03-04
Boot with the Ubuntu Live CD, and from there, see if Ubuntu recognize your drive. If yes, the problen could be a problem with th partition table of the drive, the the solution is to reformat the disc.

---

### Post by kroki on 2011-03-04
I restart it... the very first thing that appears (are the photos).. then after several minutes this other messages appear: (the first two pictures that i uploaded) 

when i'm in the message of: rom SCSI..Not Found .... if i press "home" key.. it says very fast: 
rom CDROM.. Not found 
rom floppy..

and then something else too fast i can't read (something about network)

after that the :   "press home key to... " screen appears for 2 seconds

when that happens the screen of rom SCSI..Not Found appears

:confused:

---

### Post by kroki on 2011-03-04
can i download ubuntu to get it into a CD, without damaging the software  of the computer i'm going to dowload it from?
:(

---

### Post by davidmohammed on 2011-03-04
You'll need to download ubuntu from another computer - your current computer will obviously not help you.  The download will be an ISO file.  You'll need software such as Nero to burn the ISO to a CD.

Sometimes to get into only bioses you need to press the Del key.  Try that first.

---

### Post by Toafan on 2011-03-04
Of course - provided you can burn from an .ISO file to a CD.
You'll need CD burning software - I can't help you there, but if someone you know owns the computer then they can install it.
To get the copy of the CD, just go to [http://www.ubuntu.com/]("http://www.ubuntu.com/") and download the CD image. just burning it to a CD won't work without the special software, though...
Downloading the ubuntu CD won't affect the computer, you acctually have to *do* something with it.

---

### Post by kroki on 2011-03-04
i'm going to try that.. 
i was pressing the f8 key when this appeared.. what do i select or can i do.. :(

---

### Post by davidmohammed on 2011-03-04
the first device is your floppy - the second is your CDROM and the third is your network.  There is no Hard-drive.

Unless you see an option on that screen to "add" a device such as a hard-drive, it looks very much like your hard-drive is dead.

---

### Post by donut123 on 2011-03-04
> **kroki said:**
> I was installing the ubuntu version 9.10 but it got stucked (besides it was already too slow).... so i was stupid and didn't think: i restarted the computer from the pc button.
now i cannot enter it only appears: rom SCSI..Not Found      and other things i can't read  because they are cut by the screen
:confused:pleaase help.. i have really important documents :(((((((((

I don't have the ubuntu cd, 'cause it was already installed :(
Hello...I dont think 9.10 is good any longer...see if you can download the new version...and install it.

---

### Post by kroki on 2011-03-04
now i pressed the "del" key and got this:

---

### Post by kroki on 2011-03-04
> **kroki said:**
> now i pressed the "del" key and got this: what means?

---

### Post by ikt on 2011-03-04
> **kroki said:**
> what means?

It's the BIOS, it's all your basic computer information, be careful with it :)

If you go into Standard CMOS setup, does it list your hard drive?

just quickly, how are you posting this info?

---

### Post by kroki on 2011-03-04
yeah i'll be careful (thanks for telling me :) )

this is what appears: what do i do... :(

---

### Post by kroki on 2011-03-04
> **ikt said:**
> It's the BIOS, it's all your basic computer information, be careful with it :)

If you go into Standard CMOS setup, does it list your hard drive?

just quickly, how are you posting this info?

i borrowed my brother's laptop (with windows)

---

### Post by ikt on 2011-03-04
> **kroki said:**
> yeah i'll be careful (thanks for telling me :) )

this is what appears: what do i do... :(

damn it!

new bios's show the hard drive :/

Anyway, from this:

> **kroki said:**
> i'm going to try that.. 
i was pressing the f8 key when this appeared.. what do i select or can i do.. :(

It shows your hard drive isn't listed, so there is something wrong at a hardware level from what I can see.

It may be that your hard drive died, or it may be that the hard drive cable has fallen out.

Have to check it out.

---

### Post by gmurph59 on 2011-03-04
everything was working fine...now when I do a software update it comes up saying can only do a partial update some may be corrupted etc. then when I do the update it blows away my NVIDA driver and the next time I boot I'm at a CLI prompt and have to run safe mode then reactivate the NVIDA driver. I can't figure out why this is happening. Any ideas???

---

### Post by frankduffey on 2011-03-04
> **kroki said:**
> what means?
I am a Computer Tech with over 15 yrs experience I am also A+ Certified.  I also was a business partner and ran a computer business! I would try and reset the bios to the original settings hopefully your hard drive will be detected if not I would turn this over to a Computer tech at a local store who may be able to recover your hard drive. It would be way to completed to explain to someone new how to attempt this recovery. as you have stated there are important documents on the drive. So Whats the loss worth to you more than a PC techs hour charge That's why we are A+ Certified and trained to solve problems that the average user can not. I wish you luck but 
get someone who is knowledgeable and a working tech not a friend who "knows About computers!!" believe me I can tell you horror stories about a business who let her son work on her server. OMG! so PLEASE TAKE THE PC hey year 2000 is not that old crap I ran Linux on systems older than that!

---

### Post by donut123 on 2011-05-26
Hello...was the computer ever repaired? I  A+  computer guy..      did  you tell  Him about the jumpers ? And the old computer...it could have been the smart drive..it could have went dead,,I had a computer do that..it just died..and that was it.We may never know the outcome of the computer.

---

