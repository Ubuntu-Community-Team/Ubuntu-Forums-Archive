---
title: "Installation issues"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by mpennell on 2009-06-01
Having HORRIBLE xubuntu experience here! NOTHING is working like any of the websites I've looked at say they should.

1, I downloaded xubuntu onto my hard drive; apparently, it partitioned itself and has taken up residence. Really, I wanted to just make a "Live CD" but that wasn't working either (I am on the verge of possibly having figured out the live CD-- a disc is SUPPOSEDLY burning right as I speak). But I cannot get into this Xubuntu on my hard-drive-- typing "Ubuntu" or "Xubuntu" or whatever, like some older threads suggested, DO NOT WORK. There was NO username ever given in the first place when I installed it. I recall a password screen, but no username.

2. I forget was 2 was... grr I"m so FRUSTRATED!!!

---

### Post by wpshooter on 2009-06-01
Let's make sure that you are understanding the procedure corrrectly.

1) Assuming that you are just wanting to look at the live CD version of Xubuntu and then perhaps installing it on your hard drive, are you first downloading the ISO image of Xubuntu onto your hard drive and then..

2) Are you then BURNING (not copying as data) to a CD and then..

3) Are you booting your computer to that burned CD, making sure that your CD drive is your FIRST bootable device in the BIOS ?

4) Checking the integrity of the burn Xubuntu CD using the verification function that is found on the initial Xubuntu boot screen menu ?

---

### Post by mpennell on 2009-06-01
3) Are you booting your computer to that burned CD, making sure that your CD drive is your FIRST bootable device in the BIOS ?

---

How is that done?
Also, what about the username issue? I mean, Xubuntu is apparently on my hard drive raring to go, but for a mysterious username and password that were never actually set up in the first place?

---

### Post by wpshooter on 2009-06-01
Do you know how to get into the BIOS/setup of your computer ?

If so, find the section in the BIOS having to do with which order drives/devices are booted and then make sure that your CD drive is the first one on the listing.

P. S. - What is it that makes you think that Xubuntu is already installed on your hard drive.  JUST downloading the ISO to your hard drive is NOT the same thing as installing the O/S on your computer !!!

---

### Post by LewRockwell on 2009-06-01
almost sounds like the computer is booting from the disc image...weird...

---

### Post by wpshooter on 2009-06-01
> **LewRockwell said:**
> almost sounds like the computer is booting from the disc image...weird...

Not weird, if the ISO image is properly burned to the CD and the CD is the first boot device, then booting to the CD is exactly what should happen.  And from there, (if it is the live version), then O/S can be ran directly from the CD or it can also be installed to the hard drive and subsequently ran from that hard drive, if it is the first accessible boot device.

---

### Post by LewRockwell on 2009-06-01
> **wpshooter said:**
> Not weird, if the ISO image is properly burned to the CD and the CD is the first boot device, then booting to the CD is exactly what should happen.  And from there, (if it is the live version), then O/S can be ran directly from the CD or it can also be installed to the hard drive and subsequently ran from that hard drive, if it is the first accessible boot device.

 I was referring to the disk image(ISO)...not a CD...  I was under the impression that a CD had not been fully produced and introduced into the equation yet...

---

### Post by wpshooter on 2009-06-01
> **LewRockwell said:**
> I was referring to the disk image(ISO)...not a CD...  I was under the impression that a CD had not been fully produced and introduced into the equation yet...
If they have not done so, I think all they simply need to do is properly BURN that ISO to a CD and then boot to it.  And then either run O/S from the CD or install it from that same CD.

It sounds sort of fun the way this was phrased "the ISO image partitioned itself and has taken up residence on the drive".

---

### Post by mpennell on 2009-06-01
Well, since I have Xubuntu actually loading up, bringing me to it's login screen (noted above -- username/password problem) I assume that it's on my hard drive, yes?

I do not know how to load from the BIOS/setup.

---

### Post by LewRockwell on 2009-06-01
> **mpennell said:**
> Well, since I have Xubuntu actually loading up, bringing me to it's login screen (noted above -- username/password problem) I assume that it's on my hard drive, yes?

I do not know how to load from the BIOS/setup.

 do you have ANY CD disk in your optical drive when this is happening?

---

### Post by lisati on 2009-06-01
One question mpennell, which might mean something to the people who have responded to the original question: Did you use a thing called "Wubi" to download Xubuntu and then install it "within windows"?

A comment: The LiveCD will let you try Xubuntu without the need for a username or password. If you're being asked for a user name and password, this usually means that either you've actually installed Xubuntu and given it the necessary details already, or something has gone wrong.

---

### Post by wpshooter on 2009-06-01
Did you use WUBI ?  If so, it would seem that you would have mentioned this in your original post !!!

---

### Post by LewRockwell on 2009-06-01
> **wpshooter said:**
> Did you use WUBI ?  If so, it would seem that you would have mentioned this in your original post !!!

I guess we need to put a better bigger notice asking for complete details including hardware/software/operating-systems/etc.

---

### Post by mpennell on 2009-06-01
I figured out the BIOS thing. But I guess the disc I thought I had made didn't work out.

Meanwhile, somewhere in the Dell Back-forty, Xubuntu is apparently lurking. No, there was no disc whatsoever-- I hadn't even attempted to burn a disc yet when X moved in. I was click-tapping away and next thing I knew, he was hanging his undies across the room, having partitioned his side (the one away from the Windows). BUT he won't let me in! 

"Username! Password!" he unyieldingly asserts... But all I remember is a password screen where I entered a password in setup, but NEVER a username. None. Nada. Zilch. So I'm over here by the Windows, limping along, thinking WTF? You invite a dude over and he's all "Hey, show me your papers" like some kind of cyber-gestapo. 

Any suggestions? As said, I've already tried entering "ubuntu" or "xubuntu" and then with caps, and entering with nothing at all... Totally shut out.

?

---

### Post by Mornedhel on 2009-06-01
> **LewRockwell said:**
> I guess we need to put a better bigger notice asking for complete details including hardware/software/operating-systems/etc.

Christ, yes. Something along the lines of "Please be more precise than 'I did something and now it doesn't work anymore'". No offense meant to the OP : his post was way more descriptive than many I've seen here.

I don't know about Xubuntu, but the Ubuntu installer automatically fills the "Username" field with the user's first name when he types it.

So, try your first name ?...

** everything under this line caused by misunderstanding -- ignore

> **mpennell said:**
> I was click-tapping away and next thing I knew [...]

Please, pretty please, stop doing that. Read what comes up on the screen. Error messages are there for a reason. There are people out there, trying to abide by the Human Interface Guidelines, designing error messages so that users can understand them and fix the problem, or at least get an idea of what's wrong. And then we get users here saying "some error message popped up and I clicked it ; what's wrong ?".

---

### Post by mpennell on 2009-06-01
I exaggerate, as I relay my dramatic tale of chills and thrills. No, I wasn't bulling along. The installation process actually went surprisingly well. I followed directions carefully. I simply didn't anticipate being locked out once I rebooted, you see?

---

### Post by mpennell on 2009-06-01
I reckon I could relay all sorts of specs but technically, Xubuntu appears to be working great!

He just won't let me use it.

What technical tid-bits ya wanna know? Dell, black, in the kitchen, cup of coffee in a Red Sox mug (go, baby!), and this nonsensical foolishness: Dell Dimension DIM2400, Intel, Pentium, 4 CPU 2.66GHz, 256 MB of RAM, and a little sticky on the front that reminds me to pick up the kid at school.

Yo. You guys are great!

Ooh-- my fresh new disc just popped out of the oven like a batch of choco chunk cookies! Let's see what happens now, eh?

I'll be back...

---

### Post by Mornedhel on 2009-06-01
My apologies.

It's just that this type of user attitude is often seen on these forums, usually from new Windows converts, and it can quickly get tiring to explain to someone that unless we know the contents of the error message we can't diagnose his problem however knowledgeable we are, and can he try again but this time read before clicking please.

If you have tried entering your first name and it didn't work, at the very worst you can use any Linux LiveCD (Ubuntu or another), open a terminal and type sudo less /etc/passwd, then look at the first column of text if you can recognize something that would look like your username.

---

### Post by mpennell on 2009-06-01
Nope. My disc didn't work. Hmm... Guess I got in over my head.

---

### Post by mal1958 on 2009-06-01
> **Mornedhel said:**
> My apologies.

It's just that this type of user attitude is often seen on these forums, usually from new Windows converts, and it can quickly get tiring to explain to someone that unless we know the contents of the error message we can't diagnose his problem however knowledgeable we are, and can he try again but this time read before clicking please.

If you have tried entering your first name and it didn't work, at the very worst you can use any Linux LiveCD (Ubuntu or another), open a terminal and type sudo less /etc/passwd, then look at the first column of text if you can recognize something that would look like your username.


I know what you mean.  I was using Xubuntu for a while till I got my disk from Canonical for Ubuntu 9.04.  I had some probs and posted here but when I posted, I posted details, and was helped almost instantly.  If this is a valid message (I mean no insult to anyone here, but trolls are not a rarity in forums) then it seems obvious that he has gotten it loaded onto his system.  I used the live cd once, then installed.  mpennell states that there was no cd made.  This means that mpennell installed it over the net, or used deamon tools or the virtual drive of alcohol 120 % to mount the image and install it that way.  The term "click tapping away" is what has me flommuxed.  I wouldn't even try to install an OS unless I had a base idea as to what to do.  The  free pdf book that is for download in one of the stickies is perfect for that.  Or you could go and pick up a couple of books:  Ubuntu Kung Fu, (and) Beginning Ubuntu rev 3 come to mind.  The same author wrote both and they are simple and clear.  As to your problem of not getting a disk to burn properly, I believe there is a link somewhere that you could go to and get a free copy of the disk sent to you from Canonical, like I did.  Maybe that would help.

Mike

---

### Post by mpennell on 2009-06-01
Thanks, Mike! Feel ye not flummoxed by hyperbolic jargon; it is, after all, sorta like how a newbie feels on one of these types of forums. Ya know?

Clicka tappa! Hey, you know, I think I'm heading for a Windows XP reboot. The wife and kids are PISSED. You're absolutely right: I cannon-balled off the end of the dock-- into the deep! 

But come on-- you gotta admire the pluck, no? The insane charge-of-the-light-brigade courage? At least one little byte, yes?

SO, let me get this straight, just to be clear, since I see that the earnest Hack Pack gets a wee flummed on the jot and tittle: ----> Does no one here know of a way to get through the Username/Password issue? A back door, a reset of some type?

Anyone?

---

### Post by Gazneth on 2009-06-01
At the Boot Menu select the recovery mode option, Then:
 Type```
ls /home
```

This will tell you your username.

Your username should appear in the results. Then, enter:
```
passwd <username> 
```

Please don't type the < > symbols just your username.
This will allow you to change your password if you like.

and follow the prompts. Note: your password will not appear, not even as ***** as you type it.

---

### Post by mal1958 on 2009-06-01
> **mpennell said:**
> Thanks, Mike! Feel ye not flummoxed by hyperbolic jargon; it is, after all, sorta like how a newbie feels on one of these types of forums. Ya know?

Clicka tappa! Hey, you know, I think I'm heading for a Windows XP reboot. The wife and kids are PISSED. You're absolutely right: I cannon-balled off the end of the dock-- into the deep! 

But come on-- you gotta admire the pluck, no? The insane charge-of-the-light-brigade courage? At least one little byte, yes?

SO, let me get this straight, just to be clear, since I see that the earnest Hack Pack gets a wee flummed on the jot and tittle: ----> Does no one here know of a way to get through the Username/Password issue? A back door, a reset of some type?

Anyone?

OK, I may be feeding one right now, but here goes.  I am a newbie too (at east to Linux).  I have worked on computers since the mid 70's and never once gone into the jargon that you are throwing out. But enough of this.  If you wish to get Xubuntu on your system then there is an easy path.  

[LIST=1]
[*]Back up your data on the HD.  I cannot stress this enough.  If you don't back up important data and lose it then you do deserve to get laughed at (or at least a few chuckles).
[*]contact Canonical (the company that publishes Ubuntu. On the main Ubuntu site there should be a link somewhere where you can request a free cd with xubuntu on it.  That will work, I failed to burn a proper copy of Ubuntu and installed xubuntu.  But I requested a free cd and used that when it arrived.
[*]Get the books I mentioned in my previous post.  They will help, and are better then 'click-tapping' any day of the week.
[*]Read at least the book:  Beginning Ubuntu;  at least skim through it but read the parts where it goes into detail on installing and some of the basic commands (such as sudo!!!)
[*]Now here comes the gut wrencher.  If you want to dual boot, you may have to do a full reinstall of Windows to wipe the existing partition of xubuntu (Maybe even use fdisk to get rid of it).
[*]Here is an important bit of advice:  Get some more memory.  Your system is powerful enough to handle at least a gig of ram, and you have only 256 (or is that the ram on your video card?)  Most P4's that I have seen have a minimum of 512 meg at the least.
[*]If it were me, I would get a second HD and use that as the Xubuntu side.  This way if you find that you don't like xubuntu, you can at least format the second HD as fat32 or NTFS and have more space for windows.
[*]once you either do a full reinstall of windows xp SP2, or remove the existing partition (please do not ask me how, as I do not know.  there are programs out there that can resize partitions and remove unwanted ones but they all have a risk of wiping your current OS in the attempt.
[*]and here is a real big question.  Why are you trying to use xubuntu?  Even if that ram spec you gave was system ram, you can get more, and I would reccomend at least up to one gig, two if possible.  Your system can handle the full Ubuntu version standing on it's perverbial head.  With more ram, and a second HD, you could be using the full version of Ubuntu instead of a slimmed down version.
[*]OK, back to the install.  Once you have a clean drive with windows on it, insert either the xubutu disk or the ubutu disk while windows is running (you must have autorun on for your cdrom drive.
[*]This is assuming that you have read at least the install portion of the book, or at least downloaded the pdf guide that you can get through one of the messages that is stickied at the top,   If your system does not boot from the cd, then the last answer saying Help me boot is the one that you want.  It will install a barebones copy of Xubuntu or Ubuntu on your HD and you will need to have the cd in the tray when you reboot.
[*]the rest is up to you.
[/LIST]
   Getting back to your system.  I can run Ubuntu and my system is far older then yours.


[LIST]
[*]Intel Pent 3  1 Gigahertz
[*]384 megs of ram (if that 256 was your system ram then I have you beat here)
[*]Invidia GeForce 6400 (OverClocked by a company called BFG (No I m not kidding))
[*]Creative Labs Sound Blaster Audigy LE
[*]Maxstore Quantum fireball 60 gig HD
[*]48 rpm speed CD-RW by LG
[*]DVD-Rom drive
[/LIST]

   I will admit that it seems a bit slower then it should, but this is due to the fact that my system is eight years old (Read 10 computer years to one real year).  I just hope that I haven't wasted my time, a lot of space on this forum, and a small headache in wracking my fifty year old brain for all this info.

Mike

(EDIT) Please talk in standard English, Not jargon, It helps us to better help you if we can understand what you are saying without the use of an interpreter.  :)

---

### Post by mpennell on 2009-06-03
Mike, thanks for the input!

Now, as to jargon, I literally don't know what you are talking about. Yet the jargon in cyberworld is so intense, I need to filter it through my mini Mr Coffee before I can dare a sip.

But no matter.

I got back to a point where I could download Ubuntu via Wubi (I love that name!) and so guess what the username was? Well, the point is that there WAS a username--it was autofilled into the field on the setup screen. Naturally, I didn't recall it, since I never had to pick it and type it in.

Now, a word re: books, and, if I may be so forthright: The attitude I've run straight into here in the Ubuntu world is one of touchy arrogance. No, wait-- just relax-- this is not a flame nor a destructive criticism (meaning, it's a constructive one). The Ubuntu concept is VERY COOL-- and really, we should all promote it, not get prickly when an Utterly Clueless Newbie appears stumbling through the cyberlobby of Hotel Ubuntu. 

For ex: more than one have toned a bit critically about "read the book." Wellllll-- are you aware that when you go to the Ubuntu home page there is NOTHING immediately evident about a book or books or even the need to read one? It's all very "Hey, jump on board! Easy download! Up and running fast!" So I tried and got a bit flustered.

So I gently, compassionately, and optimistically point this out to all willing to hear.

It's a cool thing and I may be enthusiastically on board (but for the Missus and kids...you know?). If so, I will do all I can to embrace the Utterly Clueless Newbie (UCN). (That might make a good title for a forum section: Utterly Clueless Newbie!). And if the answer is that the UCN should not attempt Ubuntu, then I think it should be clearly spelled out on the home page.

Hey, Mike, and all-- have a rockin' good day! (And see my other post!)

---

### Post by mpennell on 2009-06-03
Oh. And the other issue that was quite the unseen monkey wrench: my CDROM drive stopped reading. BUT I didn't know this for a long time (because it was humming and lighting up just fine). So, this was adding to my confusion as I tried to make a Live CD. 

Funny expression..."Live CD"... Sounds like an album of a band ("This weekend only! Come see Ubuntu live at the Dell Arena!"). Yuk yuk!

---

### Post by mal1958 on 2009-06-03
> **mpennell said:**
> Oh. And the other issue that was quite the unseen monkey wrench: my CDROM drive stopped reading. BUT I didn't know this for a long time (because it was humming and lighting up just fine). So, this was adding to my confusion as I tried to make a Live CD. 

Funny expression..."Live CD"... Sounds like an album of a band ("This weekend only! Come see Ubuntu live at the Dell Arena!"). Yuk yuk!

Ouch.  (on the cd-rom).  OK.  First, though it is not listed on the main site about any books needed, when you are talking about ***[COLOR=Red]any[/COLOR]*** OS, Linux, Windows, OS2-Warp, MAC OS, any of them, it is figured to be an unwritten caviet, read a book about it.  Windows is easy, you can probably pick one up in an Osco drug store near the magazine rack.  The rest, wish ya luck in most cases is the catch phrase.

   Now, as to the supposed arrogance.  If you wish to see real arrogance in the computer world, look to the Windows people.   They are more then happy to tell you to 'Read the ****** Manual' and then let you hang there.  I nentioned the books because they are a real help in many situations.  

As to the claim of Ubuntu saying that it is easy to install, run, and maintain, I agree with that 10000%.  I am fifty years old and have tried over fourteen different flavors of Linux dating back to a copy of Red Hat that I downloaded back in the early 90's.  Thats a lot of testing.  And out of all of them, I couldn't get one to fully work for me.  Ubuntu is the first one that went on my system, and worked from moment one.  I even heard sound for the first time while in Linux.  So it is simple and easy, but even it requires a bit of work.  And this community is the friendliest that I have run across.  In my short time here, I have found more help then over six months trying in the Linux Mandrake community.  And, I have already helped three (I hope) folks with the info I have gotten.  

 (The rest of this was an Edit)  

   Had to go away from the keyboard for a short and decided to edit this instead of double-posting.  

  I want to apologize if I came across as arrogant, that was not my intent.  I was trying to get a point across to you, and that point was _detail_.  That is what we need from most folk to help them.  I don't mean a full drawn out explanation of what they were doing while they were installing the OS, I mean what message popped up and at what point.   Some of those messages can mean the difference between being able to help someone or not,  that is all.  

   One more thing.  Anybody can use linux.  With some it just takes a bit of work, and a learning period to do so.  I wish you luck in your Linux experience and hope to hear from you again.

Mike

---

### Post by mpennell on 2009-06-04
...and indeed, I came off like a punch-drunk hyena who'd skipped his daily prozac. 

Got a little panicky. But I'm good now. Really. Trust me.

[Booting up sanity files...Installing caffeine...Running mental diagnostics...]

I have discovered that when one calms down, people here are REALLY helpful! Very, very, very cool. 

Cheers!

---

### Post by mal1958 on 2009-06-05
> **mpennell said:**
> ...and indeed, I came off like a punch-drunk hyena who'd skipped his daily prozac. 

Got a little panicky. But I'm good now. Really. Trust me.

[Booting up sanity files...Installing caffeine...Running mental diagnostics...]

I have discovered that when one calms down, people here are REALLY helpful! Very, very, very cool. 

Cheers!

I understand completely about the panicy feeling.  I got that way back when I was trying out a version of Suse, and it couldn't find my HD.  As I said before, Ubuntu is the easiest Linux that I ever worked with.  I nearly fell out of my chair when I heard the opening sound when it booted for the first time.  In the fourteen previous attempts, I had never gotten sound to work with it.  And that was with fiddeling with the command line, drivers (HAH!), and a myriad of other things.  Now I have a great OS, and Windows is deligated to a 11 gig partition for the sole purpose of running Alpha Centauri Alien Crossfire, and Civilization 3.  And maybe NeverWinter Nights, if I can't get it to function in Linux.

Next time you seem to have a problem, take the motto of 'HitchHikers Guide to the Galaxy" to heart:  Don't Panic.  Help is available here for most any problem.  Ciao.

Mike

---

