---
title: "I think I've ruined my hard drive - if not more also."
date: 2010-02-11
forum: New to Ubuntu
---

### Post by Chris Edgell on 2010-02-11
You know lately, I've asked about switching the two hard drives that are in same make and model Dellls.

Let me tell you about the machine I was going to borrow from; and some of you know parts of my story.

When I WAS going to put Jaunty "on the whole drive", I was assured that any former partitions, firewalls etc. would not matter -- it would all be covered.  Also, this computer I'm referring to has 2000MS inside and I got a thread pulled for asking how to bypass the password.

So I just got into the BIOS and somehow got it messed up so that it could not detect it's hard drive.  After a thread about how to reset the Bios to the default, I had removed the battery for an hour, then let it sit...for a week.

When I wanted to borrow the hard drive, I said to myself, let me just install this Jaunty 9.04 from the liveCD and if that works, well BIOS must have reset and it's found the hard drive, if not I'll go from there.

I went on and on through the install process..it took a long time.  At one point I looked and I had a very complex picture that filled the screen with thousands of little black bands each one next to the other, with some red dots, some blue dots..it looked like an artistic rendition of a multi-faceted defrag plan.  One area less that a square inch was faded looking.  Nothing worked...I waited a half hour or so then shut down manually, then began a new install over whatever I had goin' on there.

It installed fully, then I got a notice to install the updates, which I had planned to do.  When it started, it said 152MB, soon thereafter it said, "4th of 200" -- that was okay too, same as last time I'd installed on another computer.

The next time I looked, about an hour later, the screen was black, nothing I did caused anything to come to the screen.  This is probably where I should have taken audiomick's advice to me, "Don't be in any hurry, let it go, leave it alone, let the computer chew on whatever it's trying to do..."  But no, I had to do anything to get a picture on the screen.  Finally, I shut it down and waited about 15 minutes and tried to see if the new install would boot. 

Here's what I got:

Low-Graphics Mode
You may need to update your configuration to solve
    (EE) GARTInit unable to open/dev/a gpgart   (no such file or directory)
    (EE) drm drm Open Failed
    (EE) Intel (O): [dr]????Screeninit failed.   Disabling DRI
    (EE) Intel (O): couldn't allocate video memory

Now I've tried to reboot a few times; each time I get the Dell start screen offering me F2 or F12 

Then I get boot screen about booting hd 0.0 ext3
grub loading... (it goes by quickly, I can't stop it.)

Then I get a screen that reminds me of BIOS:  big, blocky, white on black, about 10 lines beginning
Skip starting firewall     not enabled
Config. net interfaces   [color=red] fail [/color]
loading ADCI   (or some such)
the rest of the 10 or so lines

Then resorts to that message above:
Low Graphics Mode

I can only post this and leave it here...for anyone who comes along who knows what has happened; what checks I can do...

---

### Post by ubunterooster on 2010-02-11
I understand you had an incomplete install? :( Only thing I can say is try again...

---

### Post by ubunterooster on 2010-02-11
Sorry, I missread. I had same update problem at one point and did same thing; same thing happened. I reinstalled (always have backups); all was fine.

---

### Post by Chris Edgell on 2010-02-11
You have given me some hope.

Right now it has one stick of RAM 254MB.  Do you think it would improve my chances for a good install AND updates if I put another stick of 254MB (I could borrow it from the other one...)  Or doesn't all this have anything much to do with RAM; mostly is it about the Hard Drive?

---

### Post by audiomick on 2010-02-11
Hi Chris.
I think you would have better luck with more RAM. I just found something here
[http://www.ubuntu.com/products/whatisubuntu/desktopedition](http://www.ubuntu.com/products/whatisubuntu/desktopedition)
at the bottom that says you need 348MB of RAM for the live CD installer, which I think is the one you have. I actually thought I had read somewhere that 512 is recommended.

When you are changing the RAM, be careful not to touch the connector. The chips are very sensitive to static electricity. You don't have to panic about it, but don't touch anything on the RAM that looks like metal.

---

### Post by ubunterooster on 2010-02-11
I would reccomend you stick more RAM in, yes. You are near the minimum and this could cause problems.

---

### Post by Chris Edgell on 2010-02-11
Hi Michael, thanks.

So I SHOULD take off my little tinfoil hat?   LOL

and thank you again ubunterooster.....

Here I go.

---

### Post by Sir Jasper on 2010-02-11
Hi,

Most importantly does your #1 computer ¨still¨ work very much as you want and need it to?

Also, do you now have 4 computers or is it still 3? 

It may or may not be helpful to move some RAM from one machine to another, but you need to check it is fully compatible with the RAM in the machine it´s being transferred to (it probably is - but it&#347; best to check).

If you want some strategic and/or tactical advice then telling us the makes, models, types (desktop etc), RAM (amounts and types) Hard Drives (sizes and revolutions per minute),  Operating Systems  and working order for each would doubtless help us to help you.

My regards

PS If you cannot find all that gen you could just let us know as much as you reasonably can about all your computers.

---

### Post by Chris Edgell on 2010-02-11
Now midway through the installation I get this window:

Installation Failed

The installer encountered an error copying files to the hard disk"

[Errno 5] Input/output error: '/target/usr/src/linux-headers-2.6.28-11/arch/arm/mach-mv78xx0/include'

This is often due to a faulty hard disk.  It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.

---

### Post by Chris Edgell on 2010-02-11
Hi Sir Jasper,

Yes fortunately my primary computer works; that's the good part.  (It's the one my friend originally set up with Jaunty.)

To answer your question:  I have 4 computers, that original yard sale special, and 3 Optiplex GX260 Dells.

I call them: Yard Sale Special (JYD "Junk Yard Dog")
#1Kirk (order rcvd/he set it up
#2Chris (the one I'm working on now)
#3Sarah (Kirk's wife/latest acquisition that truthfully, although it's embarrassing to admit, I seem to have screwed that hard drive up too--I'm wondering if it HAS something to do with the fact that both of them have one stick of RAM of 254MB... be that as it may they both seem screwed up.

the 4th one the Junk yard dog is the one I first successfully installed Jaunty xubuntu in and it was all great---but then could not get sound...I had put that aside as I had two that were just alike and could use one for a test case, if I could get one going.. which as you now know, I could not.

With this, I had just come to the decision yesterday, (when I got #3 Sarah) that I would try to concentrate on one at a time.  But that was the one the install failed and I was going to try to swap hds but then decided to make sure the hd was working on this one.


Well, anyway, I hope no one bears me any ill will, because I seem to have screwed up a great gift.  (I'd hate to be so sardonic as to say, "The story of my life"
Great intentions, hasty actions, screwed end-results, many tears and prayers, and ultimately "relying on the kindness of strangers".  

But I wax overly-dramatic  ...actually moving into rhetoric and hyperbole...because I have not fallen as far as Blanche...and I haven't shed a tear over these computers...but still, somehow, it's sorta' true, about the story of my life -- not that I should tell all to you all.  I think it's a line from the Magnificent Seven, "You can always serve as a bad example."  I don't seek pity, God knows, I just want to present my case truly.

Whew!

---

### Post by Sir Jasper on 2010-02-11
Hi again,

I suggest you keep this thread going, but halt further action pending detailed advice and then probably mulling things over for a few days before deciding what to try next.

There are many possibilites (and complexities eg upgrade ideas) to think through.

I&#7743; off to bed now as it&#347; 3.40 am here. I&#314;l revisit in a few days for your latest news.

---

### Post by Chris Edgell on 2010-02-11
Good-night, Sir Jasper
Nice seeing you.  Thanks for your kind words.

Christine

---

### Post by k3lt01 on 2010-02-12
Just noticed this thread and thought I might suggest a couple of things.

1. I think you haven't got enough RAM to install from a LiveCD, I would suggest using an Alternate CD instead.
2. Your post mentions moving the computer to a cooler environment, I have had this happen to me a few times, but then again it is summer here in Australia and we don't get the freezing temps you do in the USA. Is it possible the PC could be overheating during the install?

---

### Post by Chris Edgell on 2010-02-12
I did put another stick of RAM so now it's 254 + 254 = 508MB of RAM

That was in there before this last install that I was describing.
Should that be enough for this Jaunty 9.04 xubuntu (617MB)?

Maybe it was hot from me working it trying to read the stuff that was popping up - so that I could write that last post.  Audiomick keeps telling me not to be in such a big hurry to do the NEXT thing...give it time to rest, or cogitate, or compute, or chew on the stuff in there...

Maybe I'll try it again tomorrow and see if the heat warning part disappears.

Thanks for "writing".

---

### Post by Rex Bouwense on 2010-02-12
> **Chris Edgell said:**
> I did put another stick of RAM so now it's 254 + 254 = 508MB of RAM

That was in there before this last install that I was describing.
Should that be enough for this Jaunty 9.04 xubuntu (617MB)?

Maybe it was hot from me working it trying to read the stuff that was popping up - so that I could write that last post.  Audiomick keeps telling me not to be in such a big hurry to do the NEXT thing...give it time to rest, or cogitate, or compute, or chew on the stuff in there...

Maybe I'll try it again tomorrow and see if the heat warning part disappears.

Thanks for "writing".

Christine every time I log on you have a new problem.  You must be having fun with those other three computers.  I was once told by a very old and very wise Geek, that you still have to slow down and smell the roses.  Michael was absolutely correct in his advice.  I also have several computers.  Hardy on one which is a desktop.  It has been there for about a year plus just getting updated.  The one I experiment on is a laptop with Karmic and it still doesn't have WLAN capabilities but I'm working on that.  It sure is fun to learn about this stuff.  If I had had all of this great stuff when I was a kid, I would have grown up to be a Super Geek instead of a perpetual Noob.

---

### Post by audiomick on 2010-02-12
Hi Chris.
It wouldn't hurt at this point to just have a look at the hardware itself and make sure it is ok. This is just a suggestion, not anything you absolutely have to do.

This will be a bit tedious and time consuming, but will at least let you know if you are flogging a dead horse or not...;)

I take it you can boot into the live CD on the machine in question.
Firstly, boot into the live CD and look at the system monitor under system> administration to make sure that the machine is recognizing all of the RAM, or have you already done that? Alternatively you could do
```
top
```which I think you already know, don't you? With that, you should see a number next to "mem" with a 5 at the start. If the number still begins with two, it means the machine is not recognizing the new RAM stick.

The next thing would be to reboot, still using the live CD, and choose the memtest option from the menu. This checks your RAM. Let it run for a while, maybe an hour or so minimum. It tells you things like "first pass" and percent completed. Let it go till you think it has had enough time to do what it needs to.
The important thing is the area at the bottom right. There should be no errors if the RAM is good. From memory, it doesn't show anything if it has found nothing, and shows a count if it is finding errors.

To look at the state of the Drive, you could use smartmontools. Have a look here for instructions on that.
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
Read through it a couple of times before you try it. It appears daunting, but is actually not that hard. I have only used it once, on my old laptop, but from that I know that it works from the live CD. Basically, you have to check that the drive supports the function smart monitoring and that it is enabled (probably is), tell it to do the check, then tell it to go and collect the results. It wont report anything automatically. Once you get the results, they are pretty easy to understand. The check, like the memtest one, takes a bit of time. I think my old laptop, with a 1.6GHz processor and an 80GB Drive, needed about 80 minutes.

---

### Post by Chris Edgell on 2010-02-12
Hi, hey Rex, nice to see you.

"Christine every time I log on you have a new problem."

You got that right...I just hope that when people see my name, they don't go "Oh, no..."  

I've gotten frustrated with people that keep making, what can I say, stupid mistakes...(like don't know how to make a left-hand turn).  Geez, now it's ME, clomping around in computer world.

I'd be lyin' if I said I'm having fun...I'd be having fun if I did something and it WORKED...then I might get conceited...so the man upstairs may be keeping me down till I don't let it go to my head.  (I don't talk much about the man upstairs because I'm not used to having someone living above me...) :)  Seriously, I do tend to get over-elated when things go right, I have to watch out for, heck, the mood swings.  NOW you know me better. LOL    

My real goal and initial thrust, my motivation WAS to be able to put Linux in the old computers I hear about in a building with 500 apartments.  To give some retirees at least an email machine....now my goal is to learn enough to keep my system updated and not crashing out on me...and to prepare myself to be able to save my stuff in any eventuality.  The good deeds part would be an offshoot of me knowing what I'm doing.  "Don't get the horse before the cart, old girl."  as my earthly father would say.

So I go on, seeking to receive AND to give kindness AND intelligence as I pass through this world.

Thanks again.

Christine 

"And now for something completely different" as Monty Python would say... especially after getting in deep.

Hi, Audiomick, never fear offending me by saying something I might or should already know, if only that a good refreshment course is very good for me.  

Gotta' go...catch you all later!

---

### Post by audiomick on 2010-02-12
> **Chris Edgell said:**
> My real goal and initial thrust, my motivation WAS to be able to put Linux in the old computers I hear about in a building with 500 apartments.  To give some retirees at least an email machine....

Hey, great motivation! I reckon you'll get there.;)

---

### Post by raymondh on 2010-02-12
Ms. Christine,

I would consider audiomick's suggestion.

Check the HD.

Regards,

Raymond

---

### Post by Chris Edgell on 2010-02-22
It's beem a week or so and finally I got the energy to see what I can see again.  I am ON the computer that the HD may be messed up.

I've done everything to follow the instructions of audiomick in Post 16.  The Ram checked out with no errors.

I went to the smartmontest and am attaching the screenshot.

I had gone through all the menu :  Install.....It will only go to step 4 and won't offer me options about partitions anymore...though it did the first 2 times I tried to install.  (Remember I MAY have tried to do something while the download of updates was going on  -- something locked up on me there.  I'm pretty sure I had it doing too many things at once...THAT will corrupt...ruin the HD won't it.)  If you think it's ruined tell me what now.  If there's a possibility it's not ruined,,,at least I have some hope that the computer is not useless because I have booted from the liveCD and so everything else seems to work.

I have been at this for 2 hours and I have to go out: I just wanted to say this much to see what response I may get.  I'll be checking back in 7 hours and HOPE to hear something.

(So hi anyone, and thank you.....)

---

### Post by pirateghost on 2010-02-22
your screenshot indicates no network connection.  run```
ifconfig
``` and report back what it shows.

---

### Post by Chris Edgell on 2010-02-23
I will bring this up one more time to describe my disposition of the matter.

I have put both of those Dell gx260s aside.  I had been able to boot into the liveCD only once, almost by accident.  With neither of them was I able to boot up in any way again.  

The only advice I would want to bring this up again, would be some specific advice about whether it would be worth it to look for a used hard drive.  (Or what to do with a computer that won't boot up)  I know I will continue to check out various parts and pieces about what I've got and what went wrong.

I have brought out the one I call "The Junk Yard Dog", the one I got the whole kit and kaboodle at a yard sale for $45.  If you remember, I was thinking I knew what I was doing, when I installed Xubuntu Jaunty into it, seamlessly--well until I discovered there's no sound.  But this is my new project--"the JYD".

So let us allow this thread to sink into oblivion with the certain amount of shame for screwing up TWO perfectly, pretty-good 6-year-old computers.  I know they're pretty good because my primary computer, that was set up by someone who knew what he was doing, is perking along just fine...knock on wood.

---

### Post by Jazzy_Jeff on 2010-02-23
One thing you might try is using the Alternate Install CD. It is text based and might work better for you than the live cd. I only use the alternate install cd now when installing. I used to have problems with the livd cd's myself.

---

### Post by Chris Edgell on 2010-02-24
Okay, very good...I'll go burn that alternate CD.

Someone else just sent me a site for diagnostics for these Dells gx260.

[http://support.dell.com/support/edocs/systems/opgx260/en/ug/solvprob.htm](http://support.dell.com/support/edocs/systems/opgx260/en/ug/solvprob.htm)

They have four lights on the back.  On both of them, all four lights stay green, meaning all okay...so, you see, you never know, you think you're dead and then there is word of a grand resurrection.  God, I love it!

---

### Post by ranch hand on 2010-02-24
Before you start on any box that you are going to install Ubuntu, of any flavor, on make sure you have at least the 500 Mb of ram (I rounded that as what ever you have in the laptop is different than the 512 I run into in desktops).  They just run better with more ram.

Linux, unlike MS, runs on the ram.  It needs more to run right.

When you get the Live CD to run (always try that) pull up the partition editor gparted and format the drive to ext3 or 4, what ever you want.  This should clean the bugger up and tell you if it found any errors.

If it finds errors use the "dismount" option in the right click menu of gparted and then go to terminal and run;
```

sudo fsck

```This will check your drive and maybe even fix it.  It will give you a pretty good idea of if it is shot.

EDIT
You will soon have a truely light member of teh Ubuntu family.  Lubuntu.  I have the 10.04-testing version on my test drive.  The Live CD image was under 400Mb.  Installed with a lot of extras that I added and over 3Gb of music and images added it is well under 7Gb.

You may enjoy this:

[http://ubuntuforums.org/showthread.php?t=478237](http://ubuntuforums.org/showthread.php?t=478237)

Another thing to do when you boot to the LiveCD is to go to System>Preferences>Screensaver and uncheck the bugger so that it does not come up.  This uses ram and can really screw you on shaky systems.

This will make your life a lot easier in these adventures.

Remember to breath occasionaly.  This helps.

Have FUN.

---

### Post by Chris Edgell on 2010-02-24
to the ranch hand from south east Montana.  I wonder what YOUR life is like...oh well..  just a meandering mind about people's lives.  Nice of you to take an interest and to wish me well, or at least to wish me fun, which is even better ...as I've said sometimes I'm so embarrassed...but still driven to be honest.  

The best thing I can say for myself is that I've tried, but there are so many facts that I wish I'd have kept a checklist of things to remember when installing a new OS.  I took it for granted that these two Dells were set to go...it was only after that I found out that the install may have gotten screwed up because of only having the 254 units of ram...and then to do the updates of about 300MB.  I SUPPOSE that was the sticking point that gave me the message about something getting locked because one thing had still been going on.  I'm not sure.  I'm putting the two sticks of RAM into the one machine for anything I may do now.

In both cases I had skipped anything about partitions and just went for "Install on the whole thing" or words to that effect.  That was the only way I knew how to get rid of the Windows that I didn't have the password to...now I know I could have painted with a less broad brush...but, as I say, I know so little about what I'm doing...although I'm learning everyday.

What about the alternateCD, I guess I'll have to learn about gparted to try the next install.

Shall I skip the screensaver entirely?

Thanks all
Chris

---

### Post by ranch hand on 2010-02-24
I do not think that the alt CD has a screen saver.

On the installed OS the screen saver, if not a resource hog, will not hurt too much unless there is something pretty heavy running.  I do not use one generally, except for security locking of the screen sometimes when I do not want someone messing with my box.

One thing about the alt cd is that it takes very little resources.

Even using the installer partitioner I would select the "Manual" option and edit any existing partitions out and install with 3 new ones.  A small / (root) partition first (10 to 20GB depending on drive size and how may add on apps may be loaded) right at the start of the drive for speed, a /swap partition at least the size of the ram (needs to be at least that size for "suspend" to work and it will be used with low ram) say 1Gb, and then the rest for /home.

You will have an easy time of doing that and end up with an easier to maintain system.  You will also have a very clean HDD.

I have too many OS' installed at all times and my drives are mainly one large extended partition (it is a type of primary partition that you can put many "logical" partitions inside of {you can only have 3 primary partitions}).  I also just put my swap at the very end of the drive.

The set up I gave is what System 76 uses on their great computers (they use a 15Gb / partition).  I got our first laptop last month from them and shrank the /home a hair, deleted the swap and created a new. slightly larger one  and then expanded the / partition to 25Gb so that there is a lot of room for what ever my wife wants on the bugger.  With a 320Gb drive I figured we had the space.

I have ten OS' on a pair of 320Gb drives, one with / partitions and one with /home partitions plus a large backup partition (empty ext4) that is my test platform.  I am actually on a second test drive now.  This is a 8.04 install that is trying to upgrade straight to 10.04 (you are supposed to be able go from LTS to LTS).  Testing this jump just started the 18th.  I have one success and 2 failures so far.

All my other drives are turned off for their protection.

If you check ebay there are good sellers with small drives that are new and pretty cheap.  If you can get by with under 100Gb they get real cheap anymore.  Remember when 10Gb was a huge drive?

---

### Post by Chris Edgell on 2010-02-24
I think I have 2 Gigs, can this be true?  It is dwarfed by the 320 GB you got there, ranch hand.

I Know this can't be right, I don't know where I got the idea, well, I was talking to my sister tonight and she said she has 3 gigs and I said I have 2.  So you think it runs in the family, or what??!!

---

### Post by ranch hand on 2010-02-24
Surely you have more than 2Gb.  Xubuntu will not install on 2Gb.  4Gb maybe but it would be too tight to have any storage unless you had another storage device.

I have Ubuntu8.10 on a 10Gb drive on an old HP (512 ram - had 128 when we got it).  It is pretty tight and slow.

A 20Gb drive would work (about 6 to 8 for /).  40Gb is very nice for most uses.  Bigger drives are faster as the OS is on very little of it unless you real pile on the music, movies, images, etc.  Documents take up very little space.

It is hard to find a drive under 5Gb and they are very old (in HDD time).  The installer partitioner will give the size of the drive in Mb.

If you can load the Live CD and get the gnome system monitor it will tell you more about the box than you probably want to know.  With an internet connection you can install stuff on your Live session.  It installs on the ram and will be there until you shut down or reboot.

One nice command you may want, if you do not know it already is:
```

lspci

```
That is a lower case L at the start.  As with all "ls" commands it gives a list.  In this case the pci devices.  This is just about everything except your mother board.  Lets you run a search on the buggers to see what problems they might be under Linux.  Does not have anything to do with the HDD either but that should be available in the bios.

---

### Post by Chris Edgell on 2010-02-24
Okay, okay...it's 80 GB, 

I don't know where that 2 came from...

I'm so absurd at times...

Thanks for covering a subject quite well, I appreciate your time.

---

### Post by Sir Jasper on 2010-02-24
Hi,

Just a suggestion - it seems you have an active and continuing interest in two of your machines - so what do you think about adding their specs to your signature. There is no need to reply.

Your JYD may have a name and model on its case and you may be able to research some details externally and/or internally.

If you raise (or re-raise) your sound issue someone will surely help you fix it.

My regards

I have upgraded (not a fresh install) from 9.04 to 9.10 and am well pleased with it (though I had to effect some minor adjustments). If sometime you decide to try 9.10 on one of your machines; then ideally at minimum, first copy and paste (or backup) your Home directory to your USB stick (or somewhere).

---

### Post by Chris Edgell on 2010-02-24
Hi Sir Jasper,

Very nice to see you.

It's good to hear that you upgraded to Karmic and it worked out okay.  I had begun to think that the internal upgrade v. liveCD NEVER worked...

It was great news about my 2 "broken" Dells: that is that this Dell gx260 has diagnostic lights on the back and they show 4 green lights (out of a possible 4) that indicate, shall I say, that nothing is wrong...so whatever IS wrong, I daresay, is not terminal.  We shall see, I have burned the alt disk to check out...I don't know if there is any downside to this "text" version, do you?  I don't have anything to lose by trying it...that is a freedom.

I was so embarrassed (nearly a permanent state with telling all about my computer knowledge or shall I say lack of...):  I told ranch hand that I'm thinking my hard drive is 2 GBs...he so nicely said, "Oh, surely it's bigger than that".  I guess I was thinking of the 2 GHz of my Intel Pentium processor...but that's no excuse for entertaining such an absurd possibility as having a 2 gigs of hard drive.  Really I can't say "what was I thinking " it's so obviously a lack of REAL thinking.  (Kind of like people who say, "Ten billion, I mean, 10 trillion...")...like saying, "It was a flea, no, I mean an elephant".  "People!  Get your brain in gear!"  (Insert MY name).

As far as the sound on the JYD goes: I am back to the "delete pulseaudio" solution, but I remember being so scared of that because when I looked at the huge amount of stuff that would be deleted...I got in a panic and truly, didn't dare begin to mess with all that stuff...(IS it okay to try and then try to go back if that "fix" doesn't work?)

Later..

---

### Post by ranch hand on 2010-02-24
I would not delete pulse right yet.  What is your sound card or controller?

The alt disk installer is prety much the old Debian installer that they still use.  Works great.  Just go slow and use the back button if you do not understand something.

If you check our join dates for this forum you will see we are close.  I joined 3 weeks before my first ever install of any Linux.  I am a noob.

There are things I have gotten pretty good at like multi-boot systems and grub and grub-legacy.  There is an awful lot that I am just clueless about.

If you need to get a real hardware modem (internal) going in Hardy I am pretty slick at that too.

---

### Post by Chris Edgell on 2010-02-24
"If you need to get a real hardware modem (internal) going in Hardy" ... I have no idea what this means, ranch hand, although I did like Hardy.  I wonder what I'd miss if I went back...what were the upgrades?  Sometimes I discover new things and wonder if they were in Hardy and I just didn't know it.  (I'm hard-pressed to think of one right now, although sizing on the desktop comes to mind...if you narrow a window, it comes back narrow.. but I digress.)

This is a weird thread -- it works for me -- but I HAVE managed to incorporate all problems with three machines that need work -- into one; as long as WE know what we're talking about, we'll be okay.  Heck, this weaving between the three is how I've been spending MY time; it's nice not suffering alone.  LOL

What I REALLY wonder right now is:  shall I sit here and try to match my synaptic downloads into the secondary computer that HAS 65 GB of space out of 80 as opposed to my primary that has about 15 GBs.  Do you think if I make them match, I'll get sound?  Sometimes I think I could do that as an experiment but ultimately, I'd like one for the fullness of like Open office and Gimp with the other one specializing in video and audio and a couple of good games...or do the programs overlap so much that they'd both need so much the same underlying structure?  (And if I didn't have open office installed on one, would they still send me the updates for OOo?  Can, or rather should I, pick and choose among and between updates?)

---

### Post by ranch hand on 2010-02-24
I really would like to know what your sound card or controller is.  This is critical to diagnosing sound problems.

Run and paste results of;
```

lspci

```

---

### Post by Chris Edgell on 2010-02-24
Darn, I got the print out of THIS machine...and this machine works fine.  D'oh.

I'll hook up the other one later and get that back to you.

---

### Post by ranch hand on 2010-02-24
Great.

There are 2 types of dial up modems.  Software or Winmodems (worthless buggers) and hardware modems.  All modems of all types communicate with the modem at the other end to negotiate and control your connection.  A software modem is not real good at negotiation.  A hardware modem negotiates with a club.  With a nail in it.  You do not get bumped off line, someone with a software modem does if the server is packed.

---

### Post by JKyleOKC on 2010-02-24
Chris,

I just came across this thread today. Sorry to hear you are having so many problems, but it does sound as if you're in the middle of a great learning opportunity!

Your problems with the hard disks on those Dells sound as if the BIOS setting for disk geometry has gotten scrambled somehow. The one where you tried to clear the BIOS settings is almost certainly blank at this point, so it would be a good one to experiment on.

Do you know how to get into the BIOS setup dialog? It's only possible at the start of the boot sequence, and it varies from one brand of BIOS to the next. I've never owned a Dell so don't know which key they use to get into setup; most of my machines use the DEL key (either of the two on the keyboard) but some use function key F2. That diagnostic site you visited may tell you exactly which key for your machine, too. The time to press the key is right after turning the system on, as soon as the POST message appears. If you're too early, the machine may beep at you and complain about a stuck key; if too late, nothing will happen and the system will try to boot. If just right, you'll get a menu that includes setting the date and time, plus selections for other menus to set up the peripherals.

When you get to this point, set the date and time but don't change anything else yet. Take the choice to "save and exit" so that the setup program will write your new date and time into the BIOS memory. Then tell us what the choices are so we can direct you to the proper one to get the disk set up again. And it will help if you can make out the BIOS maker's name from the screen.

All of the BIOS setup programs I've used over the years include a capability to detect the disk geometry and configure themselves for it, but none of them have done so automagically. They seem to wait until I go into the correct setup screen and tell them to do their thing. I'm pretty sure we can get things back to where you'll be able to format the disk and go through a successful installation...

EDIT: I went to the Dell manual site and they have step by step instructions for doing what you need! It's not on the specific page you linked to, however.

---

### Post by Chris Edgell on 2010-02-24
Hi Jim

Great to see you.

First things first, ranch hand, here is the screenshot of the lscpi.  So you tell me what you can see.  

About the modems,, all I can say  is that I don't have dial up.  You'll have to say further, if there is further to say.  I haven't seen the connection, no pun intended, but if there is something I need to understand, I'll try.

Now, every time I do something with any of these 3 non-primary boxes, I have to shuffle the sticks of RAM, as each had one stick of 256 mb.  So here I go to shut down the JYD (junk yard dog) and steal a stick....no bad jokes, on my part though I have the urge to push the metaphor.

Here I go to follow your instructions, Jim...I'll be back.  Well, since no comment has intervened, I'll just add on right here.

I got to the BIOS, no problem.  But even though I tried all I could, I could not make a bit of change of any time or date.  It's selected; it says SPACE, +, - to change, but nothing changes.  The date says, Mon Nov 15, 2004.  There's nothing BESIDES System Time and System Date, is there?

This IS the machine that right away I messed up the BIOS and could no longer detect the Hard Drive.  Since then, I tried to install over the entire disk, but sadly, I overlooked that there was only 256mb of RAM, so that when I tried to download the updates, it stopped; it said something about locking up for trying to do 2 things at once.  (I'll look for my notes if you want...)

I should look for the thread when you, Jim, told me about Primary Drive, Secondary, etc...I should be able to see where I've gotten to...I've left the battery out for half an hour so the BIOS should have reset.  I did finish the install -- let me see exactly what happens when I boot up.

---

### Post by k3lt01 on 2010-02-24
> **Chris Edgell said:**
> I got to the BIOS, no problem.  But even though I tried all I could, I could not make a bit of change of any time or date.  It's selected; it says SPACE, +, - to change, but nothing changes.  The date says, Mon Nov 15, 2004.  There's nothing BESIDES System Time and System Date, is there?

This IS the machine that right away I messed up the BIOS and could no longer detect the Hard Drive.  Since then, I tried to install over the entire disk, but sadly, I overlooked that there was only 256mb of RAM, so that when I tried to download the updates, it stopped; it said something about locking up for trying to do 2 things at once.  (I'll look for my notes if you want...)

I should look for the thread when you, Jim, told me about Primary Drive, Secondary, etc...I should be able to see where I've gotten to...I've left the battery out for half an hour so the BIOS should have reset.  I did finish the install -- let me see exactly what happens when I boot up.There should be other items in the BIOS like Hardware and Boot. The Hardware section will list your Motherboard type and specs along with your drives. The Boot section should list your boot order and often goes Floppy, HDD, etc. If you want to install Ubuntu make the CD/DVD drive the first Boot option, infact it is a good idea to leave it like that anyway.

---

### Post by Chris Edgell on 2010-02-24
Okay, I escape from the BIOS and I get the black screen, white print:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 15

(Oh, I've looked THAT up, error 15 is no file found.)  All I could do at this point is to start over, when I get the Dell screen choose: F2 Setup or F12 Boot up.

At the boot up if there is a liveCD in, it boots from there, I get the Xubuntu menu with those 5 choices: Try, Install, Check mem, Check disk, was there one more?

Without a CD in there,  well, this time I didn't get the Dell start up screen, it went right to the GRUB loading, please wait
Error 15

So I'll just wait and see.

---

### Post by Chris Edgell on 2010-02-24
Thank you k3lt01.

It's amazing how complex the BIOS is in my AMD box, and so downright basic in this Dell gx260.  But there are the areas that are entered by pressing enter.  I'm sure I can find hardware.  And yes, I have left the boot from the CD in the first position.

As it is, I'm leaving it alone, even though I'm quite darn sure that this Error 15 screen won't ever change...it'll only go away when I shut down.  But I am waiting...

Thanks.

---

### Post by k3lt01 on 2010-02-24
Sorry to tell you Chris but from my experience Error 15 means your gonna have to reinstall. It will be the quickest and easiest way to get it going.

---

### Post by ranch hand on 2010-02-24
I could see no screen shot.  It is easy to copy that output and paste it to a post if you ever get back to that box.  Don't rush.

I am on one of my 10.04 installs trying to get gnome -shell to run.  Not going real well.

---

### Post by Chris Edgell on 2010-02-24
To tell you the truth, I can't remember if I tried to reinstall, since I realized that I had only been working with 256mb of RAM.

I'm going to give it a try.  I have Jaunty Ubuntu, I have burned the Jaunty Xubuntu, (which is what I really want for a couple of reasons), it has been highly recommended to install the jaunty alternate CD because it's so lightweight--I burned that last night.

I've also had it recommended to me to try to work with the partitions and gparted (I have never tried any of that.)  I've been treating this install on this problem ridden machine like stucco:  cover it all!

Shall I try to partition too?

I must have forgotten the screenshot...thanks for your attitude, telling me there's no need to rush; I appreciate that.

---

### Post by ranch hand on 2010-02-24
Heck, you may as well partition the bugger.  It is a learning experience.

With a separate /home you can really bugger the OS and reinstall, reformatting the root partition and not the /home and have a new OS with your files intact (backup is highly recommended, I do it, I have also never needed it).

You might want to look at Zenix.  It is an Ubuntu respin using the Xfce desktop environment.  The main guy in that, I believe is bodhi.zazen who is a moderator here on the forums, and a wiz on security among other things.  He is also from Montana.

You might like it.  It is a "Buddhist Edition" of Ubuntu (no I am not) but that is mainly artwork (some is very fine) and some bookmarks.  Unlike Xubuntu it is actually lighter than Ubuntu.

[http://zenix-os.net/](http://zenix-os.net/)

It is my favorite Xfce distro.

---

### Post by k3lt01 on 2010-02-24
> **Chris Edgell said:**
> Shall I try to partition too?Yes, my recomendation would be / 10 gb, SWAP 2 gb, and /home the rest. That way you have plenty of room to move later if need be and the SWAP can take up any slack that is caused by having a small amount of RAM.

---

### Post by ranch hand on 2010-02-24
> **k3lt01 said:**
> Yes, my recomendation would be / 10 gb, SWAP 2 gb, and /home the rest. That way you have plenty of room to move later if need be and the SWAP can take up any slack that is caused by having a small amount of RAM.
+1

I prefer 15Gb / but that is me.

---

### Post by Chris Edgell on 2010-02-24
I didn't waid long.  I had taken a look at the start menu of this alt CD, and I'd seen that the 5th option: want to fix a broken system (or whatever word).  So trying this seems the thing to do.

About the second page: config. the network.

"Network auto config failed probably not using DHCP protocol.  Alternately the DHCP server may be slow or some network hardware is not working properly.

Retry network autoconfig.............succeeded. 

"Np dosl drove was detected..." gives me a list of choices, one of which is continue with no disk drive.

"No partitions found, so you will not be able to mount a root file system.  This may be caused by the kernel failing to detect your hard disk drive or failing to read the partition table, or the disk may be unpartitioned.  If you wish, you may investigate this from a shell in the installer environment.

No partitions found
<Go Back>                                   Continue

So I think I must go back and select install from the starting menu and get as far as partitions.

Any comments, at this point?

---

### Post by k3lt01 on 2010-02-24
> **Chris Edgell said:**
> Any comments, at this point?First things first, check your CD integrity. If thats ok then check your memory, if they both check out ok then try to install. If need be do the install and at each step post what is happening so we can work through it with you.

---

### Post by JKyleOKC on 2010-02-24
I see that your BIOS is not detecting any disk drive, so you probably need the step-by-step instructions for putting it back to factory settings. Go to this link, which is the Table of Contents for the Dell manual for your machines: [http://support.dell.com/support/edocs/systems/opgx260/en/ug/index.htm](http://support.dell.com/support/edocs/systems/opgx260/en/ug/index.htm)

From the contents, select "Jumper Settings" in the right-hand column. When there, hit the "Page Up" key to see the material just before it. There will be a series of steps numbered 1 through 5. Do them (although Step 1 may not be necessary) and see whether that helps.

If it doesn't, then try to install from the alternate CD and follow ranch hand's suggestion for partitioning. If it seems to be hung up, just leave it alone for a while. I've had some operations take as much as 12 hours to complete (but none recently)...

I suspect that the reason it couldn't find any disk drive was that the BIOS was still blank from the reset attempts, because if the disk itself was not working you would not have all four lights on the diagnostic panel being green. However, this is only a best guess; it could be something else!

---

### Post by Chris Edgell on 2010-02-24
Yes, CD checks out and so did the memory test.

With the "Rescue broken system" the first sticking point is about config of the network.  Then I get a red screen if I can't provide an IP address., tells me to consult my network administrator.  I can't go forward or back.

Then if I just go to "Install", the sticking point is PARTITIONS.  This is what a page says:

Partitioning a hard drive consists of dividing it to create the space needed to install your new system.  You need to choose which partitions will be used for the installation.

Select a free space to create partitions in it.

Select a device to remove all partitions in it and create a new empty partition table.

On other regular installs I was shown a "floor plan" for the selection of the partitions.  On this alt CD no choices for partitioning was ever offered.

Three options are offered but none work for me.  One is "Need help"  then the following page says:  Select a partition to remove it or to specify how it should be used.  At a bare minimum, you need one partition to contain the root of the file system (whose mount point is /).  Most people also feel that a separate swap partition is a necessity.  "Swap" is scratch space for an operating system, which allows the system to ;use disk storage as "virtual memory".

When the partition is already formatted you may choose to keep and use the existing data in the partition.  Partitions that will be used in this way are marked with "K" in the main partitioning menu.

In general you will want to format the partition with a newly created (the next page doesn't finish the sentence.)

One says enter code manually, that begins with computer language and speaks of "ash"  none of it, could I do anything with.

And now it ask for my IP address. and I can't go forward or back so I have to shut it down again.

---

### Post by k3lt01 on 2010-02-25
I have never had to configure the network during install unless it is a wired network, even then I ignore that step cause it just causes grief, lol. There is usually an option to ignore so if you can I would choose that.

As for your partitioning, forgive me I assumed the BIOS corrected itself. If the BIOS isn't seeing a hard drive you aren't going to be able to install until it does. So I would follow JKyleOKC's suggestions for fixing that issue then we can work on the install itself.

---

### Post by houseworkshy on 2010-02-25
I've only just spotted this thread.  Whilst I don't have any specific advice I do have a couple of suggestions.  There are a couple of disto's which deserve a place in your collection.   
 One is called dban;  [http://www.dban.org]("http://www.dban.org/")   This is tool for deleting hard discs.  According to the man who wrote the algorithm it probably doesn't work as far as securely deleting data is concerned but that is not why I recommend it.  It is handy for fresh starts.  I use it when utterly flummoxed to start again.  Even on it's minimum security mode it still takes a long time but when finished all drives on the machine, from the point of view of a normal user as opposed to someone working for some intelligence organisation, are clean of everything even the boot loader.  
 Another is a Linux distro called Puppy  [http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm")
 This is a tiny but full featured system.  Whilst it doesn't have all the bells and whistles of Ubuntu it is so small it can be loaded into ram and run from there.  It is also an ideal choice for old machines which have low spec's and may be the one to put on an old machine to give to your neighbours.  I use it, loaded into ram, in order to free the CD/DVD drive so I can burn data to disc from a system which is in such a mess that reinstalling is the fastest solution.  It is also very handy if one wishes to know whether a problem is software and therefore mend-able at the keyboard or hardware in which case fiddling with the software is a hiding to nothing.
 You seem to have come a long way very fast.  You are also getting advice from people who know far more than me so with a bit of luck you may never need the distros I suggest.  I only mention them because, I for one, feel a lot safer experimenting when I know that they are there in the CD rack as if all goes belly up, using Puppy, I can at least grab important data, double check hardware and  browse for advice and, after using dban, make a properly clean fresh start.
 There is an exception to the panacea of these two discs about which I recommend caution and that is bios.  I only do simple things like changing boot order because getting the settings wrong in here can physically damage your machines.  For example, don't by the way, over-clocking can fry the hardware.  So get the appropriate manuals and read up before getting into it or even trying to update it.  Bios varies hugely from machine to machine, knowing about one means that the basic principles may be understood but it doesn't tell you much more than that about another one.   
 Good luck with it all, whatever happens you are certainly making the most of having several non critical machines to play with and will learn more than you ever would with a one and only   &#8220;precious&#8221; PC.

---

### Post by Chris Edgell on 2010-02-25
Oh, houseworkshy, I'm so happy to see you...my spirits had just begin to flag, dropping down to a marshy footing...but now my spirits have lifted and the bleak feeling has vanished with your firm footing and kindly approach.  You've cheered me just in the nick of time...now I can lie down to sleep in peace tonight.

I went and read some about dban; my question is when it is wiped SO CLEAN will it simply accept any install.  (ARE the bios ON the hdd?)  I guess it's a more complicated install, to even need to install other parts and pieces, LIKE the boot loader.

I had heard some about puppy.  Do you consider it to be it's best to RUN on RAM rather than any hdd install?

Did you understand, or do you know that people say you can reset the BIOS to the default by removing the battery for half an hour?  I looked at that DELL site that Jim Kyle talked about, but how does that complex bit of work (even FINDING the "jumpers" -- I couldn't..) and why would that be necessary if the bios can be reset so easily with the battery trick.  Can you shed some light on this for me?  And WHY couldn't I reset the date...what has gone wrong with this Dell, any speculative guesses...

More later.  Thanks again.  I DO feel lucky, for all of you to be here with me.  I had just started feeling blue and THIS was the perfect pick-me-up.  And now to bed.

---

### Post by ranch hand on 2010-02-25
The bios are basically the firmware that runs your motherboard and built in there.

---

### Post by JKyleOKC on 2010-02-25
> **Chris Edgell said:**
> Did you understand, or do you know that people say you can reset the BIOS to the default by removing the battery for half an hour?  I looked at that DELL site that Jim Kyle talked about, but how does that complex bit of work (even FINDING the "jumpers" -- I couldn't..) and why would that be necessary if the bios can be reset so easily with the battery trick.From reading Dell's manual, it looks to me as if they have tried to "simplify" things by removing most of the usual options found in BIOS setup screens.

Here are the five steps, copied from the manual:
```
   1. Restart your computer.
   2. As the system restarts, press <F2> to enter system setup.
   3. When the system setup screen appears, press <Alt><F> to load the Dell default settings. 

The computer beeps when the settings are restored.

   4. Verify that the time, date, and year are correct and that the Secondary Drive 0 option is set to Auto.
   5. Press <Esc> and then press <Enter> to save your changes and exit. 


```The words surrounded by < and > are the names of the keys to press. After Step 5, the system will try to re-boot automatically.

It may be that these boxes, since they were originally used in schools, are set up to boot from a network connection. That could explain why all your attempts to boot from the hard disk insist on having such a connection. If this is what is causing your problems it may be difficult to make any progress until your friend gets back. Since the first system does work, there's bound to be a way to fix things!

The magic word "BIOS" is an acronym for "Basic Input Output System" and it's a program that's totally self-contained in a chip on the motherboard. Its purpose is to translate the very basic commands needed to boot the machine ("boot" comes from the phrase "lifting yourself by your own bootstraps" which is essentially what the system does when you turn on the switch) into the sequence of extremely arcane instructions that the hardware requires. Since nothing in RAM stays around when the power goes away, and the disk drives may not even be there, this sequence of instructions has to be stored in a way that doesn't require power -- that's the BIOS chip. However a few things, like the date, time, and hard drive specifications, have to be able to change, so there's a second chip called "CMOS memory" that BIOS stores these things in. That memory is powered by the little battery. CMOS uses extremely small amounts of power so the battery can last a long time (one of my machines ran for 14 years on its original battery). Pulling the battery lets the stored information evaporate, but that takes a while.

The Dell manual seems to tell me that the machine should go through its setup routines automagically and not require you to do anything -- but obviously that's not happening since the disk drives aren't being detected properly. This is why I now suspect that the systems have been set up to require a network connection to the school's main servers in order to complete the boot process. This can be done by adding an additional chip -- but finding and removing that chip, if one is even present, is a task I would hesitate to tackle myself so I can't recommend that you do so!

The next time you get to a screen that asks for an IP address, tell it "127.0.0.1" (without the quotes) and let us know what happens. That's the "universal" address that means "right here" and is usually called "localhost" so it just **might** tell the bootstrap program to use the local BIOS rather than the network that's not there... And let us know what happens. Every little bit of information adds up!

---

### Post by ranch hand on 2010-02-25
OT
I am downloading the Lubuntu alpha3 ISO right now and it is a whooping 380Mb if you are looking for a light OS.

Lubuntu 9.10 is still beta.

I think the 10.04 is better and it will not be long now until the release anyway.

---

### Post by Rex Bouwense on 2010-02-25
Chris, if you have a real old machine, then Puppy Linux is an excellent candidate.  I would install to the hard drive then you don't have to worry about having a large enough flash drive to keep your data on.  I installed puppy on an old Dell 1000 initially but now I have it on a 4 Gb flash drive.  Go ahead and download it.  It is really tiny.  All it costs is a little time.  Enjoy.

---

### Post by egalvan on 2010-02-25
> **Chris Edgell said:**
> I have 4 computers...
original yard sale special, 
3 Optiplex GX260 Dells.

I've been (trying) to follow your threads since our disastrous start...

You state that these are Dell machines, so

THERE IS **NOTHING** YOU CAN DO IN THE BIOS TO DAMAGE THE HARDWARE.

Mess up the software, yes, but NOT the hardware.

I've cycled *at least* 20 of these GX260's through my shop...
they are physically cleaned ( compressed air @ 60psi )
drives are wiped with dban (Darik's Boot And Nuke)
tested
some sort of *nix installed,
and donated to indigent students (in Mexico)
( I've also done *many* GX240's, a few GX270's, along with even older GX1's and GX100's.

dban is good enough to wipe a drive so as to foil normal recovery/forensic analysis.
(it's theoretically possible that SEM-based analysis of depletion zones can recover something :)
 If you need to ask "what is that? then you are probably* not *in the target range of these tools :) )

> I would try to concentrate on one at a time.
  But that was the one the install failed and I was going to try to swap hds but then decided to make sure the hd was working on this one.


It is always best to concentrate on one problem at a time.
Find a base-line you can work from ( a KNOWN-GOOD set of hardware )


p.s.
if you can tell me the EXACT model of GX260 you have, maybe I can see if I have one on my bench, and maybe I can tell you the EXACT steps needed to set up the BIOS.

---

### Post by Chris Edgell on 2010-02-26
I am trying to collect my thoughts, and to communicate with all of you what is going on here.

The primary computer (a Dell) is fine.

The AMD is sitting without sound, and I'm leaving that until I HAVE to work on that problem because I CAN'T STAND another minute with these two broken Dells.

I must say that it was Dell #2 that something happened that the HD could no longer be detected.  We, here, have been focusing on resetting the BIOS so as to detect the HD.

egalvan, thank you for coming in here, I appreciate your apparent acceptance of some of my weaknesses, not the least of which is a very verbal (if not verbose) explanation of my situation.  Due to your influence, I HAVE tried to edit my digressions; I've tried to focus on being as specific as I can; as you see, it's still wordy.  Many speak in code but I don't really know code.  Sad as it may be, I am one of the ABSOLUTE Beginners that you will attract as you spread the word...Ubuntu.

To you:  you have asked me to be more specific about what Dell gx260 I have.   Is this what you want, it's as comprehensive as I can find to tell you.  If there's more, please tell me where to find it.  Also, I was very glad to know that I wouldn't have ruined the hardware, but the software..there in the bios.  I wonder if I ruined the hardwear with too many hard shut downs and reboots...and too fast.  That's a possibility isn't it?  What then? Or do we cross that bridge when we get there?

Dell Optiplex gx260 Series  Intel Pentium 4 Processor 2.00 GHz level 2 cache: 512 KB Integrated  BIOS Version A09 Service tag 9LHWXII

I'll leave it at this and again thank you all.  Each of you almost becomes dear to me, if you don't mind me sayin'; like blood brothers and sisters, you're in my heart.

(I have done lots more but it would be so time consuming to go into it now and I just can't.  But, Jim, I will say, I've looked and looked, even with my magnifying glass -- and I have no idea where or WHAT a jumper is or looks like.)

---

### Post by egalvan on 2010-02-27
> **Chris Edgell said:**
> I am trying to collect my thoughts, and to communicate with all of you what is going on here.

yes, most definitely... slow down, collect thoughts, focus.

Calm. Like Jedi Master you be, like Yoda.


>  I was very glad to know that I wouldn't have ruined the hardware, but the software..there in the bios. 
**I wonder if I ruined the hardwear with too many hard shut downs and reboots...and too fast.  That's a possibility isn't it?**

NO, it's NOT a possibility.
*maybe, perhaps*, if you punched the power button as fast as you can, for a couple of minutes....
or did a John Henry with a nine-pound hammer...
*maybe*
otherwise, please forget it.

> 
Dell Optiplex gx260 Series
  Intel Pentium 4 Processor 2.00 GHz level 2 cache: 512 KB Integrated
  BIOS Version A09
 [COLOR="Red"]Service tag 9LHWXII[/COLOR]

(nice machine, BTW)

lots of models in the GX260  line... the Service Tag will specify the *exact* model, which is what I'm after...

but, Dell stays that [COLOR="Red"]9LHWXII[/COLOR] is not a valid service tag.
Please double-check the letters and numbers...
note that the Service Tag should be showing up on the bottom of the first BIOS screen...

(you also have the most recent BIOS, which is "a good thing")

>  even with my magnifying glass -- and I have no idea where or WHAT a jumper is or looks like.)

let's forget those jumpers for now... if you have no idea what they are, or what they look like, it's highly unlikely you moved them....
so forget them for the moment.

---

### Post by Chris Edgell on 2010-02-27
Okay, -This one is 519Y521

I am now wondering if the real problem is that both of the "broken" machines have their clocks stopped in Nov. of 2004.  I was told to reset the clock to press Alt + F, but it does nothing.

Could it be the battery?

---

### Post by JKyleOKC on 2010-02-27
> **Chris Edgell said:**
> Could it be the battery?That's a distinct possibility, but if the batteries in both machines are dead I would expect the date to be stuck on January 1, 1980 (which is represented internally by all-zero bytes, and is what most older BIOSes show in such a case).

I'll back away a bit since egalvan knows these specific machines quite well, while I don't think I've ever even seen one. I'll still be following the thread, but I'll be pretty quiet so far as suggestions go. Too many cooks can spoil the broth and all that...

---

### Post by ranch hand on 2010-02-27
> **jkyleokc said:**
> 
i'll back away a bit since egalvan knows these specific machines quite well, while i don't think i've ever even seen one. I'll still be following the thread, but i'll be pretty quiet so far as suggestions go. Too many cooks can spoil the broth and all that...
+1

---

### Post by Chris Edgell on 2010-02-27
Okay, I got carried away with the idea that my salvation would be to just get a new battery.

You may snort to learn that the battery is okay...I was so busy with trying to get the right date and time that I forgot to notice that the seconds ARE ticking away even though the details are "wrong".  So, the battery works.

See. egalvan has put the fear of God into me..I WILL focus, I will edit before I post; I will stop the gonzo approach and think through the best way to say it.  (Well, right after this post.)  Today is my Birthday, I have achieved the completion of 66 years of this very interesting life, and it's time to act like an adult.  I'm kidding.  

Seriously, though, I'm going to be better; this new year of my life.

---

### Post by ranch hand on 2010-02-27
You do need to be careful about getting carried away.  There is no call for this "acting like an adult" stuff.  It is a bad idea.

Have a happy one and remember that you are a whole day older than you were yesterday.

---

### Post by JKyleOKC on 2010-02-27
> **Chris Edgell said:**
> Today is my Birthday, I have achieved the completion of 66 years of this very interesting life, and it's time to act like an adult.Hey, happy birthday! In just a couple more weeks (St. Paddy's Day to be exact) I'll start my 80th year but mentally I'm still a teen-ager...

Acting like an adult is for the birds!

---

### Post by Sir Jasper on 2010-02-27
Hi,

A Very Happy Birthday. I assume you´re kidding about the 66 bit and I&#7743; sure we all wish you well in your new acting career.

---

### Post by Chris Edgell on 2010-02-27
You all have made me feel so good.  And Sir Jasper, you really made me laugh!

Time...what can we say...they say we have our signature year and the mind sits in that frame until stirred by, like, a mirror... smile.  My signature year is I'm 29 in 1973.. it reminds me of that Biblical phrase, "In the fullness of time..." that WAS then, and this IS now and, well, I'm glad I'm still here.  And I'm glad you're here too...

Cheers
Chris

---

### Post by raymondh on 2010-02-27
happy birthday, Christine.

Raymond

---

### Post by Chris Edgell on 2010-02-27
Oh, hi Raymond.  Thank you.  Are you following this thread?  I can hardly wait to talk to the friend who gave me these Dells, and set up the first one.

That first one I put an OS into was so flawless; I thought I had it made.  (I SAY flawless, but I failed to mention, there is NO SOUND.  But for the rest, it just went in and worked...these two are another story...nothing but trouble.  Now I know that one of my first mistakes was not realizing that I was working with only 256mb of RAM.  This time I'm learning the hard way.

---

### Post by -kg- on 2010-02-28
Hi Chris, and Happy Birthday!  Mine was just a few days ago (58 years young).

I've just read through this thread, and I'm a bit surprised that no one thought of this.  If you think you might be having problems with your hard drive (or BIOS recognizing it), try this:

Boot to the Live CD, open a terminal window, and enter (or copy and paste) the following:

```
sudo fdisk -l
```

If typing, the last letter is a lower-case "L".  If all is well this command will list the partitions present on your hard drive.  Paste the results here.  Following is the results of the command on my computer:

> Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6bba44a8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2             192        9409    74033152    7  HPFS/NTFS
/dev/sda3            9409       10531     9020081+   7  HPFS/NTFS
/dev/sda4           10532       12161    13092975    5  Extended
/dev/sda5   *       10532       12161    13092864   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5d379805

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14593   117218241    f  W95 Ext'd (LBA)
/dev/sdb5               1        2439    19585012    7  HPFS/NTFS
/dev/sdb6            2440        5652    25808391    7  HPFS/NTFS
/dev/sdb7           14193       14593     3221001   82  Linux swap / Solaris
/dev/sdb8            5653        6868     9767488+  83  Linux
/dev/sdb9            6869        8692    14651248+  83  Linux
/dev/sdb10           8693        8719      216846   83  Linux
/dev/sdb11           8721       11343    21069216   83  Linux

Partition table entries are not in disk order


As can be seen, I have two physical hard drives in this laptop; "sda" and "sdb."  I have Windows Vista and three different distributions of Linux (Ubuntu, Fedora, and OpenSUSE) installed in different partitions.  Your results will not look like mine, but you should minimally have 2 partitions.  If you have anything different (like no partitions listed, or an error message), then you can be sure that you are indeed having hard drive issues.

If all is well with the drive, you might want to read at the "How To Partition" link in my signature block.  It might help you in understanding hard drive partitioning and save you some grief in your endeavours.  If you have more than 2 partitions, then we should be able to help you from that point.

Cheers! ):P

---

### Post by ranch hand on 2010-02-28
-kg- and Chris
All the good ones are born in Feb.

No self interest in that statement.  My 58th was the 8th.

---

### Post by -kg- on 2010-02-28
> **ranch hand said:**
> -kg- and Chris
All the good ones are born in Feb.

No self interest in that statement.  My 58th was the 8th.

But of course!  [IMG]http://www.freesmileys.org/smileys/smiley-laughing002.gif[/IMG]

---

### Post by Chris Edgell on 2010-03-03
Hi,

Sunday I talked to the guy who gave me the computers; he told me there was nothing special that he did for the setup on that first Dell.  That gave me hope, (as did the words of egalvan).

Just Saturday I got one 512 stick of RAM, so both of the "broken" machines have enough RAM; I also picked up a nice Dell CRT monitor for $10.  That put me with Dell 1,2, &3 all set up in a row.  I went into the BIOS of all three and went through a total comparison.  I learned A LOT there, not the least of which was in seeing them all in a row I noticed that #1, the working machine had 3 check marks next to the three positions in the boot order.  The others had only one or two checks; I saw how to place those checks by pressing space for "change" -- and realized that this was the reason I had not been able to boot up to the liveCD somewhere along the way.  I was remiss in not noticing such a thing until they were all in a row.  (It's like when my sound wasn't working because of a mute button...just the simpliest thing...)

I burned another Alt CD since it had worked so well seeing the two machines side by side.  I had focused on machine #3 because IT detected it's hard drive...but in the many hours of working the "Rescue a broken system"...it would always hang up.  But I had to study partitions, drivers, IP address, I found a guide that showed me different things to enter into the "BusyBox"  I struggled with GRUB (and ultimately that's where #3 stalled...I can't seem to get the GRUB for the boot).

 As I began systematically going through the boot menu and the liveCD menu, I noticed that the difference in the boot menus is that the #2 didn't even offer the option of booting from the hard disk drive and I was inspired to go into the machine and press all the connections of that HD -- this is the embarrassing part -- then the machine detected the hard drive.  I then installed the Alt CD and downloaded the updates.  I added the restricted extras and the SunJava package and -- voila -- I EVEN have SOUND.

It's awfully like not plugging in your vacuum cleaner...(or not noticing the clock IS running) but don't be too disappointed with me.  I learned so much.  Thank you for all your help with this.  NOW I plan to keep a log of what I'm doing.  (I DID so many things 8 or 10 times before I got systematic about it)  I AM going to focus AND meditate, egalvan!  You do cut through what I gotta' call my crappy thinking and excessive verbiage.

Thank you, thank you, thank you!  I have put in no less than 40 hours on this analysis since Saturday.  As I reread the thread, I had tried many of the things you talked about...the memory checks etc, audiomike; then too Sir Jasper who encouraged me to keep the thread going...that did provide a lot of support through time.  I liked the participation of k3lt01, who suggested the Alt CD by which I learned a world of stuff with the "Rescue Broken System"  (you too Jeff).  Ranch hand for partition talk and big thanks to JimKyle for turning me on to the Manual at Dell diagnostics--for all of the Dell support stuff was great.  To houseworkshy, I'll be using puppy or dban one of these days.  Pirate, Rex, raymond, kg, thank you all.

Shall I close this thread because I've got one out of three...I reread it and it's nearly excruciating; and these admissions are excruciating too.  But then again, I'm so happy!

---

### Post by JKyleOKC on 2010-03-03
Hey, you did great! That idea of lining up all three side by side and comparing setup screens was a very good one, and you came up with it on your own. Congratulations.

I suspect you don't really realize yet just how very much you HAVE learned during this experience. A month ago I doubt that you would have thought of comparing the three, or even two of the three. And comparing a non-working system to one that's known to be good is the very best way to do troubleshooting.

Loose connections are possibly the most common cause of problems, not just for hard drives but for everything in the computer. That might even be why your "good" computer doesn't have sound, but if #2 is now working and does have sound then I wouldn't open up the good one just yet. Wait until #3 is working as well.

And I wouldn't close the thread yet, either. It has the full history of how you got to this point, so it may help you find out why grub isn't working properly on #3...

---

### Post by k3lt01 on 2010-03-03
Chris I agree totally with Jim, you will realise that you have learned more in this process than you think you learned. Without trying to sound confusing the process of learning how to learn is different for everyone, you have found how you learn.

Congratulations and never forget 2 simple things. 1. Asking for help is a good thing, 2. Remember to "Pay it forward".

---

### Post by Sir Jasper on 2010-03-03
Hi,

Well done.

My regards

---

### Post by raymondh on 2010-03-03
as well ..... =D>

Raymond

---

### Post by presence1960 on 2010-03-03
Great job Chris. I really believe if nothing ever goes wrong I never learn.

---

### Post by egalvan on 2010-03-03
> **JKyleOKC said:**
> That's a distinct possibility, but if the batteries in both machines are dead I would expect the date to be stuck on January 1, 1980 (which is represented internally by all-zero bytes, and** is what most older BIOSes show in such a case**).

Yes, quite true, but these Dell are not that old....
they default to a "younger" date...

Chris, are you ***sure*** the battery is good?
if the clock is reseting, it points almighty hard to a bad battery...
Yes, it *could* be a bad RTC chip, but I like to think "horses" when I hear hoofbeats, not "zebras"...
Are *any* other options being reset?
Try changing something else, such as floppy being present...
I wager you'll find some other options changing....
And since those 2032 cells are only some $4 for a two-pack, it may be cheaper than therapy...

> 
I'll back away a bit since egalvan knows these specific machines quite well, while I don't think I've ever even seen one. I'll still be following the thread, but I'll be pretty quiet so far as suggestions go. **Too many cooks can spoil the broth** and all that...

Yes, I have a fair bit in their direction...
good little machines they are.

And it's the stew that can spoil :)


Chris, sorry for the delay between my posts...
my shifts are 24-48 hours, and my fiance's family has had medical problems the last two weeks (including a death), and my car has left me stranded four time in the last 12 hours...

Add to that, I'm trying to snag some re-possessed property from a holding company (for 25% of value) before someone wises up to the problems that are not problems,

and studying for a promotional exam at the fire house...

My time is seriously compromised...

but I did get two more Dell GX260's out the door with Linux on them...
so some victory to hand.

Once more unto the breach, and fie on him who first cries "hold, enough"

---

### Post by egalvan on 2010-03-03
> **JKyleOKC said:**
> 
Loose connections are possibly the most common cause of problems, not just for hard drives but for everything in the computer. That might even be why your "good" computer doesn't have sound, but if #2 is now working and does have sound then I wouldn't open up the good one just yet. Wait until #3 is working as well.



Dimes to doughnuts the connection wasn't "loose"....
it was more likely oxidized... and "wriggling it" (a highly technical term most unknown to mere mortals), or even better, disconnecting and reconnecting, is something most techs do as a matter of course in older machines. 
Sorry I didn't get around to mentioning it, along with a thorough cleaning with compressed air. My bad.

---

### Post by egalvan on 2010-03-03
Chris, don't give up, and don't put yourself down for "not knowing" things...

Forty years ago I knew that a bit was something that went into a horses mouth, and a bite was what you took out of an apple...
( OK, I was raised on a farm, in a barn :) )


And now look at me... well, better not...


Anyway, we *all* had to learn to crawl, and walk, and run.

**nobody** was born knowing everything (although I mind a laddy a couple of millenium ago)...

Please stop putting yourself down.

You have the most important attribute needed for learning...

the **desire** to learn

---

### Post by k3lt01 on 2010-03-04
> **egalvan said:**
>  but I like to think "horses" when I hear hoofbeats, not "zebras"...Say what?

Don't you think that these multiple postings could do more to confuse the issue at hand than to .........

---

### Post by ranch hand on 2010-03-05
If you are still having problems with grub on one of those boxes give a post on on it here.

I am, and I am sure others here are too, pretty good at dealing with grub.  If you are using the new grub (grub1.96 through 1.98) as opposed to grub0.97 you really should read the first post in link in my sig.  The second link I provide there is the best in depth info you will find anywhere.

I just got back from a trip to the big city for 4 days and am relieved to be back.

---

### Post by Chris Edgell on 2010-03-08
ranch hand,

It was real nice of you to offer to help me with grub; I read your post and quite a lot of leads offered on the subject and understand next to nothing.  I'm thinking of reading it all one more time and see if any of it begins to make some sense to me.

In the meantime, I had put that Dell #3 aside and got Dell #2 up and running and now had 2 good machines for comparisons.

The other machine I went to work on is the AMD that I started with before the Dells.  I had gotten the Xubuntu downloaded in there and all seemed great -- but no sound.  As I got back to it, I did everything I could, but all to no avail.  Next I decided to install the Alt CD so that I could match up the synaptic to cover any sound deficiencies in the app and pkgs.  After a couple of approaches I realized that the only way I could do it was to use the one by one approach -- there are like 26,000 possibles and there were 1122 downloads on the computer WITH sound.  THAT took some time!  After all, there was no sound.  

I went over that very comprehensive sound troubleshooting "document" but didn't want to start it without some expert guidance, well because I have Jaunty 9.04 and that seems to predate the troubleshooting pages in that they seem to indicate that between Jaunty and Karmic there was the transition to Pulseaudio.  I didn't want to start installing stuff that would find NO agreement with my two working machines.  

I also discovered how in the Dells that the soundcard is built into the motherboard (is this not so?); whereas in the AMD the soundcard stands alone.  Shall I consider getting another soundcard or someone else mentioned a PCI card for the available slot.  (I then began to read about buses and all that).

Can someone point me in the right direction with this AMD?  I am more interested in it than ever since I finally found out that the Dells are 20GB hard drives and the AMD is 80GB.  That would give me a lot of space to play around in.

---

### Post by ranch hand on 2010-03-08
So, do  I have this right, you want to get sound on the AMD box?  Did you ever look at the results of;
```

lspci

```
?

That will give you all the devices like the sound and video card or controller (usually listed as a controller if integrated in your mother board).

You could copy paste the results here of the whole thing or just the sound card and then we would have something to go on.

I am on my 10.04-testing drive again this morning and the sound on it is improved over 9.04 quite a bit.   I know some folks had a hard time with 9.10 but I did not.  Old Sound Blaster (SB) cards are all over the place and fairly inexpensive.  I recommend the Audigy1 card by SB.  May also be listed as Creative Labs.  These seem to just love Linux in general.

---

### Post by Chris Edgell on 2010-03-08
chris@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 14)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:0b.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0c.0 Communication controller: 3Com Corp, Modem Division WinModem
00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Non-VGA unclassified device: VIA Technologies, Inc. VT8235 ACPI (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
chris@ubuntu:~$ 

Hi, great, here it is.  (I have an appt, be back later)

---

### Post by ranch hand on 2010-03-08
Looking at your "lspci" output I do not see any sound device.  This could be the problem.

I would take the cover off and take a look.  If there is a card in there it may just have a bad connection.  Pulling it and putting it back a couple times may fix that.  TURN THE BOX OFF  and unplug it to do this.

If you have external speakers connected to it there is a sound card.  We need to find out why it is not being detected.

You may want this;
[COLOR=#000000][http://www.bcom.de/ftp/treiber/Asus/Hanb%FCcher/a7m266-104.pdf]("http://www.bcom.de/ftp/treiber/Asus/Hanb%FCcher/a7m266-104.pdf")

That is the manual for your mother board and shows the layout and what comes with it standard and so forth.

Has numbers pointing to parts.  Very nice if you have  not fooled around inside there much.
[/COLOR]

---

### Post by howefield on 2010-03-08
> **ranch hand said:**
> Looking at your "lspci" output I do not see any sound device.

C-Media Electronics Inc CM8738

---

### Post by ranch hand on 2010-03-08
Good God I am blind.

It is a good thing there are folks to straighten me out.

Check this
[http://ubuntuforums.org/showthread.php?t=902747](http://ubuntuforums.org/showthread.php?t=902747)

[http://ubuntuforums.org/showthread.php?t=932250](http://ubuntuforums.org/showthread.php?t=932250)

[http://www.linuxquestions.org/questions/ubuntu-63/no-sound-ubuntu-9.04-x64-desktop...-742607/](http://www.linuxquestions.org/questions/ubuntu-63/no-sound-ubuntu-9.04-x64-desktop...-742607/)

---

### Post by Chris Edgell on 2010-03-08
I DO appreciate all these links, but, correct me if I have overlooked one, they ALL seem to include pulseaudio.

It doesn't seem like I would have to "reconfigure" (if that is the correct term) all the apps to include Pulseaudio (especially if I'm not upgrading to Karmic) if the sound card is being detected...and if everything matches in synaptics to a machine that has sound.

Does this PROVE that the sound card needs to be replaced?

If it does NOT prove...well I'll have to rethink about following the advice on all these troubleshooting posts and documents that INCLUDE Pulseaudio.

Is there a simple test for sound?

Is there anything in BIOS that could or would be preventing the sound?  The BIOS setup for this AMD is very different from the BIOS of the Dells.

---

### Post by nikef on 2010-03-08
Hi Chris 

I would just like to say that you are doing a great job there with those computers and helping your retired neighbours out .
I am so sorry i can not offer you any help and i wish you every success in completing your tasks :o
I have enjoyed reading the posts and will continue to do so.

Trish

---

### Post by ranch hand on 2010-03-08
You have pulse audio.  It has been in there for some time.  If you notice the newest (unless I am still blind) version in there is 9.04.

I would recommend installing gnome-alsamixer as it has given me better service than alsamixer.  It will show up in your Applications>Sound&Video menu.  There are a lot of options in the preferences menu on it and it is easy to jigger with them to get things working.

I have surround sound and use it to control the tone and balance.  I added the launcher to my panel (right click on menu item and select "Add this launcher to panel").  Make sure that the "switch" for digital output is not checked (makes a very nasty noise - was enabled by default up to 9.04).

Make sure you check your bios to make sure there is no place in there that needs enabled for your card.  From the little I read there is no integrated sound so there may or may not be an entry for that.  On my box, for instance, there is an intel sound chip integrated that needs turned off to allow my card to work.

I mention my box as it is a Dell and you may run into this on those other boxes.  The sound on this box was terrible with that running through the included speakers.  Like an early pocket transistor radio.

---

### Post by Chris Edgell on 2010-03-08
Well, when I go to synaptics it does not show pulseaudio to be installed, by default or otherwise.

Can anyone clarify this discrepancy?

---

### Post by ranch hand on 2010-03-08
Just for you I popped over here to my Jaunty install.  Here is the result of running apt-get;
```

jak@jak-desktop:~$ sudo apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
jak@jak-desktop:~

```
I admit that this is a respin of Jaunty and does have some extras added so I chrooted into my straight up Ubuntu Jaunty install and ran the same command;
```

 root@jak-desktop:/# apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 27 not upgraded.
root@jak-desktop:/# 

```
You are using Xubuntu and the only install I have using Xfce is Zenix which is built from Ubuntu minimal.  It is also 9.10.

I will edit this in a moment when I get back to the test platform and check an install of 8.04.

---

### Post by Chris Edgell on 2010-03-08
"Just for you..."  I like that.

In fact, I am using Alt CD XUbuntu.  Does that explain the discrepancy?

Thanks for continuing here with me at all...

(Is that app-get the best way to find out what's in there already?)

IS there a list of the pkgs included in each release?

---

### Post by ranch hand on 2010-03-08
Here is the result of the same command from a chroot into my old stand by Ubuntu 8.04;
```

root@sam-desktop:/# apt-get install pulseaudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pulseaudio is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-26-generic linux-headers-2.6.24-26
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@sam-desktop:/# 

```I am not sure.  I am not a big Xubuntu fan as it is not any lighter than gnome (Ubuntu) really, thunar is number three on my list of file managers (I like nautilus best and then pcmanfm that is with Lubuntu), I like the panel and menu lay out in gnome.  So I am kind of ignorant when it comes to Xubuntu.

I think that the base system, though, is the same and should have pulseaudio on it.

Do you have a live CD that will run on your AMD box?  If so I would fire it up and check to see if pulseaudio is on it.  Synaptic would show it in the live session.

Edit

I did a fast serch on pulse and xubuntu and did come up wit hone thread for Jaunty that seemed to infer that it had to be installed on xubuntu to use it.

I would not do that if the gnome-alsamixer will get your sound going.  My card is supported by alsa and not really by pulse (old card).  I would try that before doing any thing radical.

---

### Post by Chris Edgell on 2010-03-08
A live CD of what, which, I have a few here?

Forgive my specific density, please.

Oh, I just read the edit...now let me think.  (Thanks)

Oh, I already have alsamixer...that's part of what works with these two working Dells.  Not that I know if Gnome alsamixer is different from the one that I have.

---

### Post by ranch hand on 2010-03-08
> **Chris Edgell said:**
> A live CD of what, which, I have a few here?

Forgive my specific density, please.
Sorry, I figured we were talking about Xubuntu 9.04 which is what I thought you installed on the box in question.

If you installed something else I would use the Live CD that matches what you installed and see what it has on it.

I really do not think that you should need it though if you have all the alsa stuff installed.  The gnome-alsamixer is easier to use and looks better than the (plain default) alsamixer which is why I use it and recommend it.  It is just better all around.  I do not think it will drag in a lot of dependencies.

---

### Post by Chris Edgell on 2010-03-08
Well, we've come full circle since posts 86 and 87.

So my two questions still push for answers;  

1) Is there a way to hear sound, as a test, without installing Pulseaudio? 

2) Are there any ideas besides a new sound card?

---

### Post by ranch hand on 2010-03-08
Did you try gnome-alsamixer and check your bios settings?

---

### Post by Chris Edgell on 2010-03-08
Sorry, I have written and rewritten, posted and not posted, that I see I did NOT tell you that I installed Gnome-alsamixer.

What WOULD I be looking at in the BIOS for checking my settings?  I'll go look...when you say where to look and what to look at.  As I've said they are very different in this machine than in the Dells.

Thank you.

I am going to install the Gnome-alsamixer on the Dell that HAS sound (and Alt CD,) and see how that goes.

---

### Post by ranch hand on 2010-03-08
I am not familiar with the bios on that mother board.  This is true of most mother boards come to think about it.

However, they have to have some things and others are kind of optional.  Dell for instance really doesn't give you enough control over how your box runs (in my opinion).

I would just go in and look at everything.  This will give you some knowledge of what is in there anyway.  Look for anything to do with audio or sound.  From the little that I looked at the manual for your mother board, audio is optional and needs a pci card as there is no on board sound controller.

Due to that, I would check to see if there is anything you need to do to enable the card.  In my bios on this box it was just needed to disable the on board sound.

You have never said, or I didn't see, what kind of speaker system you have.  Does it plug in with its own power or is it just powered by the card?  Do you know that the speakers work?

I know that I have fought with something that I was blaming on x only to find that y didn't work.

---

### Post by audiomick on 2010-03-08
Hi Chris, great to see that you are making progress.
I was just having the same thoughts as Ranch Hand. Make sure the speakers work before you assume that you have a software problem. I don't know how many times I have spent ages with my colleagues looking for the problem in the digital mixing desk, only to discover that a cable wasn't plugged in...

Things to check include
Have the speakers got power? If they are built in to the monitor, you can assume they have got power, but not that they work.

Is the the cable ok? The most common fault with sound is a broken cable. The moulded plugs on most domestic cables are destined to break sooner or later. You can check this by connecting the speakers on the machine with sound with the cable from the computer that has no sound.

Do the speakers work if you plug them into a source that is known to be good? Plug them into the computer that has sound to check this.

Do speakers that are known to work produce sound on this machine? You can use the speakers from the other computer to check this?

Are the speakers plugged into the right connector? The sound output socket usually has a green ring around it.

There is a small possibility that the sound card doesn't work in linux, though I think this isn't very likely. I haven't heard of the brand before, but that doesn't mean much.

I gather you are talking about the Junk Yard Dog? i.e an older machine about whose previous life you do not really know too much?
The point that egalvan made about oxidised connections applies to sound as well. If you can work out which card is the sound card, try very carefully wiggling it, or pull it out and put it back in, to freshen up the connection. Turn the computer off and remove the power cable before you do this. You will probably have to remove a screw to be able to unplug it.

---

### Post by k3lt01 on 2010-03-08
> **Chris Edgell said:**
> 1) Is there a way to hear sound, as a test, without installing Pulseaudio? In Ubuntu you can go System > Administration > System Testing. That tests everything on your system. I am not sure if that is available on Xubuntu or whatever it is you have installed.

---

### Post by Chris Edgell on 2010-03-09
Thanks Trish, I appreciate you comments.

Hi Audiomick,  Simply put, the speakers work -- but I don't mind you covering all the bases here; it is the kind of point where I could go wrong.  I must say I have downloaded the 102 page manual for, yes, the AMD aka JYD.  You did read, didn't you that it's gone up in my estimation since discovering the 80GB hard drive.  Especially after all the confusion and finally finding out that these Dells have 20GB hard drives...so now I'm talkin' sweet to this Junk Yard Dog.

I am beginning to think that the XUbuntu on the ALT CD is the same regular XUbuntu and the difference with the Alt CD is the tests it offers and the final option, Rescue Broken System.  Am I right?  Also I'm kinda' looking for the thread that talked about whether XUbuntu is a savings of resources as compared to Ubuntu, OR NOT.  I remember the thread was good, but I can't remember where to find that analytical post.  

It's been a long, hard day...but nice to see you all.  It's feeling like Spring in Chicago, well, if you remember that we've had long, chilly springs for the last few years...which is to say it was 46 degrees out there, and it felt good.

Oh, that's not on my system k3.

More some other time...no doubt tomorrow.  LOL
Chris

---

### Post by ranch hand on 2010-03-09
I installed Xubuntu and Ubuntu on the same drive once to see what the difference was.  did not amount to much as far as space used (about 500Mb) and no difference on this box as far as CPU usage.

If you think about it the fact that folks argue about it is a pretty good indication that there is little or no difference.  There are OS' out there that are little.

Zenix is nice and it is small.  I see that you know bohdi.zazen.  He is, I believe, the main source behind Zenix.  He is also a Montana dweller (other end of the state).  It is the OS I now use to show off Xfce.

I have Ubuntu running on a box as old as you are using, with 512ram (had 128) and a 10Gb HDD.  Not much space but we use it for email and browsing mainly and if we need to store something we have this box that I am on with five 320Gb HDDs.  Your boxes with 20Gb drives are plenty to run Ubuntu with an easier to use, I think, desktop environment for the, possibly, hard of learning folks that may end up with them.

If you wait for the meddle or end of May, 10.04 will be out and the Lubuntu release is looking better all the time.  It is more stable than Ubuntu right now and Ubuntu is pretty stable for an Alpha.  10.04 is going to be a very nice release and I think it is going to work well with all sorts of hardware.

You are correct in thinking the OS is the same on the alt CD.  The alt CD will install on boxes that folks can't get the LiveCD to work on, not sure why.  You do have a little more opportunity to customize the installation (leave things out - add things).  I like the Live CD a little better but it does not have the automated rescue help of the Alt.  I like being able to be on line to find info if I need it to do the repairs myself and that takes the Live CD (some folks learn by doing- I learn by breaking and fixing).

You need to tell me exactly what it is you are using on these boxes.  I will get a copy of the ISO and install it on my secondary test platform.  I will be better able to see what controls you have to work with on the OS that way.  I think you are using Xubuntu 9.04, is that right?

---

### Post by k3lt01 on 2010-03-09
> **Chris Edgell said:**
> Oh, that's not on my system k3.
```
sudo apt-get install checkbox checkbox-gtk gksu python-gtk2 python-glade2 debconf python python-central udev
``` should help you to install it.

---

### Post by Chris Edgell on 2010-03-09
Now, k3, can I just copy this and paste it into the terminal?

---

### Post by k3lt01 on 2010-03-09
Sure can Chris.

---

### Post by J V on 2010-03-09
Methinks that somewhere along the 12 pages this went off-topic, a new thread would help everyone help you better :)

---

### Post by k3lt01 on 2010-03-09
> **J V said:**
> Methinks that somewhere along the 12 pages this went off-topic, a new thread would help everyone help you better :) Possibly, possibly not. Most of us have been here with Chris on this problem (machine(s) not issue) for the time this thread has been going, so we kind of know where we are up to in helping Chris work through it. Normally I would agree with this but not this time.

---

### Post by Chris Edgell on 2010-03-09
k3:  

I did get that checkbox "toolbox".  NO sound was heard on the test.  What a LONG analysis was issued.    

Below I copied two sections that were printed about my system.  Maybe someone will be able to glean something that will give a clue about my lack of sound.  If this kind of stuff is basically meaningless for my purpose, just say so.  I don't want to waste time with it if that's the case.

I was also shocked at the extremely long list of blacklisted apps and/or whatever they were.....




```
[CODE]00:0e.0 Multimedia audio controller [0401]: C-Media Electronics Inc CM8738 [13f6:0111] (rev 10)
	Subsystem: C-Media Electronics Inc CM8738 [13f6:0111]
	Control: I/O+ Mem- BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
	Latency: 32 (500ns min, 6000ns max)
	Interrupt: pin A routed to IRQ 5
	Region 0: I/O ports at c800 [size=256]
	Capabilities: <access denied>
	Kernel driver in use: C-Media PCI
	Kernel modules: snd-cmipci

And later on:

/etc/modprobe.d/alsa-base.conf

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```[/CODE]

---

### Post by k3lt01 on 2010-03-09
```
Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
``` This line suggests you may have inadvertently aborted the tests.

The blacklistings just tell us that their are some drivers (I think) blacklisted so they do not affect how the system works, in other words they are not used.

I would suggest at this time you may want to google Ubuntu C-Media CM8738 and see what it comes up with or do a search on the forum using C-Media CM8738.

---

### Post by Chris Edgell on 2010-03-09
My real question is:  Did you give me this site for the mere and simple reason of giving me a sound test?  Did you ever mean for me or anyone else to analyze this information?  Do you and/or others think this huge issue is of any real value; or conversely, do you think having this "all out there" somewhere is of any detriment?

---

### Post by ranch hand on 2010-03-09
I would like to see the complete read out.  This is a new diagnostic tool to me and it looks pretty good.

The one bug mentioned seems like it should be resolved by now but there may be other things that we have not seen that would be helpful.

As to having it all "out there", I do not think that there is going to be anything that would compromise your box.  Nothing should come up that is not general to that card and mother board.  Therefore it would be open knowledge to folks that want to know it.  Even so I think it would be awful hard to compromise a box by way of the sound card.

One thing that needs to be considered in security concerns is how much effort your box is worth to get into.  This is an old box that is being set up for casual usage.  Who, pray tell, wants to invest the effort and time to compromise it.

Another thing to consider is how much help the information may be worth in terms of getting the sound to work.

I would just throw caution to the wind on this one and put it "out there".

---

### Post by JKyleOKC on 2010-03-09
> **ranch hand said:**
> One thing that needs to be considered in security concerns is how much effort your box is worth to get into.  This is an old box that is being set up for casual usage.  Who, pray tell, wants to invest the effort and time to compromise it.While I concur with your recommendations, I need to point out that any box no matter how old that's connected to the Internet is a prime candidate for being involuntarily recruited into a botnet, which can then be used to send spam, store child porn, or launch distributed denial of service attacks.

I had this brought sharply home to me within the past week. I got a strange Email from one of my regular correspondents (who maintains a department in the association magazine that I edit) and it contained a link to an address that ended in ".cn" which is the country suffix for China. That raised my hackles so I messaged Norma to ask whether she had sent it to me; she had not. I had her do a full scan of her system for malware, and it came up clean. However by the time the scans had finished she had received messages from several other people listed in her address book. One had received a Viagra ad, others had mysterious links similar to the one I got!

The rule these days, of course, is to never click on a link in any Email message unless it comes from a trusted source and you confirm that the source did, in fact, send it to you. It's extremely easy to fake the "from" address in Email, so it cannot be trusted!

---

### Post by ranch hand on 2010-03-09
> **JKyleOKC said:**
> While I concur with your recommendations, I need to point out that any box no matter how old that's connected to the Internet is a prime candidate for being involuntarily recruited into a botnet, which can then be used to send spam, store child porn, or launch distributed denial of service attacks.

I had this brought sharply home to me within the past week. I got a strange Email from one of my regular correspondents (who maintains a department in the association magazine that I edit) and it contained a link to an address that ended in ".cn" which is the country suffix for China. That raised my hackles so I messaged Norma to ask whether she had sent it to me; she had not. I had her do a full scan of her system for malware, and it came up clean. However by the time the scans had finished she had received messages from several other people listed in her address book. One had received a Viagra ad, others had mysterious links similar to the one I got!

The rule these days, of course, is to never click on a link in any Email message unless it comes from a trusted source and you confirm that the source did, in fact, send it to you. It's extremely easy to fake the "from" address in Email, so it cannot be trusted!
Every thing you say is true, however, Chris is concerned about the publication of diagnostic info about her  AMD box.

I do not think this is a threat to her or any future user.

You are absolutely right that if you are connected you have a security hole.

---

### Post by Chris Edgell on 2010-03-09
sudo apt-get install checkbox checkbox-gtk gksu python-gtk2 python-glade2 debconf python python-central udev

This is the package k3 gave for "System Testing".  I installed through synaptic because I had heard that if you "get app" through terminal you have to uninstall through terminal also and I didn't know if I could do that...and the same is true of synoptic; if installed through synaptic it must be uninstalled through synaptic.  (Is this true?)

I was gratified to see that it worked and there it was  --installed.  Then I began to run the tests.  I thought that would be it.  If the card COULD make a sound, when I pressed that button -- it would.  Well it didn't make a sound -- then it asked me if I wanted to see all the diagnostics.  I said yes, or however that moment went...and it began to show me about, I'd say 50 pages, fine print, diagnostic description of each and every thing that goes on in a computer -- is my guess.

I could decipher so little...that IS why I picked out two sections that seemed pertinent to the subject of sound.  (k3 believes I may have aborted the interworkings, although I thought it was finished.)  It did appear on my Applications > System > Systems Testing menu (AS Systems Testing).

Ranch hand, maybe you, or even you Jim, run it on one of your machines and see just how THAT unpacks.  Will ya'?  At this time, I don't see any point of me running it again, do you?  

The truth is what I was worried about is some hacker being able to see everything.  It IS the reason I don't use my debit card online, and also I am afraid to do online banking.  Maybe my fears are unfounded and unreasonable.  (If so, offer me your opinion on that if you want to.)

I WAS glad you brought up your occurance about .cn; not that it's really related but a friend of mine in India right now, sent me an email with an IQ test and I fell for opening that especially it being from her and I saw right away it was some kind of Spam Scam.  I saw it when I had closed and then tried to email her back and it was embedded in there " her name @inviteOrangeshark.com"  I tried every way to delete it from my contacts, for example it didn't even show up.  I deleted HER e-dress and was going to put it manually and the address came to be the Orange Shark one.  In the meantime I got 4 spams; two for some kind of Chicago Pillow Talk.  I contacted them (finally found how) and they said they'd unsubscribe me but they couldn't promise it wouldn't happen again.  The only way I could write to her was to send it to myself and type her in at the carbon copy box.  I have received no more spam but would not be opening anything from her.  

YOUR story makes me think, or I should say wonder, if Linux is targeted...probably just another paranoid delusion.  LOL

Let me close here and see what comes of all this.

Thank you all for your support.
Chris

---

### Post by JKyleOKC on 2010-03-09
> **Chris Edgell said:**
> I installed through synaptic because I had heard that if you "get app" through terminal you have to uninstall through terminal also and I didn't know if I could do that...and the same is true of synoptic; if installed through synaptic it must be uninstalled through synaptic.  (Is this true?)

Ranch hand, maybe you, or even you Jim, run it on one of your machines and see just how THAT unpacks.  Will ya'?  At this time, I don't see any point of me running it again, do you?  

The truth is what I was worried about is some hacker being able to see everything.  It IS the reason I don't use my debit card online, and also I am afraid to do online banking.  Maybe my fears are unfounded and unreasonable.  (If so, offer me your opinion on that if you want to.)First, Synaptic, aptitude, and apt-get are all just "front end" programs for the "dpkg" utility, so all of them eventually wind up at the same place and add to the same internal database. Thus if you install via any of them, or even via dpkg itself, you can uninstall with any of them. I've installed a few things by just double-clicking on the .deb file's icon (which launches dpkg directly), and uninstalled them via Synaptic. I prefer Synaptic myself over the others, but that's just a matter of personal preference.

I'll see if I can run the checkbox package on one of my machines that's giving me some difficulty in tracking its temperatures but it may be a while before I get that done.

As for safety of online banking, I do almost all of my banking online and also pay most of my bills on line as well. I do take extreme care about security; the database repair I do for others involves their financial data, and I also repair a number of medical practice files. Thus keeping my systems extremely secure is essential. I'm also a bit paranoid about Email; I'm averaging a hundred or more junk messages a day and I never click on links except those that I verify as coming from trusted sources. The delete key is the best defense against phishing, and careful selection of sites when surfing is the best defense against hack attacks.

Just keep in mind that the risk of having a credit card's data stolen is much greater at any restaurant where the server takes it to the back to run the charge, than it is when dealing with reputable firms on line. (Not to accuse all servers, but every occupation has its share of bad apples so the risk is always there.) Just be sure that the link uses "https" rather than just "http" and that the little padlock symbol is showing in your browser, and you'll be as safe on line as in the real world.

---

### Post by ranch hand on 2010-03-09
It is also good to remember that ALL credit card transactions go over the "net".  Crackers generally attack the big server companies where they have a better chance of scoring thousands of cards than trying to get them one at a time in home machines.

---

### Post by JKyleOKC on 2010-03-09
Quite true!

I can't find "checkbox" in the repositories for Hardy LTS, which is the version I'm running. Apparently it didn't get included until Jaunty.

However I did a bit of google searching and discovered that this is not a specific set of tests, but rather a control framework that can be extended to run any kind of test you can imagine, so long as you can create a script to do it. Thus your guess, Chris, that it tested almost everything the system could do is pretty close to correct!

Now if I could just figure out why the temperature sensors in this box I'm writing this from all claim the box is full of ice cubes (0 and -1 C) and that the fans aren't turning at all... It's not really a big deal but it has gotten under my skin!

---

### Post by Chris Edgell on 2010-03-09
[https://wiki.ubuntu.com/Testing/Automation/Checkbox](https://wiki.ubuntu.com/Testing/Automation/Checkbox)

Can you tell when it was created by this website?  Oh, but you probably were already here, by what you were saying.

---

### Post by ranch hand on 2010-03-09
> **JKyleOKC said:**
> Quite true!

I can't find "checkbox" in the repositories for Hardy LTS, which is the version I'm running. Apparently it didn't get included until Jaunty.

However I did a bit of google searching and discovered that this is not a specific set of tests, but rather a control framework that can be extended to run any kind of test you can imagine, so long as you can create a script to do it. Thus your guess, Chris, that it tested almost everything the system could do is pretty close to correct!

Now if I could just figure out why the temperature sensors in this box I'm writing this from all claim the box is full of ice cubes (0 and -1 C) and that the fans aren't turning at all... It's not really a big deal but it has gotten under my skin!
Seeing that they are going to offer you an upgrade from 8.04 to 10.04 after release (I have had it work on test installs of 8.04) you might try using a version from a later versions repo.

I would not do that on a production OS, only on a test install.  I have run a lot of things that were never backported.  Most have worked.  Some are a real wreck.

---

### Post by k3lt01 on 2010-03-09
> **JKyleOKC said:**
> I can't find "checkbox" in the repositories for Hardy LTS, which is the version I'm running. Apparently it didn't get included until Jaunty."checkbox" replaced "hwtest" so the Hardy version is probably hwtest.

@ chris. There was an article in an Australian magazine a couple of months ago that said you are safer shopping and banking online than you are if you actually go into a shop or bank IF you follow a few simple precautions.
1. Always use a known good machine to do your banking/shopping on.
2. NEVER use Internet Explorer to do banking/shopping online.
3. Always clear your cache.
4. Try not to use the machine you bank/shop with for other general browsing.
5. Only use a debit card, credit cards can max out really quick, debit cards only use your money.
6. Make sure the machine you bank/shop with is up to date with all security updates installed.

---

### Post by Chris Edgell on 2010-03-09
> **ranch hand said:**
>  I have run a lot of things that were never backported.  

First, I don't know what that is

> **k3lt01 said:**
> 

3. Always clear your cache.



Second I don't know how to do this.

You can tell me here, or I can try to learn these two things elsewhere.

Chris

---

### Post by k3lt01 on 2010-03-09
Backports are applications taken from a newer version and "backported" to an older version. If you have a look at your Software Sources you will see an option for a Backport repository.

Clearing your cache is easily done. In Firefox go Edit > Preferences. Then when Firefox Preferences opens go to Advanced > Network. Under Offline Storage make it 0 MB and click "Clear Now". Check the screen shot to see what I mean. That will clear your Cache, understand that doing this means everytime you close Firefox you will lose any files that help it to remember what a page looks like so browsing can take a little longer. You will also have to manually sign once more into any pages like Ubuntu Forums if you click "Clear Now".

---

### Post by Chris Edgell on 2010-03-09
Thank you k3, it's been great meeting you!

---

### Post by k3lt01 on 2010-03-09
> **Chris Edgell said:**
> Thank you k3, it's been great meeting you! Pleasure is mine.

---

### Post by JKyleOKC on 2010-03-09
I discovered that the program was hwtest in Hardy and was renamed (and greatly extended) for Jaunty. When I ran it, it merely verified that my sound, video, keyboard, mouse, and internet connection all worked; nothing more! Still no clue as to why the temp and fan sensors in this box don't show up anywhere but in the BIOS report...

EDIT: Finally discovered what was wrong and got things working. The recommended installation procedure for the sensor-reading packages had given me the wrong data! Once I located the correct driver and installed it everything began working as expected. The moral: sometimes the "official" answer is wrong. As Sherlock Holmes observed, once you eliminate the impossible, what remains has to be the solution to the problem.

As for fraud prevention, I don't ever use my bank-issued "check card" in debit mode except at the bank's own ATMs. Everywhere else I use it in "credit card" mode. It bears the Visa logo and thus has all the fraud protection that Visa provides for regular credit cards. My bank has a zero-loss guarantee, but if anyone were to drain my account I'd be in deep trouble for the 30 to 60 days while things were fixed up. Fraudulent credit-card charges, however, have to be reversed more rapidly while the investigation goes on...

---

### Post by ranch hand on 2010-03-10
Well, that was fun.  I installed the checkbox-cli package on my Ubuntu 9.04 (the only package missing from the full set).

Ran it.

Went and opened the generated file in gedit.

All I can say, Chris, is that if you only had 50 or so pages you have a very short report.   I am not sure how many pages there are but there are 628 screens to view it all (24493 lines in gedit and I get 39 lines on the screen).

I did test my audio and it works, I am shocked.  I thought it was all in my head.

Turns out that my video works too (I could see the colored bars).

What fun.

Do not post your results.  I don't care about any security issues on this.  Some one may attempt to read the whole thing and go blind or maybe die before finishing (perhaps from boredom).

While this is really neat and I am glad I have it I do not think it is going to help us a whole lot.

---

### Post by Chris Edgell on 2010-03-10
> **ranch hand said:**
> 


All I can say, Chris, is that if you only had 50 or so pages you have a very short report.   I am not sure how many pages there are but there are 628 screens to view it all.
 

Do not post your results.  I don't care about any security issues on this.  Some one may attempt to read the whole thing and go blind or maybe die before finishing (perhaps from boredom).



Okay, okay....it WAS 628 pages...what was I THINKING trying to keep the truth from you.  LOL

Thank you for assessing the value of it all, for me.  (So are you saying that even though you discovered that your video card works, it didn't point the way to solutions for using it; I must infer that you weren't because you didn't KNOW it worked?)

Thanks Jim (The short test sounds adequate, really, for all intents and purposes.)

---

### Post by ranch hand on 2010-03-10
I knew it worked, use it all the time.  Just wanted to see what this checkbox was all about.  I do have a tendency to be a smartass.

Gave me a lot better readout on my card than I have seen before.  This could be handy in some instances.

If you installed gnome-alsamixer, did you check all the configuration options out?  The options under Edit>Sound Card Properties is where you want to look.  Something may be muted or just turned down too low.

---

### Post by Chris Edgell on 2010-03-10
How could I miss that??!!  "I thought it was all in my head."

(Don't stop, that's one of the things I like about you.)  LOL

Well, back to SOUND, or should I say lack of.


I just downloaded Ubuntu Jaunty on this JYD/AMD (replacing the XUbuntu)....I thought if anything should fix a software problem it would be a new version...yes, no, maybe...in this case:  NO


It's interesting to see the big differences between this and XUbuntu.  This IS Pulseaudio (v. alsa), the System Tests happens to come with the installation, and so does OpenOffice (v. AbiWord).  There are lots of differences in the way it's set up and appearances.

I Did the Java and Adobe packages as requested by YouTube.  I downloaded the restricted extras; I downloaded 58 additional things after the 281 updates...but still no sound.  There is nothing to compare my synaptics to nor the BIOS.  I'll be studying the manual about the sound components (is it an actual card?  I see 3 cards, two are not it and the third one, well, it is the one that the monitor actually connects to -- could that be a sound card.)

(Why is my cursor trembling?)

---

### Post by ranch hand on 2010-03-10
I still think you need gnome-alsa mixer.  You can always remove it is it does no good.

You can also run, in terminal, for the alsamixer;
```

alsamixer

```
No sudo.  Put the terminal on full page and be sure to use the direction arrow keys as it is bigger than the screen.  Hit enter when you have moved to something you may want to change and you will be able to work that particular item.

As always there is info at:
```

man alsamixer

```
I prefer the gnome-alsamixer as you can do all that in a good gui.  I also think it works a lttle better and supports some older cards better, not sure why.

---

### Post by Chris Edgell on 2010-03-10
chris@chris:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 14)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:0b.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0c.0 Communication controller: 3Com Corp, Modem Division WinModem
00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Non-VGA unclassified device: VIA Technologies, Inc. VT8235 ACPI (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
chris@chris:~$ 

I am pasting this here; it is the output of lspci.  The card that I was thinking was the sound card is the nVidia card.  So is the sound card built into the motherboard?  I was so sure that I read that it is NOT.  The little about one inch small "box" where the speaker plugs in...THAT can't be called a card.
  
But the alsamixer says:
   Card:CMediaCMI8738                                                      &#9474;
Chip: CMedia PCI

One of my frustrations is that I HAD the AMD manual for this machine and can't seem to find it again...and I've looked and looked and looked.  If anyone can give me the URL for that I'd love it.

I'm not going to spend much more time trying to get this machine to make a sound.  When I give up (or until such time I want to spend money trying to get sound) I will use this one for experimentation project and/or learning projects...like even with Open Office...well there could be lots of things because it IS 80GB so there is lots of room for projects... so I am not feeling defeated here.

Although I do want one more go-round about the "Sound Card".

Chris

---

### Post by ranch hand on 2010-03-10
The manual for the mother board says that it would need to be a pci card but you may have a alightly newer version of that MB.

Your lspci does say it is an audio controller.  This usually does indicate that it is part of the MB and not a separate card.

I just ran a search on your "CMediaCMI8738" card.  Ran it for jaunty ubuntu.  Came up with this that purports to get it working with pulseaudio in Ubuntu.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I do not know.  I can tell you that the author is a valued member of the testing forum and is pretty good at hacks.  Might work.

---

### Post by k3lt01 on 2010-03-10
> **Chris Edgell said:**
> 00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)This is your card.

> **Chris Edgell said:**
> But the alsamixer says:
   Card:CMediaCMI8738                                                      &#9474;
Chip: CMedia PCI[It is correct.

> **Chris Edgell said:**
> I'm not going to spend much more time trying to get this machine to make a sound.Awwwwe don't give up just yet.

Do me a favour pleas Chris. Go System > Preferences > Sound and open up the sound preferences for me. Check my screenshot to see what I mean. Now your in Sound Preferences see what is listed under hardware. Also make sure the output volume isn't muted in this gui and that the volume slide control is at least halfway if not all the way to the right of the slide. Mine is turnd off cause I don't like my computers making noises anytime I do something.

Ok now that is done down the bottom of that is a part titled "Setting for the selected device" have a go at changing the setting drop down to something else, try each one if need be while you have something playing a sound.If there is more than 1 device listed, I doubt there will be, do the same for each one. Let us know if anything happens.

---

### Post by Chris Edgell on 2010-03-10
Well you have Karmic.  Maybe I should just do that.

I'll let you see my screenshots of my System > Preferences > Sound

I'm not sure of the additional figures after the CM-8738, my (Rev 10) was not an option.  I was just guessing.

I'm glad you encourage me to go on!  Thanks, I needed that.

You see mine is very different from yours.

---

### Post by k3lt01 on 2010-03-11
Ah, I forgot they changed it with Karmic, I've been having a blank day today lol. Have you tried changing the drop down boxes in your Jaunty install to see if it does anything? I haven't got any Jaunty installs anymore so I'll be flying blind with any suggestions I make. I'm sure with the screenshots and with help from people with a Jaunty install we'll figure it out.

---

### Post by audiomick on 2010-03-11
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=149776&stc=1&d=1268334582[/IMG]Hi Chris,
what happens if you click on the test button here
[ATTACH]149781[/ATTACH]

Edit: I can't get this picture to show up as a thumbnail, but I am determined to figure it out, so I will keep trying to edit this post until I do. But right now I have to go and cook dinner for my girlfriend...;)
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=149776&stc=1&d=1268334068[/IMG]

---

### Post by Chris Edgell on 2010-03-11
Hi Michael,

I know that I am moving right along...maybe too fast; but I am moving right along.

I have spent the morning INSTALLING Karmic Koala in this machine.  Now I have to spend some time reading about sound in Karmic.

I tried to open that and couldn't; I'll try again and tell you what message it gives me.

Actually, the layout is so new to me that I can't even find where it downloaded to.

---

### Post by audiomick on 2010-03-11
Hi Chris.
Have another look at the last post. I changed the format of the picture from xcf (gimp format) to png, and now it works.

edit: if it downloaded, it will be either on the desktop or in a folder called "download"  or something similar in  your home folder.

---

### Post by Chris Edgell on 2010-03-11
Michael, 

I can now click on this and see the close-up.  Now, you must remember that I have changed to Karmic (as you have, I see) and now I no longer have that tab for devices that shows in the screenshot.

Now YouTube says I need Javascript and Adobe, but neither is in synaptics.  What shall I download?

Now, I have gone and looked at the Software Download Center.  There is a lot of stuff there, what shall I do next?

---

### Post by audiomick on 2010-03-11
That sounds like you haven't installed the ubuntu-restricted-extras yet.
Have a look here
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
There is a link to click on there that reads "click here to install...." that should take care of it. Don't miss the comment just under that about playing DVDs.

If the link doesn't work (which it should), you can also install ubuntu-restricted-extras via the synaptic package manager.

---

### Post by Chris Edgell on 2010-03-11
Here is the screenshot of what happened when I tried to download from the link.

(When I go to synaptics and type in Ubuntu restricted extras, it doesn't come up. Where is it?)

---

### Post by audiomick on 2010-03-11
you don't need to choose an application, just tell it "ok".
That "apturl" that you can see in the first little window is the application it needs. The "choose" is just there for if you want to use something else, or if it doesn't know it should be using apturl.

I just tried it out, and if ubuntu-restricted-extras is already installed (as it is on my machine), it just comes back with a message saying so, so it is quite safe.

---

### Post by ranch hand on 2010-03-11
Try this link;

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Repositories](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Add_Extra_Repositories)

You need the stuff for Medibuntu.

It is very good at getting the right repos in and telling you how to do it.  How to add the puplic key is in that section too, down at the end.  That is a really great site for setting up your box on any version (not 10.04 yet).

After you get that set up use synaptic or;
```

apt-get update

```
and 
```

apt-get ubuntu-restricted-extras

```

---

### Post by Chris Edgell on 2010-03-11
Here's my screenshot...

Now I'm wondering about the download CD that I installed from...

---

### Post by audiomick on 2010-03-11
There is a documentation page about medibuntu here
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
There is a command there that you can cut and paste into the terminal to set up the repository for medibuntu, and another to install the key.

---

### Post by Chris Edgell on 2010-03-11
Where the heck IS the clipboard?

I am trying not to get frustrated with this new system.

I'm sorry...I was able, in both cases to just go and paste, regardless of the clipboard.  It's installed.....

---

### Post by audiomick on 2010-03-11
> **Chris Edgell said:**
> Here's my screenshot...

Now I'm wondering about the download CD that I installed from...
Ok, you probably need to enable some more sources in synaptic.
system> administration> synaptic package manager
in the "preferences" menu choose "package sources"
on the first tab, tick all the boxes except the one called something like "source code"

Remember, I am translating this from an install that is in German, so the names of things might be a bit different to what I write.

What you are trying to achieve is to enable the repositories for "main", "universe", "restricted", and "multiverse".

I just tried to make a screen shot, but I have lost it somewhere in the depths of my computer. I will put it in here when I find it.

edit: here it is. The screen shot thingy was still set to store in the wrong folder.
[ATTACH]149788[/ATTACH]

---

### Post by ranch hand on 2010-03-11
9.10 is not a version that I really like.  It had a lot of stuff thrown into it so that it could be included in 10.04.

10.04 is more stable now (beta1 comes out on the 18th) than 9.10 was at the RC stage (1 week before the final release).  There are a lot of things that should be backported to it but that is somehow in conflict with the Ubuntu policy on package backporting.

---

### Post by Chris Edgell on 2010-03-11
Well, ranch hand, we'll see about that then...

Here are my screenshots Michael.

---

### Post by ranch hand on 2010-03-11
That should get you the "extras" if you hit the refresh button in synaptic.

---

### Post by audiomick on 2010-03-11
Yes, do the refresh thing, then try and get the ubuntu-restricted-extras again.
That is, assuming you had added ticks to the boxes before the screenshots? If they were already all selected, let us know.

---

### Post by Chris Edgell on 2010-03-11
Why can't I seem to get back to the first screenshot I have in that line-up of three?

How did I get there?

Now I go to sys>adm>syn pkg mgr

Preferences> choose pkg source 

But here's my screenshot when I go to preferences...What did I do different?

How DID I get to the one that says Software Source?

I got to the software sources!  I GOT THERE!  Now let's see....

---

### Post by ranch hand on 2010-03-11
System>Administration>Software Sources

Is what you want.

---

### Post by audiomick on 2010-03-11
Wait on: the sources shown in the screen shots were all ok. All you need to do is (close the pop up and) click on the "reload" button in the top bar of synaptic, the one with the circular arrow icon.

---

### Post by Chris Edgell on 2010-03-11
I just was able to download the restricted extras.  Very good and I thank you.

Now what mixer or gui should I download?

I have always liked aumix, but when I mark it it tells me that if I download that I will need to download the OSS Compat...is that a big deal, (let me go look it up...)  It seems more related to ALSA than to Pulseaudio, yes?  Let me look at other, well I don't know what others there are...although I'm still trying to understand the relationship between Pulse and Alsa...

---

### Post by Chris Edgell on 2010-03-11
And here's what I get when I look at the Gnome-alsamizer...

---

### Post by audiomick on 2010-03-11
I just noticed this question
> **Chris Edgell said:**
> Where the heck IS the clipboard?
You can't "find" the clipboard. That is where the computer puts the stuff that gets copied when you do a cut and paste or a copy and paste. If you are interested, there is a thing called "parcellite" available in the repositories that puts a little icon in the task bar with which you can recall the last things that you copied. You can adjust how many steps it remembers. I am finding it very useful, but it isn't necessarily something you absolutely have to have.

As far as your mixer goes, I gather you mean a sound mixer. You could install
gnome-alsamixer
for that, I think.
It turns up in your applications menu, probably under "multi-media", or something like that. On mine, it is in "Unterhaltungsmedien"....;)
Having said that, I find the thing a bit puzzling myself.


In this picture
[ATTACH]149809[/ATTACH]
the red arrow points to the fader on the "input" side. If I turn that down, the sound from You Tube, for instance, goes away. I am pretty sure it also turns of the signal from a CD, but am not completely sure.
The green arrow points to the master output fader. If that is all the way down, nothing comes out at all. The boxes down the bottom called "stumm" are mute switches. If they are selected, nothing comes out of whatever that fader controls, no matter what position the fader is in.

In the "edit" menu under "sound card properties" there are boxes to select what is visible on the mixer. Select them all, to make sure you can see all the possible controls.


edit: just saw your last post. Click apply and let it install.

---

### Post by Chris Edgell on 2010-03-11
The last two hanging chads...(remember them? or not...)

The last unfinished business...

I once found the Manual for this AMD Duron (tm) processor but I just can't seem to find it again.

The other question is: Is my sound card a card or not...I've got to locate it to see about a possible replacement...

Yes, still no sound.....but if the sound card wasn't working would it still show up?

---

### Post by audiomick on 2010-03-11
I think it probably is a sound card as opposed to a built in sound chip, but that is just a guess. I would open the case and look at where the plug that you plug the speakers into is mounted. If it is on board, i.e built in, the plug will be mounted directly onto the motherboard. If it is a plug in card, the plug will be on the card. This is pretty self explanatory when you see it.

As far as the manual for the machine goes, have you tried your friend google for that? There are manuals for most things in the net these days.

I will be off to bed very soon now. It is 2 a.m. here...
I will look back in tomorrow some time.

---

### Post by Chris Edgell on 2010-03-11
I do not know how I found it before, but I WILL find it again.  I have googled but don't see to get it.

I downloaded the clipboard and just can't access it.

And so goodnight.

---

### Post by ranch hand on 2010-03-11
Personally I would be doing your updates before anything else.  9.10 has been out  awhile and there have been many fixes.  Those updates will make it about twice as stable as it is now.

---

### Post by k3lt01 on 2010-03-11
@ guys, your confusing the heck outa me with the rigmarole your telling chris to do.

Hi Chris, by rights Karmic should be set up with EVERYTHING you need (assuming its Ubuntu) if it isn't there is another problem but we will cross that bridge if we ever come to it. Could you do this for me please.

Go System > Preferences > Sound and open up the sound preferences for me. Yep you guessed it we are going back to a previous post so we know we we are starting from.

Now your in Sound Preferences see what is listed under hardware. Also make sure the output volume isn't muted in this gui and that the volume slide control is at least halfway if not all the way to the right of the slide. Mine is turned off cause I don't like my computers making noises anytime I do something.

Ok now that is done down the bottom of that is a part titled "Setting for the selected device" have a go at changing the setting drop down to something else, try each one if need be while you have something playing a sound.If there is more than 1 device listed, I doubt there will be, do the same for each one. Let us know if anything happens.

---

### Post by Chris Edgell on 2010-03-11
Oh, I think I see what you mean.  Like have the YouTube going while I try each one.  (Yes there is just one device listed.)

---

### Post by k3lt01 on 2010-03-11
That's it, let us know what happens.

---

### Post by Chris Edgell on 2010-03-11
I was going through them one at a time and when I got back that device area said:


internal audio
Disabled
Off

---

### Post by Chris Edgell on 2010-03-11
Here's how it looks now...

Oh but wait...that was just how it looked when the bottom choice was "off"

---

### Post by k3lt01 on 2010-03-11
Turn it on and see what happens.

---

### Post by Chris Edgell on 2010-03-11
Okay, I did each one and got no sound.

(In rereading this, I wouldn't want michael or ranch hand to feel bad, I think I caused the fragmented responses, by me being so quick to be back and fourth, just like this last little interchange with you.  I stay at it for so many hours at a time and have so many ups and downs I lose any focal point and/or powers of concentration.  I do see how in a back and forth interchange it is somewhat easier to keep it to the two doing the talking....you know, unless there are long periods between the interchanges making it less like a conversation between two people on the case.)

But, I want to say, it's all good...

The test tune I check my sound with is "He Washed my Eyes with Tears" by that Jimmie Swaggart.  And it starts out, (spoken) "Well, praise God"
I really wait for those words coming out of my speakers.....

On that other point, there is no actual card; it seems to me that it is simply a one inch square cube plugged into the motherboard.  

Well, I must close for now.
Chris

---

### Post by k3lt01 on 2010-03-12
I do understand the back and forth thing and that it gets confusing. I also understand the desire not to cause offence to posters who have helped along the way. Both Ranch Hand and AudioMick have my utmost respect (Ranch Hand and I both test Lucid and post in the Lucid testing forum). However, I was worried, not really but I can't think of a better word atm cause I'm having a blank day, that we had no real answer to what you had and even if it was "turned on". We now know it was "turned off" and nothing we did until it was "turned on" again would be of any value. It is important to do this type of thing in a structured way. Now we have the baseline, the "card" is now turned on (hopefully it still is) we may be able to get something happening.

Ok so we now have a proper baseline. That was the important thing even if we didn't get it working.

I am wondering why it was disabled by default. It may be that there is no driver available for it in the kernel even though Ubuntu recognises that it is part of the motherboard. I'll do some digging on Google to see what I can find. 

(EDIT: Could you now go System > Administration > Hardware Drivers and see if anything comes up in the list. If something does come up let us know what it is before you enable or disable it. That way we can see what it is and if it might have any effect).

---

### Post by Chris Edgell on 2010-03-12
k3, see post #172, whether it clearly implies that it was NOT off by default.  As I had gone through them, when I got back it said disabled and off...but that was only because I had left it on the "off" position in the going through the options (the top option being "off")--I hadn't seen their connection until I discovered that, when I left the bottom on off, it showed the top as being off and disabled.

Here's the screenshot of the drivers window.

---

### Post by k3lt01 on 2010-03-12
Forgive me for being a bit slow I'm just trying to clarify this for my own benefit atm. Was the "card" turned on while you checked it? The message I got from your posts was it was turned off by default, now I don't really have a clue ;)

---

### Post by kio_http on 2010-03-12
I always prefer using the alternate installer. True its not as aesthetic, but its got more options and is stable

---

### Post by Chris Edgell on 2010-03-12
I was very glad you clarified that for me that you have your own relationship with Ranch Hand and Audiomick; as you know already they are both very good to me.  Thank YOU for being you.

Let me say it this way:  That bottom drop down menu says "Settings for the selected device."  There are about 15 of them.  When each one is clicked it is reflected in the top area where it says, "Choose a device to configure"

So in the top area that device to configure is "Internal Audio", each "Setting" I click in the list below becomes the last line of the top space, first line being the original "Internal Audio"; as I click through each one it is added to the top box beneath "Internal Audio".  Then the last item in the bottom list says off.  I clicked on that as if it too were an option and when I went and looked at the top it said, "Internal Audio" "Disabled" and "Off"  I panicked thinking I had "lost" the "Internal Audio" when actually I had just turned it off inadvertently, by clicking on the "Off" in the bottom menu.  Have I made myself clear with so many words?  It was not off by default.

---

### Post by k3lt01 on 2010-03-12
Guess what! I'm now on the same page as you, lol :popcorn:

I'm thinking there is either a driver issue (unlikely to my way of thinking) or something in your Sound "Card" itself is broken (more likely to my way of thinking).

I'll do some searching and will see what I can find.

I may not be on this weekend, I have my little bubba to look after, so I'll wish you all well and will get back as soon as I can.

---

### Post by audiomick on 2010-03-12
> **k3lt01 said:**
>  I'm thinking there is either a driver issue (unlikely to my way of thinking) or something in your Sound "Card" itself is broken (more likely to my way of thinking).
I agree with this. You did ask in a post earlier if it is possible that the sound card is broken but still being recognised, and I don't think anyone answered. Yes it is possible. The computer "sees" the electronics immediately behind the connector that connects the card to the main board, but the card has several stages of electronics after that. Any of these could be broken without the computer knowing anything about it. 

I just did a bit of a search, and came up with a post** in German** on Unixboard.de here
[http://wiki.unixboard.de/index.php/C-Media_Electronics_Inc_CM8738](http://wiki.unixboard.de/index.php/C-Media_Electronics_Inc_CM8738)

It says that the card is 100% Linux compatible, and works with ALSA as well as with OSS, another Linux sound system. As far as I know, pulseaudio sits on top of ALSA, so theoretically, the card should be able to work, no matter what. 

The post also says that most distributions should recognise the card automatically, as the drivers are built in. This is the case on your system: the system knows the card is there, and doesn't want to load any proprietary drivers to make it work. That is not to say that the driver works perfectly, but one can assume it as much as one can assume anything... ;)

Maybe k3lt01 has some more suggestions on how to test the sound; to be quite honest, I haven't looked into the topic very much at all. My computer isn't allowed to go "beep", and I rarely listen to music on the computer. Having said that: in the list in this screenshot
[ATTACH]149852[/ATTACH]
you can go through all the possibilities one at a time without worrying about breaking anything.
Of the settings that are likely to be in the list, the following are the most likely to be correct:

Analogue Stereo Duplex : this means the card is able to receive analogue audio and give out analogue audio at the same time. 
The "analogue" refers to the type of signal that is arriving from the outside at the card and the type of signal that is leaving the output connector of the card. There are things that connect via "digital" connections, but I expect your speakers are plugged into the "headphone" or "line out" connector of the card, and that is analogue.

Analogue Stereo Output : this means that the card can put out an analogue signal, but not receive anything, i.e. it should deliver a signal to your speakers, but wont be able to see anything that you plug into the input of the card (which you are also not doing at the moment).

The various 5.1, 7.1, "surround" or what have you options may or may not deliver a signal to the output you are plugged in to.

Just for interest's sake, here is a picture of the connections on my machine. The red arrow points to the connector with the green ring that is the connection for stereo analogue out. This connector nearly always has a green ring around it, and is the one you should be plugged in to.
[ATTACH]149853[/ATTACH]
The other ones are for things like microphone in, and the various speakers for centre, left rear, right rear and what have you in a surround (5.1, 7.1) installation.

We have also discussed whether the sound card is on board (built in) or a PCI card. In this picture, you can see from where the sound connections that the red arrow is pointing to are, that my sound card is on board. If it were a PCI card, as I am sure yours is, the connections would be in one of the card slots in the area that the green arrow is pointing to.
[ATTACH]149854[/ATTACH]

Please don't think I am assuming that you have made some silly mistake or anything. I am sure you are on the right track. I just think that the more you know about this stuff, the more easily you can understand what people are suggesting you try out. I'd rather tell you something you already know than have you wondering what is going on.

---

### Post by Chris Edgell on 2010-03-12
Hi,
Great!
I must say that the back of my computer looks just like yours except I have 3 
"holes" (what ARE they called?) for speakers and mikes where you have 6.

I have 3 cards in that bottom area you point out:   1) accommodates telephone input, 2) accommodates Ethernet connection and above that, 3) nVidea card.

As I said, my speakers plug into a squar-ish yellow cube about 1" sq. that appears to be plugged into the motherboard...is that the way YOURS is?

Just wanted to add:

I noticed in the link you sent about the CMi8738, that it spoke of Alsa and OSS as two different categories, as if Alsa would be for PSI cards and OSS would be for "no card -- but rather plugged into the motherboard".  When I went to look in my synaptics for aumix it said if I were to install THAT it would require a boatload of OSS stuff.  Do you distinguish between an ALSA base or an OSS base as even your link implies?  Or am I wrong in some assumption?

---

### Post by audiomick on 2010-03-12
Ok, so maybe it is on board audio. Interesting to know, but it effectively doesn't make any difference to the process of trying to make it work. Yes, mine is on board audio, i.e. built in to the mother board. You have less holes to plug into probably because the card can't do as many variations on the "surround sound" them as mine can. Mine is only about 2 years old, and was a bit expensive...;)
The "holes" can be referred to as "connectors" or maybe "sockets". "Plug" is the connector on the end of the cable. That is also sometimes called a "jack".

Just by the by, one of the difficult things when I first came to Germany was re-learning the names of all the cables and connectors that I see at work in German. You really feel like an idiot trying to ask for something or talk about the thing in your hand when you know an English word for it, but have no idea of the word in the local language, even though you already speak the language fairly well. ;)

---

### Post by Chris Edgell on 2010-03-12
Look back to the edit on my previous post.

About the language, yeah, like "computer-speak",   LOL  In fact it reminds me of a Persian whom I'd met and he was telling about when he came right to college with NO english, and his roommate showed him, for one thing, the bar of soap and Corosh repeated after him, "Yes, SOAP" and then the guy made the washing motion under the arms and Corosh threw up his hands, "I know WHAT it is FOR, I just didn't know the word."  (In his own language Farsi)  How often what is unfamiliar is considered ignorant by the people who go that route every day...which IS, BTW. the tricky part with Beginners on Ubuntu...there is new to Computers and there is new to Ubuntu...everyone knows by now, I was the former.

---

### Post by audiomick on 2010-03-12
> **Chris Edgell said:**
> 
I noticed in the link you sent about the CMi8738, that it spoke of[COLOR=Red] Alsa and OSS as two different categories[/COLOR], as if Alsa would be for PSI cards and OSS would be for "no card -- but rather plugged into the motherboard". 
Not really different categories; the are just two different systems for implementing sound in Linux. They are also neither of them specific to on board or PCI sound chips. If you want some more stuff to read
[http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture](http://en.wikipedia.org/wiki/Advanced_Linux_Sound_Architecture)
[http://en.wikipedia.org/wiki/Open_Sound_System](http://en.wikipedia.org/wiki/Open_Sound_System)

Ubuntu uses ALSA, and that is fine. It is interesting to know that OSS also exists, but I don't know of any reason to want to change to it.

---

### Post by ranch hand on 2010-03-12
Did you ever run those updates to your system?  There may well have been  a problem with the audio drivers in the 9.10 release that has been fixed by now.

I know there were some sound problems for some folks at release time.

---

### Post by Chris Edgell on 2010-03-12
I forgot to mention that I ran the updates immediately after running the install...I was so anxious to see if I would get sound.  Then I ran many many packages...but to no avail.

---

### Post by ranch hand on 2010-03-12
Hmmm.  I think you are going to need a card.  I really do recommend the older Creative Labs ones (Sound Blaster, Audigy).  Alsa supports them very well.   Cheap used ones ore on Ebay from computers, like some I have and you have, that folks took apart for the parts.

An Audigy1 card from Ebay is doing its thing in my box right now.

---

### Post by k3lt01 on 2010-03-12
I don't have anymore suggestions at this time sorry. I found info saying the card was supported so I am leaning heavily towards the card being cactus somehow.

The only thing I would do now is to go through the drop down menu (like Michael suggested) again and see if it works. Otherwise if you really do want sound on that machine I would be following Ranch Hands suggestion and buying a cheap old stock card like a Creative Sound Blaster (I have one of them on my desktop and it's brilliant) and using it.

---

### Post by audiomick on 2010-03-12
> **k3lt01 said:**
> ... the card being cactus somehow.
That's Australian for "irreparably broken". It is great to see someone using proper English...:popcorn:

I think the E-Bay suggestion is a good one. Anything that is called "sound blaster" something or other should work. They were the absolute market leaders about 10 years ago, which means that they will almost certainly be well supported and will sound quite good enough for "household"use.
Look at this for instance
[http://cgi.ebay.com/Soundblaster-Ensoniq-ES-1370-PCI_W0QQitemZ350326729414QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item519119aac6](http://cgi.ebay.com/Soundblaster-Ensoniq-ES-1370-PCI_W0QQitemZ350326729414QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item519119aac6)

The thing to check before you buy anything is if you still have a PCI slot free. You need to open the case, look where the cards are plugged in, and see if there is still a socket free.

Here is the picture again
[ATTACH]149902[/ATTACH]
we are talking about the area that the green arrow points to
you said this
> I have 3 cards in that bottom area you point out: 1) accommodates telephone input, 2) accommodates Ethernet connection and above that, 3) nVidea card.
if you want to add another card, there needs to be a socket free next to those cards.

---

### Post by k3lt01 on 2010-03-12
> **audiomick said:**
> That's Australian for "irreparably broken". It is great to see someone using proper English...:popcorn:LOLOLOLOLOLOL, it's funny when you feel you are among friends you revert to colloquial language.

If I may go off topic for a slight moment, Michael (we also share the same first name lol) are you a member of Ubuntu-AU? I know your in Germany but I don't think that would matter.

Back on topic.

I can personally vouch for Creative Labs hardware as I have some. It is sturdy and works ootb (out of the box) whenever I have tried it. Just be sure to get something that is a little older because 1 its cheaper and 2 new technology sometimes takes a little while to be adopted into the kernel.

---

### Post by audiomick on 2010-03-12
> **k3lt01 said:**
> ...are you a member of Ubuntu-AU? I know your in Germany but I don't think that would matter.
I hadn't even thought about that, but maybe I should look into it. ;)

---

### Post by Chris Edgell on 2010-03-14
I have ordered the very one you pointed out audiomick.  It made me aware of a misconception I'd had.  If I had set about to replace, I would have been trying to match my Cmi8738 sound device; now I see that it's more like with a printer, you put in something that's compatible and the computer detects what you put in.  

I was noticing that my Dell #1 (primary machine) has that internal sound production when the speakers are unplugged but the Dell #2 does not, (although the sound works with that "System Testing" sound-it does beep at me-- and the speakers plugged in work too).  I just wondered why it doesn't produce sound, since the internal speakers work, in the same way that machine #1 does work with Youtube, etc.

---

### Post by audiomick on 2010-03-14
> **Chris Edgell said:**
> I have ordered the very one you pointed out audiomick.  It made me aware of a misconception I'd had.  If I had set about to replace, I would have been trying to match my Cmi8738 sound device; now I see that it's more like with a printer, you put in something that's compatible and the computer detects what you put in.  Ok. I hope it works then...:-?:-\" Should do, though, and if I understood the e-bay ad, it was only 6 dollars...

> I was noticing that my Dell #1 (primary machine) has that internal sound production when the speakers are unplugged but the Dell #2 does not, (although the sound works with that "System Testing" sound-it does beep at me-- and the speakers plugged in work too).  I just wondered why it doesn't produce sound, since the internal speakers work, in the same way that machine #1 does work with Youtube, etc.
There are a lot of variables there, as you would have gathered from the discussion about sound thus far. If you are sure, as you said, that the hardware is all in working condition (internal speakers and what have you, it might be the easiest to do what you have already done: set the two machines up next to each other and see what is different. You have seen pretty much all there is to see in the way of sound adjustment thingys. Go through them one by one and see if you can see any differences.
Very important: if the #2 machine is doing _what you want_, even though you notice that there is something else that doesn't work as you expected, **write down anything you change** in the way of experiment, so you can get back to where you are now if you want to.

---

### Post by ranch hand on 2010-03-14
Another thing that would help is to work one machine at a time.  Having two running for comparison is a real good idea but just do changes on one of them.

I think you will be impressed by the new card.

If you want great sound I like the Audigy cards for surround sound but you need a pretty good surround sound speaker set.

---

### Post by Donald1715 on 2010-03-14
WOW... some thread. Just a few comments:

No such thing as a 254 mb ram chip. They come like so, 32mb, 64mb, 128mb, 256mb, 512mb, 1+gig, 2+gig etc. Some laptops have some built in ram so that will appear to throw off the above numbers.

If you want more ram for and older system and don't know what kind to get, make note of the model number of your computer, then try the manufacturers website, or go to one of the online auction sites and find similar computers for sale and see what they use. You'll see many people selling chips that will be listed to work in certain computers. To be extra safe, pull your old ram chip and compare it to the picture of the one you see online to make sure it's the same type. Don't fret too much about static... just make sure you have grounded yourself to the computers frame first to discharge any static before pulling the chip. Most systems these days need minimum 512mb's.

If a systems bios is not detecting a hard drive, it's for the following reasons:

The jumper is set wrong on the drive. Most are set to CS, but sometimes it needs to be set to Master/Single if it's the only drive in the box.

The IDE cables or 4pin power cables are dirty (blow out with canned air) or kinked.

Someone has messed with the bios. In which case you can set it to default settings.

The drive is bad.

The main reason to reset the CMOS on the Motherboard (and no, pulling the battery won't reset it, you have to change a jumper setting on the MB to do that, and you'd most likely need your motherboard manual to know which jumper) is if you have set a "power on" password for the Bios, and forgotten it. Resetting the CMOS clears the password back to the default.

For all the people here having troubles with partitions... I never make more than two partitions. One for the OS, and a small one for the backup restore copy of the OS. For instance, if I have an 80gig drive, the first partition would be 60gigs, secondary 20gigs. When I make a Ghost image periodically, it goes in the secondary partition.

For running other OS's, here's some food for thought. Try a mobile rack such as Vi-powers super-rack. They are cheap, under $20 and once you install it into your case in a free 5 1/4" drive bay, you'll never have to open your case again to access your hard drive. Now you can have a drive for WinXP, another drive for Linux, another for whatever... If one OS is giving you a hard time or crashes... it's easy as opening a drawer to remove that drive and slide in a new one with a working OS. I've been using mobile racks for years and they are great.

---

### Post by Chris Edgell on 2010-03-14
Hello Donald1715, 

I'll have to visit your page and check you out.  It's always nice having someone else come on board and "work with us" although work is such a relative term.  It has become more pleasure than work...even though, well, the people who help me here while not using the emoticon for banging the head against the wall at least may be challenged to teach someone with so many gaps in understanding.  Which is to say sometimes it takes me awhile.  One of the best things I can say about myself is that I try to be scrupulously honest. 

You may have read that I was not only new to ubuntu/linux but really new to computers and so many things I've been unclear on the concept.  And SO much is brand new to me...like I have no idea what a mobile rack is...well unless it's an external hard drive...or, I see it goes inside into a drive bay.  It sounds good but so far the only thing I have done at all is to install an OS on the "entire disk".  It stretches my brain to think of partitions and "gparted" etc...but I must say little by little I am getting the picture.

There are quite a few who will disagree with you when you say that removing the battery  WON'T reset the BIOS.  You SOUND like you know what you're talking about, but so do they.  So it's a hard point to read.

I wish you'd go into your profile and put what you are running into your signature or when you put what distro you're using it goes right there on the left beneath your name.  

But nice to read your post.

---

### Post by bradmayne04 on 2010-03-14
Are you sure your system meets the minimum requirements????????

---

### Post by k3lt01 on 2010-03-14
> **bradmayne04 said:**
> Are you sure your system meets the minimum requirements????????Yes, we have worked through that in the 20 pages or so that is this thread :popcorn:

---

### Post by Chris Edgell on 2010-03-15
k3,
I like you better everytime I see you.

---

### Post by k3lt01 on 2010-03-15
> **Chris Edgell said:**
> k3,
I like you better everytime I see you.lol :popcorn:

---

### Post by albert s on 2010-03-15
this post, is by far, one of the more interesting ones for me also being a newbie.
without posting, but simply by reading I have learnt quite a lot, and in the meantime have managed to sort out some sound on an oldish PC I have been trying to get running good on Ubuntu. 
thanks Chris.  :)

---

### Post by Chris Edgell on 2010-03-15
It's so gratifying hearing this from you albert s

And some very nice people here, don't you just love it. I'm happy that you managed to get some sound on an oldish PC.

---

### Post by albert s on 2010-03-15
I had back track running on an old laptop without an HD for a while and it had a tag line something along the lines of
 " the quieter you are the more you hear "
often comes to mind for me when trying to solve my ubuntu problems I find.
I started out on ubuntu using a P2 800MHz with 256ram, and now through friends/relatives upgrading I have found myself with an "all singing all dancing " (relative I know), dual core with 1G of ram.!!!!
and I would never(if avoidable) go back to windows. 9.10 really made it easy for me to stay here, it just seemed to have all the packages I needed.
now, I really must try this gimp thing out........

---

### Post by Chris Edgell on 2010-03-15
I haven't mentioned this before because, well, because I HAVE tried to focus on one machine at a time.  But now that I am waiting for the PCI card for the AMD, I have focused on Dell #2.

As I turn it on and off I have discovered that when I DO come to shut it off... I get the message like, "Unable to shut down."  And then I have to do a hard shut down and when I hold that button down I get this message in the black screen with white print

*Starting network connection manager NetworkManager                    [OK]
*Starting Avahi mDMS/DNS-SD Daemon avahi-daemon                        [OK]
*Starting Common Unix Printing System" cupsd                           [OK] 
saned disabled; edit /etc/default/saned
*Starting System Tools Backends system-tools-backends                  [OK]
*Starting anac(h)ronistic cron anacron                                 [OK]
*Starting deferred execution scheduler atd                             [OK]
*Starting periodic command scheduler crond                             [OK]
*Checking battery state...
/dev/sda:
 setting Advanced Power Management level to Oxfe (254)
HDIO_DRIVE_CMD failed"  Input/output error
                                                                       [OK]
[16839.638119] end_request: 1/0 error, dev sda, sector 30147935
[color=blue]Now THIS shutdown the first numbers change 3396.050424]  but the end "sector 30147935" same[/color]
[16839.638190] EXT3-fs error (device sda1): ext3_get_inode_loc: unable to read i
node block - inode=942844, block=3768484
[color=blue] This[3396.050496] changes but  the inode # and block# are the same 942844 & 3768484[/color]
[-[16839.64640819] end_request: I/0 error, dev sda, sector 34187615

(and then there are countless more lines just like that except the numbers change-if I keep hitting the shut down button it fills page after page with this line.)
[color=blue] This time thare are many more lines like these with the "unable to read" and as I flash through page after page the only thing that changes is the second half of the first number.[/color]

I'm thinking that it is showing me bad sectors...remember way back when...the title of this thread that I think I've ruined two hard drives......  COULD this indicate a bad section that only shows up...I want to say now and then, because I think I've had to do the hard shutdown many times...well at least 10 just while concentrating on this machine since about 3 days ago.

I can get it shut down, and then reboot and it will boot to the installed OS.  But I do remember that it has never been a good shutdown.

---

### Post by audiomick on 2010-03-15
> **albert s said:**
> 
now, I really must try this gimp thing out........
Hi Albert. Try looking here:
[http://gimp-savvy.com/BOOK/index.html](http://gimp-savvy.com/BOOK/index.html)
If that doesn't work, google "grokking the gimp". I can get it on my Ubuntu machine, but not right now on the Vista Laptop I am on....;)

Hi Chris.
That doesn't sound all that good with the shut down problems. I am afraid I am a bit too tired to think about it right now. I hope someone else looks in...

---

### Post by presence1960 on 2010-03-15
> **Chris Edgell said:**
> I haven't mentioned this before because, well, because I HAVE tried to focus on one machine at a time.  But now that I am waiting for the PCI card for the AMD, I have focused on Dell #2.

As I turn it on and off I have discovered that when I DO come to shut it off... I get the message like, "Unable to shut down."  And then I have to do a hard shut down and when I hold that button down I get this message in the black screen with white print

*Starting network connection manager NetworkManager                    [OK]
*Starting Avahi mDMS/DNS-SD Daemon avahi-daemon                        [OK]
*Starting Common Unix Printing System" cupsd                           [OK] 
saned disabled; edit /etc/default/saned
*Starting System Tools Backends system-tools-backends                  [OK]
*Starting anac(h)ronistic cron anacron                                 [OK]
*Starting deferred execution scheduler atd                             [OK]
*Starting periodic command scheduler crond                             [OK]
*Checking battery state...
/dev/sda:
 setting Advanced Power Management level to Oxfe (254)
HDIO_DRIVE_CMD failed"  Input/output error
                                                                       [OK]
[16839.638119] end_request: 1/0 error, dev sda, sector 30147935
[color=blue]Now THIS shutdown the first numbers change 3396.050424]  but the end "sector 30147935" same[/color]
[16839.638190][COLOR="Red"]_ EXT3-fs error (device sda1)_[/COLOR]: ext3_get_inode_loc: unable to read i
node block - inode=942844, block=3768484
[-[16839.64640819] end_request: I/0 error, dev sda, sector 34187615

(and then there are countless more lines just like that except the numbers change-if I keep hitting the shut down button it fills page after page with this line.)

I'm thinking that it is showing me bad sectors...remember way back when...the title of this thread that I think I've ruined two hard drives......  COULD this indicate a bad section that only shows up...I want to say now and then, because I think I've had to do the hard shutdown many times...well at least 10 just while concentrating on this machine since about 3 days ago.

I can get it shut down, and then reboot and it will boot to the installed OS.  But I do remember that it has never been a good shutdown.

Did you run fsck on sda1 from the live CD? If not boot the Live CD and choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda1 -y -f -v -c
```Let it complete and see if it detected and fixed any errors on the filesystem. Reboot without the Live CD and see what happens now.

---

### Post by JKyleOKC on 2010-03-15
> **Chris Edgell said:**
> I'm thinking that it is showing me bad sectors...remember way back when...the title of this thread that I think I've ruined two hard drives......  COULD this indicate a bad section that only shows up...I want to say now and then, because I think I've had to do the hard shutdown many times...well at least 10 just while concentrating on this machine since about 3 days ago.

I can get it shut down, and then reboot and it will boot to the installed OS.  But I do remember that it has never been a good shutdown.Some of what you see there is actually left over from booting up, but the error message really is from the effort to shut down. To see which is which, use the Ctrl-Alt-F1 trick to see your leftover boot time console messages. They will probably end with the "setting Advanced Power Management..." line, which normally takes place just before switching to the graphical login program. Then to switch back to the normal graphic display, hit Ctrl-Alt-F7.

There's a way to force a disk check and repair during the boot process, but I don't remember the details right now and could not find it in the "man" (manual) pages. I'm sure one of the others will tell you how to do it, though. It's something like creating a specially named file, but what I disremember is (a) the exact file name and (b) which directory to put it into.

If it's only a few sectors that are bad, doing the repair should do away with the message and prevent other problems.

Those numbers at the start of each message line are the elapsed run time at which the message was written. That's why they keep increasing as you go along.

To see exactly what is happening during the shutdown, you can open a terminal window and issue the command ```
shutdown -P now
```to see the messages that result. I would expect you to see the same errors you report, but there just might be a bit more detail...

EDIT: I just googled for the force checkup, and the line ```
sudo touch /forcefsck
``` (from a terminal window) ought to do it. Then do a "restart" and expect the bootup to take quite a bit longer than usual...

---

### Post by k3lt01 on 2010-03-15
> **JKyleOKC said:**
> EDIT: I just googled for the force checkup, and the line ```
sudo touch /forcefsck
``` (from a terminal window) ought to do it. Then do a "restart" and expect the bootup to take quite a bit longer than usual...It will also give you some warnings that it could cause file system damage and ask you if you want to continue.

---

### Post by Chris Edgell on 2010-03-15
I appreciate, greatly, the responses here...my dears...(see how I am...)

Having read presence1960 first, I proceeded with that plan.  When the back and forth motion of installing was finished some message flashed which I couldn't catch; then the screen went to the DOS prompt then went completely black.  I Waited some time and went and did it again...same thing happened.  Now I've waited a long time but the screen remains black.  I tried to remove the CD but it stays locked, so I'm wondering if this is possibly the long install that Jim talked about.

But now, I've rebooted to the installed XUbuntu and I'm wondering if I can run that sudo that Presence1960 instructed me to run in the CD OS, if I can run it in this regular installation that on here.  

You can discuss with each other what would be the next best course of action.  Do you all hold to what you've said here.  Jim, do you think what you suggest is, in your own mind, and knowing MY situation, is the best way to go?

---

### Post by presence1960 on 2010-03-15
> **Chris Edgell said:**
> I appreciate, greatly, the responses here...my dears...(see how I am...)

Having read presence1960 first, I proceeded with that plan.  When the back and forth motion of installing was finished some message flashed which I couldn't catch; then the screen went to the DOS prompt then went completely black.  I Waited some time and went and did it again...same thing happened.  Now I've waited a long time but the screen remains black.  I tried to remove the CD but it stays locked, so I'm wondering if this is possibly the long install that Jim talked about.

But now, I've rebooted to the installed XUbuntu and I'm wondering if I can run that sudo that Presence1960 instructed me to run in the CD OS, if I can run it in this regular installation that on here.  

You can discuss with each other what would be the next best course of action.  Do you all hold to what you've said here.  Jim, do you think what you suggest is, in your own mind, and knowing MY situation, is the best way to go?

I would not run that command from your OS if the OS has sda1 mounted. You can cause severe filesystem damage by running fsck on a mounted partition. If you try to do so you will receive a warning. I would then do what Jim suggests, I tried it and when I rebooted the filesystem check did run for me.

---

### Post by k3lt01 on 2010-03-15
IMHO you do need to fsck your disk.

[Here]("http://manpages.ubuntu.com/manpages/karmic/en/man8/fsck.8.html") is a little bit of reading for you if your interested. It is the Man page article Jim was referring to. While it is good to read these things you don't need to do any special commands right now. A simple fsck at the boot prompt will suffice.

---

### Post by Chris Edgell on 2010-03-15
I was feeling like I have so lettle to lose..anyway, I put in the sudo command that Presence recommended NOT for the actual installed system.

When I ran it I got this message:

I'm sending and then going to put the net connect into the Dell#2 and send you the screenshot...

---

### Post by Chris Edgell on 2010-03-15
...

---

### Post by JKyleOKC on 2010-03-15
Running fsck on a disk that's mounted is a definite no-no, and the standard boot process has to mount your /dev/sda disk, so it's not a good idea to try to run fsck from the normal boot.

Using the /forcefsck option that I suggested causes the boot process to load the fsck program into RAM, then unmount the disk, run the program, and on completion re-mount the disk. It normally happens at least once every 30 days or so anyway but you never see it in the standard boot process, because the "quiet" and "splash" options that are the default in grub hide the bootup messages. I edit the "/boot/grub/menu.lst" file on all my systems to remove those two options, so that I see all the advisory messages scrolling across the screen. That's because I like to know what is happening (or in some cases not happening) at all times, but many newcomers become greatly confused by all that data and think something is badly wrong -- so that's why the default is to hide them.

And I've never seen a warning that forcefsck may cause data damage; such a warning DOES appear if you try to run fsck on a mounted disk, though.

EDIT: your screen shot shows that you defined the drive as "/dev/sdal" rather than "/dev/sda1" so that's why the error message; it's the numeral one, not a small L...

---

### Post by Chris Edgell on 2010-03-15
Okay Jim, I'm about to try to follow your instructions.

DID I follow your instructions or have I done something not quite right?

Here we are:

---

### Post by ranch hand on 2010-03-15
Do run any fsck stuff from the live CD.  It must not be done in a mounted drive.

Better to use the terminal command to force a shut down than hold the power button down.

If that doesn't do it hit Alt+Sysrq +b.  This will force a reboot and and you can hit the power button when the bugger is shut down momentarily.

---

### Post by JKyleOKC on 2010-03-15
The -P has to be upper case; if it still doesn't work, use -h (lowercase) instead. The -P is supposed to force powering down, while -h simply tells it to halt. On most systems, the "halt" will cause it to power down anyway...

---

### Post by oldefoxx on 2010-03-15
Already 22 pages to this thread and no fix in sight yet?  Maybe I can help a bit.  My whole career was working on computers and peripherals, and I learned PCs on my own because there was nobody around to give courses on them.

Here are some key tricks.  The first is, find where the problem is located.  To do that, you have to swap things around.  That is,
if your hard drive works in a different PC, then it can't be the hard drive.  If another drive works in your bad PC, then you can see that this doesn't make sense, so maybe you missed something, like whether a drive connector wasn't hooked up right to start with.

But say you don't want to tear down a working PC just do do this.  What next?  See if you can get up and running on the LiveCD.  If so, then the PC is mostly working, which means you might be back to the hard drive again.  But that is progress of sorts.

The hard drive doesn't work in the bad PC?  If you don't have a second drive to stick in there in its place, maybe you can just rig it as the second drive on a working PC.  Get that PC up and running, then see what it can tell you about the second drive.  There are programs from off the internet that can rigorously test the drive and map out any bad sectors or sections found. 

When working with hard drives, the first one is Master and the second one is Slave.  This is important, otherwise the signals to the two drives mix together.  There are jumper settings on each drive to say which it is.  But if you prefer, newer drives have a setting for CS, meaning Cable Select.  But either both drives have to be set for Cable Select, or one has to be Master and the other Slave.  There is almost a small place on the drive shell to indicate which pins represent what settings, or you can look up the drive on the internet.

If you are interested, you can get USB to IDE or USB to SATA adapters so that the drive can be hooked up via a 2.0 USB port.  You could also use a 1.1 USB port if your PC is pretty old, but that is very slow compared to 2.0.  A USB connected drive will also bypass the hard drive controller, meaning if it works that way, maybe it is a controller problem instead.  Some USB adapters claim to go either way, IDE or SATA, and may even offer a 2.5" or 3.5" drive connector, meaning they work with laptop drives as well.  If you have a drive that works via USB, that is not a bad way to leave matters, assuming that your PC Setup will let you boot via USB.  Many don't. However, if a hard drive controller is deemed bad, a PCI card to do that job is not too expensive.

I like USB drive connectors, because they turn any internal hard drive into an external one, either temporarily or permanently.  That way you get continued use from working drives even if the PC they came in are judged to be dead.

Trying to work with a PC that isn't booting to test a hard drive that might be bad is not the way to go.  You have to determine what is bad, or where the problem lies, and then go from there.
We use to call it Easter Egging, meaning you have to look in every spot for where the eggs might be hiding.  You can't just assume that there are no more, or that everybody else has found them all.  Unless you check yourself, you don't really know.

There are CD images on the internet that provide a lot of little programs that can help.  They can test all sorts of things, and some can do a good job reviving hard drives that just seem to have gone bad.  Use a search engine, use words to express what it is you are searching for, then check out the links that come up.  You may not find what you want the first few times around, but what you do find may help you pick search words that will get you closer on the next search.

---

### Post by Chris Edgell on 2010-03-16
Hi oldefoxx,

Happy to see you here.  I had just began to read your post but wanted to write and defend the people helping me.  This thread is about 4 computers and there have been so many things fixed...there have been so many problems that I've even created along the way...so please don't think that you're going to be the hero on a white horse coming in to help a bunch of ineffectual fools.  Truthfully, I'm the only one who comes close to THAT description.  So, much as I like you, please show a little respect for the people who help me so patiently...even to having to continually correct me for the small case p instead of the capital P.  You see what I mean...but I beg you, don't go away mad, because I call you out a little bit for your high-handed remark...it may be only the one...I may be the goofball (I shouldn't call myself such names, even in extreme hyperbole...egalvan will chide me...) jumping the gun...forgive me, as I said I'm truly happy to see you.  These guys have been trying to work together...they have more or less taken me under their wings..and I deeply appreciate them.

And blessings on your head too.

See, I jumped on you too quickly...your one sentence wasn't THAT bad...sorry oldefoxx, forgive me.
Chris

---

### Post by Chris Edgell on 2010-03-16
See, now I think I probably made everyone feel bad or at least uncomfortable...Sorry all.  It is getting late and this is really something for me to study.  You guys have been so patient with me, and haven't been afraid to present it all in truly simple terms.  That in itself is truly an art and to remain humble as you teach one who is comperable to a fifth grader is not just an art it is a gift to God, or whatever you call whatever is higher than you.  PLEASE go see:  [http://www.ted.com/talks/taylor_mali_what_teachers_make.html](http://www.ted.com/talks/taylor_mali_what_teachers_make.html)   It is a great little 4 minute stand-up act about teaching.

So I sure will be studying this in the next couple of days (I have a pretty demanding social calendar this coming week)...I can get on here but that wouldn't be too fair if I don't study all you all have been trying to teach me.

And oldfoxx, I really will have to study just to comprehend what you are addressing...I barely know what you're trying to tell me...but I think I can plow through it and see if I can grasp thye essence of your post. 

What I really need is for one of you, (like audiomick) to find me the hard drive for these Dells so that I dare to try anything oldefoxx talked about.  I DON"T dare to mess with my good one and as the title of this thread says...two of them can be ruined...I have done so many hard shutdowns.  I even remember the guy a couple of years ago who told me that it doesn't hurt to shut down with the power button.

I do need a break after messing up with that l and that P.  I end up feeling a little A-D-D.

And so good night.

---

### Post by egalvan on 2010-03-16
> **Donald1715 said:**
> WOW... some thread. Just a few comments:


If a systems bios is not detecting a hard drive, it's for the following reasons:

The jumper is set wrong on the drive. Most are set to CS, but sometimes it needs to be set to Master/Single if it's the only drive in the box.

It's a mighty rare BIOS that will **fail to detect** a drive because the jumper is set to CD or Master or Slave...
the BIOS code sends a ID_Req down each enabled channel,
and sets up any drive that answers. Doesn't matter the jumper...
Confilicting jumper setting *can* confuse the code, but that is another fish to fry. She only has one drive.

> 
The IDE cables or 4pin power cables are dirty (blow out with canned air) or kinked.

Removing and replacing will usually clean the contacts, as the contacts are of the "sliding contact" design.
And the "dirt" is going to be of the "oxide" variety (rust).
Regular dust is rarely a problem in contact areas.
And unless the kinking is severe enough to have physically damaged the cable, it will not be a factor.

BTW,removing and replacing is almost always a good idea to clean the contact area on almost all components of an older computer.
Expansion cards, RAM, CPU, cables, cords, etc.
And removing the old thermal paste from the CPU and applying new will usually "Be a "Good Thing"


> Someone has messed with the bios. In which case you can set it to default settings.
Resetting the *entire* BIOS can be a radical solution (it will reset anything else you may have set, such as date/time), but can sometimes be necessary.

The main reason to reset the CMOS on the Motherboard **(and no, pulling the battery won't reset it, you have to change a jumper setting on the MB to do that,** and you'd most likely need your motherboard manual to know which jumper) is if you have set a "power on" password for the Bios, and forgotten it. Resetting the CMOS clears the password back to the default.[/quote]

And yes, pulling the battery **will** clear any desktop BIOS.
BTW, Laptop BIOS have a different architecture, which is security-oriented. Pulling the battery usually has *no* effect, and there are *rarely* jumpers on-board. At times, special "dongles" are available to reset lappie bios's.
And some lappie makers require completely changing the EEPROM chip in order to "reset" the passwords (which usually entails replacing the mobo) (again, security mind-set here)

And most Desktop BIOS jumpers will be labeled,
they will almost always be near the battery,
but if not, then a visit to the website for the info (or manual) is needed...

And it's a rare desktop BIOS that the CMOS_reset, and the reset jumper, and removing V+ for a specified time would have different results...
normally, all three actions result in the same clearing of the EEPROM area of the BIOS (which is where the data is stored)

> For all the people here having troubles with partitions... I never make more than two partitions. One for the OS, and a small one for the backup restore copy of the OS. For instance, if I have an 80gig drive, the first partition would be 60gigs, secondary 20gigs. When I make a Ghost image periodically, it goes in the secondary partition.

Good advice.
But is making three partitions any harder than making two? :)
It's the jump from one to many that stumps most folks...
"Two is an irrational number, and should not exist"
*The Gods Themselves* I. Asimov

On my drives, I always make three primary, and one extended.
This gives me the maximum flexibility.
And I almost always use PartedMagic, an excellent LiveCD distro dedicated to drive partitioning, formatting, recovery, etc.
YMMV

> For running other OS's, here's some food for thought. Try a mobile rack such as Vi-powers super-rack. They are cheap, under $20 and once you install it into your case in a free 5 1/4" drive bay, you'll never have to open your case again to access your hard drive. Now you can have a drive for WinXP, another drive for Linux, another for whatever... If one OS is giving you a hard time or crashes... it's easy as opening a drawer to remove that drive and slide in a new one with a working OS. I've been using mobile racks for years and they are great.

Again, good advice. It seems to me that the use of these racks has diminished a lot. They used to be much more prevalent in years past.
I myself find that only one of my machines has a rack still installed, when I used to have one on every tower in my house/shop.
I wonder why? I'll have to ponder the notion.

---

### Post by ranch hand on 2010-03-16
egalvan
I agree with almost everything you say.

I do beg to differ on the number of primaries.  I only have one 20 to 30Gb and the rest is extended.  I believe this is more flexible.  I actually have a couple drives with only 1 extended partition but I would not recommend this to anyone.  That is real flexible though.

I do have 12 OS' on one external enclosure (test platform), 7 of which are some variation of 10.04, the others are there to see how 10.04 gets along with them and to be there in case I screw all the 10.04 installs.  This is down from 22 on the same drive last testing cycle.

That is why I do not waste flexibility with 3 primaries.  I have set up systems with 3 primaries myself but they were for normal people, not me.

---

### Post by audiomick on 2010-03-16
> **ranch hand said:**
> ...but they were for normal people, not me.
*chuckle*

Hi Chris.
First of all, I have noticed a few posts from oldefoxx, and I think he knows what he  is on about, but I do wonder if he went through the thread or just jumped in at the end? 
Anyway, what he is telling you can be boiled down to a couple of points:

Fault finding must be an orderly and systematic process. You have already had advice in this direction, maybe without having had it put this way. The principle is the same, whether it is a computer or a car or a washing machine or a sound system: If your system has a fault, swap out the components one at  time and see if the problem goes away.
This is what the advice about swapping drives around is about.

The point about the drive being master or slave is valid. It has also been dealt with by egalvan and a couple of others. However, as egalvan also pointed out, you have only one drive in each of the machines, so you don't need to worry about that for now.

Incidentally, the comments about unplugging and plugging back in the cables are not to be ignored. You have already noticed this yourself, haven't you? I think I remember something a few days ago where you pulled the cable, plugged it back in, and all was well. That would be worth trying on the connectors on the drive, if you haven't already.
Incidentally, I did that to mine just the other day. It didn't want to start, apparently had trouble finding the drive. I opened it up, fiddled with the connectors (SATA, and I ask myself who designed the connector. It is crap.) and now it seems happy again. The machine is only about 2 years old...

The comments about USB and USB enclosures are no doubt all correct, but I think that might confuse things for you at the moment.  The principle is, there are cases you can get for mounting drives in. You take the drive out of the computer and put it in this external box. The box has a little tiny "brain" and a USB connector. The "brain" in the box makes it possible to connect the drive to the computer via USB instead of the normal connection. 
The advantage of this that oldefoxx is talking about is that this means that the drive is being accessed by the computer a different way; another way of swapping out components to see if things get better.
If the drive works in the USB enclosure but not on the normal connection, then you know that the "talking to the drive" part of the system has a problem, and not the drive itself.
As I said, this is all well and good, but I think you have enough possibilities to find your problems without adding another variable to the equation. If and when that becomes neccessary, someone will surely be able to guide you through it, but just "put in on the side for later" for the time being.;)

This
> Trying to work with a PC that isn't booting to test a hard drive that  might be bad is not the way to go. is certainly true, but don't worry. You have enough possibilities available that you don't have to be in that situation.

I'll leave you with that for now. Hope it helps, and I hope I didn't tread on oldefoxx's toes...;)

---

### Post by Chris Edgell on 2010-03-16
ranch hand always makes me laugh.  Thank God for small favors...  Nice to see you again egalvan..you must have noticed you got an honorable mention...even in your absence.

So many interesting comments and points in response.

As I said, I'll be glad if I can , within the next 6 months, get into the stability of a LTS (long term support?!) release...WILL that be at the end of this month, Lucid Lynx (?)

I really WANT to explore different partitions but I have only had the nerve to check the box "Install on entire drive".

See how life moves along for me...well I hope the PCI card fixes the AMD aka JYD because I thought I had almost got 3 out of 4 working but now I'm almost back to ONE... Don't YOU lose hope, but of course you can quit if you get sick of me.

I swear, I'm going to ask my friend if she'll give me one more Dell, so that I'll have a control group again.

As I mentioned I want to get a hard drive from ebay or wherever...but I can't make audiomick do all the work like he did finding me the PCI card...I've got to find out about replacing this hard drive by myself.  (I say that, but secretly hope someone will send me the link and I'll soon have my niece tell me it's on the way)...sounds like a cushy life, doesn't it?

     "If the drive works in the USB enclosure but not on the normal connection, then you know that the "talking to the drive" part of the system has a problem, and not the drive itself." quoting audiomick  What a great sentence, it clarifies a lot for me...It's what I'm really trying to find out with these TWO hard drives.

I thank you all for the fine sparking of my day.

---

### Post by Sir Jasper on 2010-03-17
Hi Chris,

I have found a free and simple cloning program, Dr Freeware ([http://www.drfreeware.org/download.html](http://www.drfreeware.org/download.html)) which you may like and find to be particularly useful.

The download you would need is the 300 Mb zip file. I downloaded it to my Xubuntu Desktop and unpacked it. Then I used the Brasero option ¨Burn Image¨ with a blank CD in its drive and then browsed to select the ¨DrFreeware.iso file¨

I then rebooted from the CD (fedora linux OS - which may of itself be of interest) and used the highly self-explanatory Drive Dumper tool.

I have, just for you, tested it today; successfully cloning my Xubuntu partition (I do not have a separate Home partition) from my main internal hard drive to a same-size partition on my secondary internal hard drive; then I cloned it back with no problems.

If you can make a secondary internal drive by moving one of your 20 GB drives to a ¨test¨ computer you could either clone from 20 GB primary drive to the ¨new¨ 20 GB secondary drive (instead of cloning from partition to partition]. You could alternatively or additionally  clone to a [probably partitioned] USB external hard drive, but the data cloning rate might then be more like 12 GB an hour.

My regards

PLEASE NOTE:
It is for data rescue, backup, migration, or computer forensics etc and for transferring important data from a faulty Drive if the partition table or file system is damaged, or it  has lots of bad data blocks. However, if possible, I would prefer to test my drives before cloning.
For NTFS, FAT, UFS 1, UFS 2, EXT2, EXT3, and ISO 9660 are supported; ***BUT NOT EXT4***.
For IDE/SATA/USB Hard Drives, memory cards, USB Memory Drives. For those able to boot from a USB stick that can be used instead of a CD.
Gparted is also on the disc - (and for information a Data Recovery program for accidentally deleted files and also avast! Antivirus, linux version)
On my ancient computer The fedora CD took 2 minutes to load and the cloning rate (internal drive to secondary internal drive) was about 24 GB an hour.

So it makes 1 to 1 copies (i.e. including free space}. I have not tried Clonezilla, which most likely has a faster cloning rate and I seem to recall it can also make Smart Copies [i.e. does not spend time cloning free space], but especially for cloning a smallish drive or partition speed may not be of the essence. I anticipate some of your many friends will add their expert comments, criticism and suggestions. 

FOR WINDOWS USE ONLY:
There is a separate 5 MB download for cloning 2K / XP / 2003 / Vista / 7 (NOT 9x) from within Windows.

---

### Post by ranch hand on 2010-03-17
I move OS' around all the time and have never used any of those cloning "tools".  I have one built into any Live CD and installed on all my OS'.

It is called gparted.  Simple copy/paste operation to move OS'.  It is true that you do have to make sure that the /etc/fstab file is correct before trying to boot  to the moved OS but that is fairly self explanatory.

Maybe I am just weird.

---

### Post by Chris Edgell on 2010-03-17
Today I watched a video from computerscience1.org  It is the Harvard extension course about computers.  I was inspired to try to remove my hard drive.

This is the Dell #2; the one that originally couldn't detect the hard drive.  After wiggling the place there the IDE cable connects to the motherboard, and wiggling the connections on the "top" of the hard drive...and then it COULD detect the hard drive.  I had gone ahead and installed the XUbuntu...then just this last week I was getting the message, "Unable to shut down".  These last couple of pages have been about if that HD could be corrupted.  

Now I am truly embarrassed (again) to say that after removing the IDE cable and plugging it back into the hard drive it is working correctly again, with the shut down and all.

I was unable to disengage the piece that I would have to call the wiring connection.  Shall I just pull harder to get it to come off?  I was afraid to force pulling it off, but that IS how they showed doing it on that video.  (Is it the oxidization holding it in place?)  I wanted to be able to remove the hard drive from the machine...so that would require pulling this "plug" out.

If I had it all to do again I would follow Exodist's original post to me way back when I was asking on that thread "Re: Can a real noob learn by doing-with chance for free computer?"  See:  [http://ubuntuforums.org/showpost.php?p=8637658&postcount=25](http://ubuntuforums.org/showpost.php?p=8637658&postcount=25)  
Go read THAT post.  If I HAD followed that good advise then...all this would not have happened twice.  Still, I gotta' say how much I learned and to have it happen twice...it has really impressed me with the huge importance of good connections.  I am going to change my ways and see if I can do these three machines right step by step. 

Although I must ask, along with that question of pulling that connection off the HD.  Shall I?  And shall I pull all the connections up and clean...pull the CPU up and put that seal as Exodist said about the real cleaning job.  I have the urge to do it with this Dell...'cause, why not?

What do you think?  Or shall I go piece by piece as I have been doing.?

I don't think you're weird, ranch hand....but I am about to make myself laugh out loud...

Sir Jasper, you sure seem to love to advocate cloning.  I NEVER see it mentioned elsewhere  and wonder how you came to be so gung-ho...hope you're not offended by the vernacular.

---

### Post by Sir Jasper on 2010-03-17
Hi ranch hand,

I am in no doubt that your knowledge of ´buntu is as a lake by comparison with my pond; but whatever magic tricks you can perform, they are not so quickly, easily and accurately performed by Chris and myself. Although I do, as a limited security measure, copy and paste from my Home directory to another partition in a few minutes

I think cloning is a much simpler solution for the uninitiated and it would be great if you could advise Chris since you will have also some feel for her weaknesses. 

So with your Grubbing expertise, suppose that Chris could clone from a primary internal drive to a second (or even third as in your case) internal drive then it seems to me that booting from the second (or third) drive would virtually prove that the clone was hunky dory and equally importantly that that drive should be reliable. and a clone back could be undertaken with safety.  

My regards

PS It&#347; 2am here and I&#7743; away until next Monday so I&#314;l check back then.

---

### Post by audiomick on 2010-03-17
Hi Chris,
you just "caught" me. I have been meaning to go to bed for the last 45 minutes....

> **Chris Edgell said:**
> Today I watched a video from computerscience1.org  It is the Harvard extension course about computers.  I was inspired to try to remove my hard drive.Great, good on you!

> This is the Dell #2; the one that originally couldn't detect the hard drive... after removing the IDE cable and plugging it back into the hard drive it is working correctly again, with the shut down and all. That is telling us that that connector might be a bit dodgy, or just have some stubborn corrosion on it. If you get similar problems again, you know where to look. If it comes up again, you might want to think about cleaning the contacts or replacing the cable. For now, I would just see how it behaves for the next couple of weeks.

> I was unable to disengage the piece that I would have to call the wiring connection.  Shall I just pull harder to get it to come off? The way to describe the correct approach would be "cautious determination". Those plugs can be stubborn, but I wouldn't force anything. Have a good close look at it to see if there isn't some kind of locking thing on the connector. I haven't seen an IDE connector for a few years now, and can't remember if they do or not.

> Although I must ask, along with that question of pulling that connection off the HD.  Shall I?  And shall I pull all the connections up and clean...pull the CPU up and put that seal as Exodist said about the real cleaning job.  I have the urge to do it with this Dell...'cause, why not?Having a good look around inside is a good idea. Make sure all the cables are plugged in right, even un-plug and re-plug things (with due caution). If you want to pull things apart on a grand scale, remember to label things before you start, maybe take some photos.

As far as the heat paste under the CPU goes, yes, it is probably a good idea to renew that. The paste is there to make sure the heat can get out of the CPU into the heat sink properly. However, I have never done this. I can't say how difficult it is, but I know that if you get it wrong, it could fry the CPU in the course of time. Wait and see what a few others say about attempting that. I think it is not hard as such, it is just a matter of knowing what to watch out for,  how much of that heat paste to apply and so on.

Time for me to go to bed now, I think. It is after 2 in the morning here...:o

edit: Sir Jasper isn't the only one who advocates cloning. I have seen it referred to a lot. It is a recognised way to do backups.

---

### Post by Chris Edgell on 2010-03-17
very good audiomick

Good night...

---

### Post by Sir Jasper on 2010-03-17
Hi again,

I am not at all religious, but even I know the parable of the wise and foolish virgins.

Having read your post I am not at all offended and it is entirely your decision if you choose not to wear your life belt when at sea in a small boat in a gale.

---

### Post by audiomick on 2010-03-17
> **Sir Jasper said:**
> Hi again,

I am not at all religious, but even I know the parable of the wise and foolish virgins.

Having read your post I am not at all offended and it is entirely your decision if you choose [COLOR=Blue]not to wear your life belt when at sea in a small boat in a gale[/COLOR].
not that we want to put you under any pressure or anything....;)

---

### Post by ranch hand on 2010-03-17
Isn't it amazing how easy it is to make life tougher than it needs to be?

I am not sure which cable you are pulling on.  If it is the ribbon, there are a lot of very small pin connectors in that plug.  They are a tough pull if not oxidized.  Haul off and horse that sucker off and put it back on a couple of times.

The other connector is your power connection and it is usually easier to get off but still may require some force.

Just be sure not to pull on anything but the plastic plug itself.  Do not pull on the ribbon or the wires or you may bugger them up (not expensive to replace).

I would leave the CPU alone for now.  Wait until you decide to put in a Mother Board or something to try messing with that stuff.   There is such a thing as trying to learn too much at once.  That said I am all in favor of learning the advanced stuff first and then learning the basics later.

Someday, if you can afford it, get yourself a modern box that sues SATA drives.  The connectors are amazingly smaller and none of this "master" and "slave" crap.  Our new box run SATA and I am just going nuts swapping drives around because it is so easy.

---

### Post by Sir Jasper on 2010-03-17
Hi audiomick,

Chris actually does need pressure to steer a sensible course. She has four machines and yet wants another (to what immediate useful end).

I have tried to help Chris occasionally, but though I am not a nursemaid I try  (unimpressed as I am by melodrama) to give her good honest advice flavoured with a sense of priority.

My regards

---

### Post by Chris Edgell on 2010-03-17
I know I should, or could be looking at all the options for backing things up.  I am afraid that I am in a tempest in a teapot as opposed to a gale force wind out upon the vasty deep.  So you see...I am not afraid.

Which is to say, I have my files on a CD and there are so few of them; I have nothing really to fear  I'll admit I want to learn partitions and gparted and even external hard drives or USB backups...but right now the need is only theoretical.

As far as cloning, I WILL read about it and see what I can see.  Right now the only thing I would HATE to lose is all of my bookmarks.  Remember when I shrunk them to a PDF I think, and put them on my new computer.  I would like to have a copy of all those.  I HAVE been thinking about looking into it.  It seems like when I compressed them before it not only copied but cut in that way of getting them into another machine.  I'd like to put them on all three of my other machines, at least on the two that basically work.  

Hey, maybe I'll do the deeper cleaning on that #3 Dell that is sitting quite nearly defunct right now.  Maybe I'll do that tonight, rattle the connections...

---

### Post by ranch hand on 2010-03-17
> **Sir Jasper said:**
> Hi ranch hand,

I am in no doubt that your knowledge of ´buntu is as a lake by comparison with my pond; but whatever magic tricks you can perform, they are not so quickly, easily and accurately performed by Chris and myself. Although I do, as a limited security measure, copy and paste from my Home directory to another partition in a few minutes

I think cloning is a much simpler solution for the uninitiated and it would be great if you could advise Chris since you will have also some feel for her weaknesses. 

So with your Grubbing expertise, suppose that Chris could clone from a primary internal drive to a second (or even third as in your case) internal drive then it seems to me that booting from the second (or third) drive would virtually prove that the clone was hunky dory and equally importantly that that drive should be reliable. and a clone back could be undertaken with safety.  

My regards

PS It&#347; 2am here and I&#7743; away until next Monday so I&#314;l check back then.
In the case of Chris and her drives, as there is nothing of importance on them currently, I would swap in a drive and install on it or use whatever is on it now.

Installation is so fast with Linux, Ubuntu particularly, that transferring all the data is usually slower than a fresh install if you do not need to transfer a lot of files.  You also do not transfer all your mistakes (I am good at making some really bad ones - as in - gee I wonder what would happen if I did this?).

A lot of folks do upgrades from version to version and then spend a lot of time getting the files cleaned up and this and that.  I do a fresh install and transfer the files I want on to it.  RW CDs and DVDs are cheap and reusable if you do not have an extra drive to back up to.

That is where I think cloning or, I think, using remastersys is great because you can put what you want an a CD or DVD as back up.  Remastersys alows you to make a live CD of your installation.  If you do it on a regular basis you can really fry your OS and just reinstall it to exactly where it was.  Kind of neat.  I have only tried it once but a lot of the respin distros based on Debian or Ubuntu are made using it.

---

### Post by overdrank on 2010-03-17
To all, this thread has changed topic many times. I can not review all the thread. Not enough time tonight :) 
Do you think it is time to move on.

---

### Post by Sir Jasper on 2010-03-17
Hi again ranch hand,

I did not rush and spent some 10 months getting Xubuntu to my abolute satisfaction (though I do have some seemingly unimportant, but unexplained anomalies).

I have forgotten how I achieved that personal utopia and I would really hate to lose any of the advances I have made - so I clone and I upgrade.

With Chris having so many apparently ¨identical¨ computers it seems to me that that if the hardware is identical, then cloning from one reasonably good environment would create another with identical properties.

My regards

@ overdrank,

This thread is a classic example of what not to do; but things are where they are and I have only the welfare of Chris in mind and in a roundbabout way I am trying to bring it to a conclusion though surprisingly [to me] it does seem to engender a lot of interest

---

### Post by ranch hand on 2010-03-17
> **overdrank said:**
> To all, this thread has changed topic many times. I can not review all the thread. Not enough time tonight :) 
Do you think it is time to move on.
Chris,
This is probably a good idea for anyone that may have similar problem  to be able to follow.

Why don't you start a new thread for this current computer and post a link here so that those of us that want to follow the saga can do so?

---

### Post by k3lt01 on 2010-03-17
I sort of agree with overdrank, although after 4 weeks I think its a bit late for moderator attention. > **Sir Jasper said:**
> @ overdrank,

This thread is a classic example of what not to do; but things are where they are and I have only the welfare of Chris in mind and in a roundbabout way I am trying to bring it to a conclusion though surprisingly [to me] it does seem to engender a lot of interestI personally don't fell that you, I, or anyone else apart from Chris and the moderator team have the right to bring this to a conclusion. Methinks you take way to much responsibility upon your person.

Those of us who have been with Chris through this "epic voyage" know where she is up to. Others have joined in at various points, not knowing because they haven't read the thread, and have made comments without actually realising that the issue they were talking about has been fixed. Others still HAVE read the entire thread and have been compelled to make positive comments about it. The point of all this is, each to his own.

---

### Post by presence1960 on 2010-03-17
> **k3lt01 said:**
> I sort of agree with overdrank, although after 4 weeks I think its a bit late for moderator attention. I personally don't fell that you, I, or anyone else apart from Chris and the moderator team have the right to bring this to a conclusion. Methinks you take way to much responsibility upon your person.

Those of us who have been with Chris through this "epic voyage" know where she is up to. Others have joined in at various points, not knowing because they haven't read the thread, and have made comments without actually realising that the issue they were talking about has been fixed. Others still HAVE read the entire thread and have been compelled to make positive comments about it. The point of all this is, each to his own.

+1

I agree. I have tried to lend Chris a hand on other threads she had started & from what I have got to know about her is she wants to learn more about linux and computers in general. As long as the threads are following that course they are legit threads. We all had to start at the beginning at one point to get where we are now. No one begins as an expert.

Case in point: Chris just learned a valuable lesson about hard disks when not detected or operating properly. She opened the case and checked the connections to/from PSU and hard disk & mobo and hard disk. Problem solved. 

Although this thread does not deal entirely with linux OS, it is within the scope of acceptable help. Hardware problems unfortunately are still prevalent in the linux world.

---

### Post by Chris Edgell on 2010-03-17
> **Sir Jasper said:**
> 

@ overdrank,

This thread is a classic example of what not to do; but things are where they are and I have only the welfare of Chris in mind and in a roundbabout way I am trying to bring it to a conclusion though surprisingly [to me] it does seem to engender a lot of interest

Oddly enough, it was Sir Jasper who told me to keep it going.

  	
 4 Weeks Ago 	  #11
Sir Jasper


Xubuntu 9.10 Karmic Koala
	
Re: I think I've ruined my hard drive - if not more also.

Hi again,

I suggest you keep this thread going, but halt further action pending detailed advice and then probably mulling things over for a few days before deciding what to try next.

There are many possibilites (and complexities eg upgrade ideas) to think through.

I&#7743; off to bed now as it&#347; 3.40 am here. I&#314;l revisit in a few days for your latest news.



I tend to think that these are very sour grapes.  I am sorry to be thought so poorly of by Sir Jasper.  I always thought if people didn't like it they could NOT post.

But I would not want to stir any passions that would get this thread jailed, there has been too much good information in it for me to lose it that way.  I want to always be able to refer back to stuff I learned here.  

So to keep this thread from falling into jeopardy, I REQUEST it to be closed.

Thank you all, you've been great.
Love
Chris

..

---

### Post by redmk2 on 2010-03-17
> **Chris Edgell said:**
> ...
So to keep this thread from falling into joepardy, I REQUEST it to be closed.

Thank you all, you've been great.
Love
Chris

..

Wait, wait, waaaaaaaaittttttt.  This is my favorite nightly soap opera!

Have the mods move it, but don't close it!

Love you all,

-Red

---

### Post by presence1960 on 2010-03-17
> **Chris Edgell said:**
> 



I tend to think that these are very sour grapes.  I am sorry to be thought so poorly of by Sir Jasper.  I always thought if people didn't like it they could NOT post.



Thank you all, you've been great.
Love
Chris

Chris don't close the thread because of a comment. In my experience in here if I took it that much to heart what some people say directly to me I would not continue to be active in here. I say my piece and let them say theirs, then I move on. No one is that important or has that much power over me. It is strictly my decision to allow others to have their say, deal with it at that moment and then move on that allows me to continue in here and in life.

---

### Post by k3lt01 on 2010-03-17
> **presence1960 said:**
> Chris don't close the thread because of a comment. In my experience in here if I took it that much to heart what some people say directly to me I would not continue to be active in here. I say my piece and let them say theirs, then I move on. No one is that important or has that much power over me. It is strictly my decision to allow others to have their say, deal with it at that moment and then move on that allows me to continue in here and in life.Do what I have just done in another thread, reply and say all other comments via PM. Big egos and nasty words are not very Ubuntu-ish and should be kept in private between the people with the issue.

---

### Post by Chris Edgell on 2010-03-17
What you say is very good...I have to tell you about an employee in my apt bldg -- there are 26 stories, 20 apt on each floor.  One office worker told me, "Chris just take what YOU can use and leave the rest alone..."  I was greatly impressed.

Three weeks later she quit...LOL

Sometimes I like to allow the great divide.  Like the tide rolling out.  I don't view this action as cowardice but of character.

---

### Post by Razorback on 2010-03-17
I have been following this thread.  We all struggle with new things and it is good because we learn.  One interesting thought is that, surely in an area as big as Chicago, there could be hands-on help to work through the hardware issues.  I think it is noble to provide these PCs to others for email, etc.  I maybe speaking out of turn but maybe one of the local LOCO groups has a member that could help out.  Just a thought....

---

### Post by presence1960 on 2010-03-17
> **Chris Edgell said:**
> What you say is very good...I have to tell you about an employee in my apt bldg -- there are 26 stories, 20 apt on each floor.  One office worker told me, "Chris just take what YOU can use and leave the rest alone..."  I was greatly impressed.

Three weeks later she quit...LOL

Sometimes I like to allow the great divide.  Like the tide rolling out.  I don't view this action as cowardice but of character.

I don't think it is cowardice. I think this thread is useful not only for you but for all. New people trying ubuntu who may not be real computer savvy can read this and garner encouragement and confidence. More experienced computer users can read this and be reminded just what it was like at the front end of the journey- that yes they too had struggles and issues in the beginning. Sometimes that is easily forgotten by some.

Of course whatever action you decide to persue I will respect.

---

### Post by JKyleOKC on 2010-03-18
> **Chris Edgell said:**
> I was unable to disengage the piece that I would have to call the wiring connection.  Shall I just pull harder to get it to come off?  I was afraid to force pulling it off, but that IS how they showed doing it on that video.  (Is it the oxidization holding it in place?)  I wanted to be able to remove the hard drive from the machine...so that would require pulling this "plug" out.If that piece is the small almost-clear plastic plug with four individual wires going to it (usually located at the lower right corner of the back of the drive) it's your power connector for the drive, and the tech name for that kind of plug is "Molex connector" (Molex is the name of the original manufacturer of them). Unlike the ribbon cable connector, which is the one with 40 small holes for pins and which carries the data and control signals, my experience has been that the Molex ones are almost impossible to get free. I usually have to grip the plastic with pliers and use a large screwdriver as a crowbar! However so long as you're putting all the strain on the plastic, not on the wires themselves, I don't think you can do a lot of damage...

Molex connectors are also used several other places inside older boxes. For example, almost all of my fans are powered through them, although a few of my fans use smaller 3-contact plugs. Disk coolers, which I've added to several machines, also use the Molexes.

I second the advice about SATA drives, but it really takes a newer motherboard to get full benefit from them. My two newest machines both use SATA drives; the newest is a Compaq that I picked up (less monitor) at Office Depot last October for less than $325 including tax. It's amazingly fast and serves as my router, firewall, and in addition is my production machine for database recovery. The other one was built by my son some four years ago and at the time was state of the art, but it's noticeably less peppy than the newer one although both processors are rated for similar speed and both have 2 GB of RAM. Both are much faster than my older systems, however, which are running with 80-GB IDE drives and much smaller amounts of RAM. All, of course, are running Xubuntu 8.04.4 LTS (and I just may stay with Hardy even after the new LTS comes out next month).

---

### Post by Chris Edgell on 2010-03-18
Well, that's a real nice post, presence 1960.  You make a good point.  Now that I have requested it closed, shall I rescind my request?  Shall I contact them and say I've changed my mind?  It makes me want to go back through it and take out what I want to keep.  Will they always let me go back through it, even if it gets locked?  I don't really know how that works.  Oh yeah, I do think anyone can look at a locked thread; it's a jailed thread that can no longer be read, isn't it.

Oh, hi Jim, very informative...and just what I was wondering.  Very good.You remember, I really had liked Hardy too and was sorry when my first helper put Jaunty in.  Now I can't remember what the differences are.  But it does have one more year of long term support, doesn't it?  Makes me want to burn it and put it one of these machines just to refresh my remembrance.  

I could look for help elsewhere, I just wanted to see if I could do it with just me and the people on the forums and it has proven to be more than adequate help, Razorback.

---

### Post by presence1960 on 2010-03-18
> **Chris Edgell said:**
> Well, that's a real nice post, presence 1960.  You make a good point.  Now that I have requested it closed, shall I rescind my request?  Shall I contact them and say I've changed my mind?  It makes me want to go back through it and take out what I want to keep.  Will they always let me go back through it, even if it gets locked?  I don't really know how that works.  Oh yeah, I do think anyone can look at a locked thread; it's a jailed thread that can no longer be read, isn't it.



I am not sure how that works Chris. maybe a mod can answer that for you.

---

### Post by Chris Edgell on 2010-03-18
overdrank says we don't have to close this thread but he has said, it could be closed and do topics one by one.  The thing I have liked so well is to be able to bring up many points that I need clarified and to NOT have to stay strictly on the topic of one specific problem to be solved.

Also he has told me that we can always read locked threads, just not post any more comments; only a jailed thread gets removed and made totally unavailable.

BUT JIM, as I read your last post, I see where you say that this new COMPAQ now serves as your router.  Can you tell me what that means, how it works??!!  (Or is it something so extremely advanced that you see no point in going into it?)

---

### Post by Razorback on 2010-03-18
> **Chris Edgell said:**
> 
I could look for help elsewhere, I just wanted to see if I could do it with just me and the people on the forums and it has proven to be more than adequate help, Razorback.

No, I didn't mean to look elsewhere.  I was implying that hardware issues can be tough to identify and that you could try to see if a fellow ubuntu forums person was local to give you additional help with that.  Sometimes it is easier to be there in person to see what is going on.  I know I have had an easier time helping family members with their problems sitting at the PC.

---

### Post by Chris Edgell on 2010-03-18
Oh, thank you for the clarification.  Yes, I must admit sometimes it's hard getting the picture from Youtube and/or computerscience1.org.

I have family always going to Arkansas, John Brown Univ., I believe.

Oh, you must like Hardy Heron too?!  (Did you see me mention it to Jim Kyle, who uses it?)  Oh, now I notice ranch hand uses it also.

---

### Post by Razorback on 2010-03-18
> **Chris Edgell said:**
> I have family always going to Arkansas, John Brown Univ., I believe.

Oh, you must like Hardy Heron too?!  (Did you see me mention it to Jim Kyle, who uses it?)

John Brown is near here - about 20 miles.
Right now using Hardy Heron.  Not using Ubuntu exclusively but will upgrade next month to Lucid.  I like the LTS versions - don't have to tweak too much to get it going.  I do like Linux though.  Wish more companies wrote software for it - then I would use it exclusively. ;)
I do feel for you - Dells can be a pain to work on - they don't used standard hardware - even there power supplies aren't available except through them.

---

### Post by ranch hand on 2010-03-18
There may well be a "lug" in your area too (Linux Users Group).  My son, who lives where there is a population, says they are very helpful.

There is one in Billings MT, only 175 miles from here.  I have never had anything to do with them because I never go to Billings.

---

### Post by Chris Edgell on 2010-03-18
Well, after all this, I just came on to tell you that I got the PCI card, put it in and after going to the System>Sound>Hardware and then output...
Ta-Da I have SOUND.  This is the AMD that has the 80GB hard drive (as opposed to the Dells with 20GB HDs, and no room for adding on the INSIDE, additional HDs) and what looks like room for inserting another. Also remember that this is the ONE machine with Karmic installed (which is why I have that System>Sound>Hardware GUI at all.) 

So now after such a low point, three out of 4 seem to be up and running.

That third Dell, I plan to swap out the hard drive, (well after first removing and reconnecting it...it may be like #2, just a connection problem).

Again, and as always, I thank you all.
Chris

---

### Post by audiomick on 2010-03-18
> **Chris Edgell said:**
> Well, after all this, I just came on to tell you that I got the PCI card, put it in and after going to the System>Sound>Hardware and then output...
Ta-Da I have SOUND. ...
Hey, great news! And isn't it a great feeling when something like that works that easily and simply??

---

### Post by Chris Edgell on 2010-03-18
Oh yeah!

Now I put the hard drive from #2 into #3 and #3 works fine with that hdd.

I put the hdd from 3 into 2 and I get the error 15.  I was told that it never fails, when you see that error, you must reinstall.  So I have started the ALT CD.  I'll see how each step goes. Check CD-ROM; check Memory; Rescue broken system.  Well, I couldn't complete broken system step because I got hung up.

The point of the hangup is when I get this menu to choose from:

Execute a shell in /dev/sda1
Execute a shell in installer environment
Reinstall Grub boot leader
Choose a different root file system
Reboot the system

When I choose Reinstall Grub boot loader...it says installing grub from device or
/dev/hda will install Grub to the master boot record of your 1st hd (IDE)

that goes to RED SCREEN -- FATAL ERROR

And so it goes.....

(I had asked if I could swap out the 80GB hdd for one of the 20GB in the Dell, if it fits..when I was doing this edit, I took it out because I thought I might look ridiculous again so soon--but in the meantime albert s has answered so I don't want his answer hanging out in the wind...)

---

### Post by albert s on 2010-03-18
with my limited knowledge, and as its not too much of a gap(size or age wise) if the connectors are the same then I dont see that it would hurt to try.
thats what I have done.

---

### Post by audiomick on 2010-03-18
> **Chris Edgell said:**
> Oh yeah!

Now I put the hard drive from #2 into #3 and all works fine.

I put the hd from 3 into 2 and I get the error 15.  I was told that it never fails, when you see that error, you must reinstall.  So I have started the ALT CD.  I'll see how each step goes. Check CD-ROM; check Memory; Rescue broken system.
Go Chris, Go!!! :popcorn:

---

### Post by penguinv on 2010-03-18
Hi Chris,

Lets get simple. (My mind cant take the complex so I keep simplifying but somehow they call me smart. Go figure.)

2. You should be able to use any hard drive. But change one windows system to another. But first:

1. **Is the physical computer ok?** 
Put in a hard drive. If you have a dell manual it will tell you if it wants the memory in pairs. Dont short yourself. Put in a bunch of memory. 
**Dell will help you.** Can you install windows? Yes I know you dont want windows but that's the form of the help and you can use this support to make sure that the hardware works. 
I was using a Dell (the owner gave me it, the manual, the disks.) The support man sent me a copy of Windows XP-SP2. That helped.
  Now in my plan here, you've established that the computer works, memory, bios, built-in stuff like the audio etc.

[I]I'm assuming you want Ubuntu and no Windows at all.
[/I]3. Now put in a LiveCD and tell it to reformat the entire hard drive. Now you can see what it does and tell us.

[INDENT]You need to run the hash check on the LiveCD -not just on the downloaded file- to make sure the CD is pure as the driven snow. I've had the copy fail once![/INDENT]

[I][COLOR="DarkOrange"][B][SIZE="3"][SIZE="2"]Poetry is good but objectivity and clarity works. 
   AKA
Kisses don't last but cooking do.[/SIZE][/SIZE][/B][/COLOR][/I]

---

### Post by k3lt01 on 2010-03-18
Penguin, I think it has now been establish that each computer works as it should, if the hdd is swapped around. This basically tells me that the hdd is cactus (irrepariably broken) if it wont install Ubuntu again.

Chris, just an idea that may help. With the hdd  that you had to swap out you could try Gparted on it. There is a Gpartd LiveCD available from [here]("http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.5.2-1/gparted-live-0.5.2-1.iso?use_mirror=transact"). You burn it like a normal Ubuntu CD and use it as a Live CD. It will tell you if your hdd is ok or not.

Btw, may I express my heartiest congratulations on a job well done getting sound on the "no-sound" pc. :popcorn:

---

### Post by ranch hand on 2010-03-18
> **k3lt01 said:**
> Penguin, I think it has now been establish that each computer works as it should, if the hdd is swapped around. This basically tells me that the hdd is cactus (irrepariably broken) if it wont install Ubuntu again.

Chris, just an idea that may help. With the hdd  that you had to swap out you could try Gparted on it. There is a Gpartd LiveCD available from [here]("http://downloads.sourceforge.net/project/gparted/gparted-live-stable/0.5.2-1/gparted-live-0.5.2-1.iso?use_mirror=transact"). You burn it like a normal Ubuntu CD and use it as a Live CD. It will tell you if your hdd is ok or not.

Btw, may I express my heartiest congratulations on a job well done getting sound on the "no-sound" pc. :popcorn:
Gparted is on every Live CD too.  So if you have one you could just use that.  I do not think that any version newer than the one on your 9.10 CD is any better and the one in 10.04 is a little buggy on some hardware.

---

### Post by Chris Edgell on 2010-03-18
I was delighted to receive the well-wishes from you and others, it made me feel so good, after having kinda' a low point last night...just in time I got this nice lift.

I must say, so many of you have not only told me how, but rather, taught me how.  Sometimes we don't know what we're doing and the good teacher comes where the student is at, and then speaks directly, not talks down.  So I thank so many of you for your sensitive approach to an adult who happens to be trying to learn.

And k3, (Michael), it was the perfect time and touch for you to bring the GParted_here_and present me with the lesson plan, so to speak.  It was the marker at the crossroad, "This Way".  I burned that CD and will be very glad to be checking that out soon.  I'll be letting you know.

Thank you.

Oh, I see ranch hand now.  Hi.  I don't know what you mean, "It is on every live CD..."

---

### Post by k3lt01 on 2010-03-18
Ranch Hand is correct Gparted is on all LiveCDs, but the Gpartd CD is updated more often than Ubuntu is released so new features and bug fixes occur often. e.g. Gparted LivCD formatted ext4 before Ubuntu did. Also the Gparted LiveCD is just that, a Gparted LiveCD, there is nothing else to get in the way. I use it on any suspect drive and on new drives as well just to verify the drive is good and any problem isn't caused by a faulty Ubuntu LiveCD.

---

### Post by Chris Edgell on 2010-03-18
Well, I gotta' admit...I thought it was going to be easy...but NO...lol

It was running with the tiniest of print, and then it began asking questions that, basically I began guessing at.  This is like running the "Repair broken system in a way, (isn't it?); asking what keyboard and having to choose from 200 or so...I choose qwerty standard standard then some other code #.

Let me put it on here and at least come back to you and ask what I am supposed to enter...okay?  Well, if you're around...otherwise I'll pose my questions and wait for an answer from wherever.  (I only word it that way so that you don't feel obligated about this step in any way...although I do need help with this from somewhere.)

I thank you.

---

### Post by Chris Edgell on 2010-03-18
Well, I ran the LiveCD GParted on my primary machine with the big plasma screen, in a bright light.The first choice, I just let it run on the default.  Then I came to policy for handling keymaps and I chose "Select Keymap from full list"  I chose querty US American  Standard  Standard

Then I took the option #33 which was like the default for English  And then I got the window telling me about the partitions.

/dev/hda1   17.95Gib
/dev/hda1  ext 3   17.95 Gib   used  5.27GiB  Unused 12.68GiB boot
dev/hda2   ext     17.13 GiB713.83Mib
dev/hda5  linux-swap  17.13 (Was that MiB?)

During all this time across the top were icons for:  Exit; screenshot;  terminal;  GParted;  Info;  Screen Resolution

However whenever The cursor went "on" each it turned into a black gloved hand with a pointing finger...but none of these icons responded in any way...I then did a hard shutdown and here I am describing the trip.

EDIT:  Now I get it.  It worked on here, giving the output that I posted above; then it worked on the AMD showing the partitions and the swap, it was the same structure as the above.  And on the hard drive in question...it just shut off and left me with a black screen...and now, even though it was able to download the XUbuntu, it is not able to to do the update, and it cannot detect the ethernet.  So it is very clear...that that hard drive is shot.  

I had put the 80 Gig hard drive from the AMD into that machine and it seemed to work fine.  So I'm thinking I can get an 80 gig into a Dell and the AMD has room for two hard drives...but I must admit that with the 80 gig hd in the Dell (and remember that hd has the Karmic...I clicked on youtube and didn't get a picture but I got sound...in fact it seemed like I was getting sound from two sources...and no picture..

I just thought I'd tell you that, and even though I'll be thinking about it...I may not try it again because it's a little time consuming putting those braces on the sides of the hd so that it fits snugly and securely in the Dell hd slot...the screws and all else is compatible so I have to wonder why the sound did those strange things.  In fact, I probably will try it again, just so I can look at what hardware is detected, etc....or maybe someone will just tell me that the hd that was in the Dell has a special compatibility with the video card or something ...  The good hd in Del #2 is an IBM Deskstar tm and the one that went bad is a Seagate, but neither of them have any indication that they would be acting differently in a Dell...so I'm still left wondering about why there was no video on the Youtube.

Now as I look at hdds on eBay in the smaller sizes I see SATA and IDE.  Is that the two basic types in these older PCs?

---

### Post by ranch hand on 2010-03-18
If you have an Ubuntu 9.10 Live CD try it.  You know how to run it and learning one thing at a time is easier.

If you have that CD, and boot to the desktop, you will find gparted at System>Administration>Gparted (I think - on some versions it was listed as Partition Editor).

It should do the job.  There are a couple of other tools in every install and on the CD that may do a better job but they are kind of a bugger to learn and have no gui.  Strictly CLI.  I didn't think that you really needed the hassle of learning to do that with no partitioning experience.  I have never had the nerve to use one of them yet (sfdisk).

---

### Post by JKyleOKC on 2010-03-19
> **Chris Edgell said:**
> BUT JIM, as I read your last post, I see where you say that this new COMPAQ now serves as your router.  Can you tell me what that means, how it works??!!  (Or is it something so extremely advanced that you see no point in going into it?)I wouldn't call it extremely advanced, but it was much harder to set up in Xubuntu than was the previous machine that used Mandrake 8.1 (no longer available). The problem is that all of the "helpful" simplification that makes Ubuntu so great as an initial venture into Linux tends to prevent the not-so-usual configuration required of a router! For instance, I had to add a second network card, and then go into the depths of the boot-up code to defeat the automatic renaming of the network interfaces. All in all it took me about two weeks of trial-and-error fiddling to get it working properly -- and that was after having had a similar setup working for more than 8 years on the Mandrake system!

In other words, I wouldn't recommend you try it at this stage of your learning; I found it extremely frustrating to do, although the end result is working quite nicely now and was worth the effort.

The advantage it gives me over an out-of-the-box router is that I can tailor its actions in much finer detail. For example, I run a private FTP server for my database customers to upload their files into, and that had to be kept as secure as possible. However since many of my customers find out about my services via my web site, I have to allow "anonymous uploads" which makes the server a magnet for folk who want a place to store possibly illegal copies for free. The server gets attacked several times every day by people trying to break in. To combat this, I've added a special program that checks the server log every two minutes, and if it finds an attack in progress, immediately adds a router rule to drop all packets coming from the attacker's address. This both stops the attack immediately, and makes it impossible for the attacker to resume it later. This is just one example of the "fine tuning" made possible by having one Linux box serving as my router. I also have an ordinary router (on a different IP address) that serves my laptop via wireless, and it doesn't have anywhere near the capabilities...

EDIT: Saw your question about SATA and IDE after initially posting this reply. Yes, those are the two major types today but older machines probably do NOT have the ability to use SATA drives. SATA requires a totally different controller and the older boxes don't have it. Also, it's very difficult any more to find new drives smaller than 200 GB or so! Buying used drives on eBay is a gamble; they may be worse than the dead one you're replacing, since all the moving parts mean that drives are usually among the first parts of a computer to physically wear out (only fans seem to go bad faster)...

---

### Post by k3lt01 on 2010-03-19
@ Jim. Mandrake is now Madriva.

@ Chris. The Gparted LiveCD is just a base Debian system (Ubuntu is based on Debian and the Gparted LiveCD uses Blackbox or FluxBox instead of Gnome) that only has Gparted on it. That is why I use it, it may take a little work to learn but not much and considering you have come along in great leaps and bounds I feel your up to it.

---

### Post by nikef on 2010-03-19
> **Chris Edgell said:**
> Well, after all this, I just came on to tell you that I got the PCI card, put it in and after going to the System>Sound>Hardware and then output...
Ta-Da I have SOUND.  This is the AMD that has the 80GB hard drive (as opposed to the Dells with 20GB HDs, and no room for adding on the INSIDE, additional HDs) and what looks like room for inserting another. Also remember that this is the ONE machine with Karmic installed (which is why I have that System>Sound>Hardware GUI at all.) 

So now after such a low point, three out of 4 seem to be up and running.

That third Dell, I plan to swap out the hard drive, (well after first removing and reconnecting it...it may be like #2, just a connection problem).



Again, and as always, I thank you all.
Chris

Hey Chris great news 3 out 4 aint bad :p
Glad to read you got the sound working to .

---

### Post by Chris Edgell on 2010-03-19
k3

Is there more to the GParted than what I described above?  When the black hand showed on all those functions across the top, including Exit, if I had waited would that hand have gone away and let me do any of those things, including screenshot...or was the GParted essentially finished at that point?



So when ranch hand says:  "It should do the job. There are a couple of other tools in every install and on the CD that may do a better job but they are kind of a bugger to learn and have no gui. Strictly CLI. I didn't think that you really needed the hassle of learning to do that with no partitioning experience. I have never had the nerve to use one of them yet (sfdisk)."


Was there something to learn there, that I didn't conceive of, ranch hand? and WHAT is sfdisk?  Well I should go and look that up and see how GParted might be called a "sfdisk"

Oh yeah, using my favorite tool for simple direct questions I went to the google search page, typed in What is an sfdisk, and hit "I feel lucky" -- it took me right to this page:  [http://linux.die.net/man/8/sfdisk](http://linux.die.net/man/8/sfdisk) 

and that page went into the "dangerous part" how to change any partitions...Now I get it.  

Thank you, Nike

---

### Post by JKyleOKC on 2010-03-19
> **k3lt01 said:**
> @ Jim. Mandrake is now Madriva.I know; while version 8 was okay and the 2005 version also was fine, the current versions refused to run on my older machines, which is why I switched over to Xubuntu for all of them.

---

### Post by ranch hand on 2010-03-19
fdisk, cfdisk and sfdisk are all partition and repair tools that have been around for a very long time and are very good.

Gparted and some others were developed, partially to have a gui so that partitioning and repair would be a little easier.

You can check out the CLI disk tools on their man pages;
```

man cfdisk

```
I use cfdisk as an example as it is the one I like when I am not using Gparted.

I prefer to use gparted usually (98% of the time).

Make sure that you get HDDs that fit the setup on your boxes.  If all of them are using the wide ribbon do not get any SATA  drives as you will not be able to use them.  They take a completely different connector.  It is an improvement but no use on old boxes.

---

### Post by JKyleOKC on 2010-03-19
> **Chris Edgell said:**
> k3

Is there more to the GParted than what I described above?  When the black hand showed on all those functions across the top, including Exit, if I had waited would that hand have gone away and let me do any of those things, including screenshot...or was the GParted essentially finished at that point?While I've not tried the GParted Live CD myself, the "black hand" pointer is how at least one of the desktop themes available indicates a link that you can click on to go to some other place. When it is on Exit, for instance, a click should cause the program to exit.

The specific theme and pointer set that I use the most has a red arrow pointing to the top left, when it's just a pointer, and this changes to a red arrow pointing straight left when it's on a link (and a thin vertical bar when I'm typing text as I am now). The one on this machine, though, is a small black arrow pointing to upper left most of the time, and does not change for a link. It can be confusing!

---

### Post by Chris Edgell on 2010-03-20
It's odd, so many times I do something the first time and it works...then when I do it again...it doesn't work.  It most likely is a well-known phenomenon: probably called by Confucius: "Getting lucky first time out of box but falling flat on face soon after".

As I said, I put that 80GB hdd from the AMD into the Dell and it worked, even the sound (remember also: it worked WITHOUT the PCI card--well maybe you knew that that other problem requiring the PCI card WOULD have been in the hardware of the AMD if a PCI card made it work).  

So, as I was saying, the song worked, but the video wasn't showing-it just was the little black screen.  I had left it alone for a day or two but then when I tried it one more time,it wouldn't boot up at all...I got only a messages in tiny white print on an all black screen stating (I've got to learn to copy stuff down)...stating that it could not be mounted, maybe saying something about not finding the root.....

I didn't think too much about it, thinking that all would be well when I stuck it back in the AMD.  When I did that...well I got that same message and it seemed that the only thing to do was to reinstall...in other words start over.  I could have come on the forum and asked about it but I do want to work through SOME problems on my own...although in the meantime I learned nothing about my big trouble spot...the space from startup to the point that the OS that is running...the root...the mount point:  all that, plus the swap, would you say, is about partitioning.  

(Although, now that I think again, maybe the root and mount are not particular to partitioning -- they just come up when involved in partitioning.  Which is me asking:  [color=blue]Can I study root and mount APART FROM partitioning per se?[/color]

I even went so far as to doing one thing differently -- when it came time for the partitioning during the new install, when asked me how did I want it, side-by-side or on the whole disk...since it showed me how the two installs would look side by side; since it informed me that at the boot up I would be given the option of which I wanted to boot into; also it told me that anything BUT side-by-side or over the whole disk (if the size of each section plus the swap were to be done manually would be considered advanced)...THAT would be learning how to partition.  

But after getting both installed side-by-side, when I rebooted, it DID NOT give me the option...it gave me a list of things but none was 9.10 Karmic.  THAT must be my next project, learning how to partition manually.

You won't believe it, my friend said she WILL give me another Dell...now THAT one will be the one I should learn to partition on because it comes with Windows 2000; I can save that until such time I am able to get past the password and still get my favorite game (WordSlinger) there.

Anyway, I was redoing the OS after the failure to mount message and I thought I might as well put the Xubuntu Jaunty and see if I could get the sound now that I have the PCI Card...and you know what?  I COULD NOT get sound.  I remembered that was why I had put the Karmic into it anyway because I believe it was k3 Michael who turned me on to the System > Preferences > Sound  and am able to do the hardware sound check there....and that is NEW to Karmic.

SO...I reinstalled the Karmic, did the update, installed the extras...(didnt even have to do that sound gui that card IS set up I guess)... and TA DA...I have sound again.  So it was a long trip getting back to where I was.

Bye for now
Chris

---

### Post by ranch hand on 2010-03-20
You may well have rescued that install of 9.10 if you had reinstalled grub;

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

If you are going to learn manual partitioning I would start the next time you reinstall something.  Install on 2 partitions.  One for / (root) and one for /home.  Then if you need to reinstall you do to a problem such as you had with 9.10 you just point the installer at the root partition and tell it to use that for / and to format.  You point the installer at the /home partition and tell it to use that for home but do not have it format /home.

While it is a good thing to back up all your data anytime you install, that has never failed to give me a fresh / and leave my /home untouched with data intact.

I would encourage you to hold off on doing anything to your "new" Dell until the end of next month when 10.04 is released.  While we are, of coarse, having some problems with beta1 that just came out it is more stable than 9.10 was when released.  The version of grub is much improved.

Of coarse you could get the package for the newer grub and install it on 9.10 too (I have it) but 10.04 is just a better OS already than 9.10.

---

### Post by Chris Edgell on 2010-03-20
Hi,

This grub link is JUST what I need.  I took a glance and will go and give it a good read.

Now that second paragraph is just like Greek to me...I'm hoping I can grasp the concepts as I read that article. 

Thanks...nice to see you.

---

### Post by ranch hand on 2010-03-20
If you read the link in my sig, just the first post, you will have a basic grasp of grub.

The second link that I give in that post is the best in depth study of grub you will find.  The author, drs305, is guilty of writing a lot of the wiki information on grub.

When the new grub was introduced at 9.10-testing-alpha2, there was no real documentation except the first link that I give in that post and, of coarse, we didn't know about it,  It was a rough ride and we made up the documentation as we went along.

drs305, kansasnoob, miefera, herman, myself and a few others that I can't remember right off the top of my head are all pretty good at breaking and fixing the new grub.  I really love grub-legacy but this new one is a lot more flexible and will deal better with the new types of drives and file systems that seem to come out every other week.

It is far from perfect yet but it is already a lot easier to really do things with and to than grub legacy.

Grub-legacy, by the way is grub0.97 and the grub you are using in 9.10 is grub1.97beta4.  What I am using is grub1.98.  If you have 9.04 installed you can get grub1.96 (early version of he new grub in the 9.04 repo.

---

### Post by Chris Edgell on 2010-03-20
I thank you greatly...even though my brain reels...I am like a Checkers player reading descriptions of great chess games even though he has only seen a chart of how the pieces move.  In other words, "What the heck are they doing"

I've got to slow this sucker down some..to put it in your kind of vernacular... and just compare THIS stuff to reading the lines in MY OWN boot script, at least.  (Maybe I'll begin to see some light...or maybe I should just accept that it's the thing that gets me from here to there --maybe to try to understand it is to try to learn what a programmer writes...when I don't HAVE TO learn that.

I think I should at least be able to understand your post, linked to your signature, don't you?  Maybe when I get the picture, I'll say, "Oh, I get it, that wasn't so hard."

---

### Post by ranch hand on 2010-03-20
I first wrote that for the 9.10 testing forum because new people would join in and not have a clue.  It was  a sticky there for a while.

You have to remember that I am a noob too.  You should also remember that folks with no real experience with grub-legacy have an easier time with grub as they do not have to unlearn a bunch of things.

That was written with a very clear memory of all the stupid questions  that I asked about grub-legacy when I first joined the forums here and how hard it was to get my head around it all.

I would like to know how it goes with you.  I have hopes that it will give you a very simple but working knowledge of grub.

If you have any problems just holler.

It really is kind of fun to play with and you will see a type of entry that never needs updated.  It is all I ever use.  If you have that on the OS that you are using for the grub menu and you have that second debian based OS (like Ubuntu is) on the drive, you can wipe that OS and replace it with a completely different OS (debian based) and use the same menu entry that you were before.  I like it.

---

### Post by Chris Edgell on 2010-03-21
Has everyone heard of this but me??

Go to Synaptic and download "hardinfo"; then hit Alt + F2, type in "hardinfo" then press enter.  You will see a window that covers ALL about your computer.  Try it!  I am amazed at the dozens of times I was struggling to find out stuff about all that's in my computer...and it's like any link...it's all there and it's so easy if you know where to look.

---

### Post by ranch hand on 2010-03-21
Yup, you are the only one that didn't know that.  Well, you and probably about half the other users out there.

There are a lot of handy things built into Linux.  This is the reason for a good CLI system.  You just can't do all this with guis because they just take up to much room and processor power.

---

### Post by Chris Edgell on 2010-03-22
Well, I'm glad I found out about it...so much information.

I have to ask:  I acquired a wireless mouse (Kensington PocketMouse Pro Wireless).  When I google it, it talks about a driver.  Do [color=red]I[/color] need a driver for it with Linux?  The site doesn't mention Linux and, well, I just wonder if I can use it.  It has the USB piece, new batteries, and red power-light ON.

---

### Post by ranch hand on 2010-03-22
I have never used one but if you have something to plug into a USB port it will probably just work.

If you go to synaptic and run a search for nvidia (I do on all the OS' I use to delete the stuff) you will see several entries.  Those are drivers for those video cards.  A whole lot of drivers are included with the kernel.  This is why most stuff works.

The drivers mentioned are, I am sure, for MS.  If you think you are having a hard time installing Ubuntu you should try installing that pig.  The disk takes a long time and then you need to hunt up and install a BUNCH of drivers and programs.  It can be a real nightmare on some hardware and is pretty much a long days work if there is no problem.

Just plug it in and try it.

---

### Post by Chris Edgell on 2010-03-22
Hi,

I did install the nvidia, but I'm sorry to say, it still doesn't work.  Is there some other step I could take to make sure there is the driver.   Well, any other options...if not, no harm done as it was free to me.  (But, of course, it would be nice as the ones that came with the Dells have no scroll wheel.)

See you later.

---

### Post by audiomick on 2010-03-22
> **Chris Edgell said:**
> Well, I'm glad I found out about it...so much information.

I have to ask:  I acquired a wireless mouse (Kensington PocketMouse Pro Wireless).  When I google it, it talks about a driver.  Do [COLOR=red]I[/COLOR] need a driver for it with Linux?  The site doesn't mention Linux and, well, I just wonder if I can use it.  It has the USB piece, new batteries, and red power-light ON.
Hi Chris.
just plug it in and see if it works. I had success / luck with a usb/ wireless keyboard and mouse from Logitech. I think there is a certain amount of standardisation there. If it doesn't work, it won't break anything, and you will know you need to do some more digging. If it does, problem solved. Just remember to put fresh batteries in it...;)

---

### Post by ranch hand on 2010-03-22
I brought up nividia as an example of available drivers.  It is for video cards made by that company.  It should have no effect on your mouse.  Most of the nvidia stuff should be installed anyway.

It does nothing on your AMD box as that uses its own brand of video (ATI).

Seeing that I unintentionally misled you I thought I better look into that mouse.  Haven't found anything helpful yet.

How about plugging it in and then posting the terminal output from;
```

lsusb

```
That should pick up anything hooked through your usb ports

---

### Post by Chris Edgell on 2010-03-22
Hi, Michael,

Nope, it doesn't work.  (And the batteries are new)....so....

I may do some more digging and see what I can come up with.

See ya'
Chris

---

### Post by Chris Edgell on 2010-03-22
Here are the screenshots; 1) hardinfo, 2) the command you gave, lsusb.

I remember last time I thought my car battery was okay because the lights came on...but I needed a new battery anyway.  THESE batteries are not brand new..could they be old enough they light the light IN the mouse but not fresh enough to do the rest of the work?

Oh, I have installed the nvidia in both the AMD and the Dell #2.  I mean to say, I had done that before you said what you said, ranch hand, even though I really didn't understand about the card not affecting the mouse...(shall I uninstall just because I don't need it?)

---

### Post by ranch hand on 2010-03-22
Well, hmm, you are detecting it.  That is good.  Why doesn't it work is the question.

Batteries may be a good idea just to know if that is the problem.

I can't find a thing on it except some bug that should not have to do with your hardware.  I did find a page on setting this mouse up in gentoo so it must be possible.  The font was unreadable on the page so I couldn't really learn anything there.

There are a lot of drivers out there but they are all for MS that I can find.

Lets get some batteries we know are good in there and see if it works that way.  Then we will panic or something.

---

### Post by Chris Edgell on 2010-03-22
I wish I had the batteries that had a battery tester included...so it may be tomorrow.  But they had never been used...they should be good.

You guys are so nice to me.  Thanks again, as always.

---

### Post by k3lt01 on 2010-03-22
I have a Microsoft Wireless mouse and keyboard on my desktop and it works ootb. Have you rebooted since you plugged it in?

---

### Post by Chris Edgell on 2010-03-22
Nice to see you.

Yes, I did reboot.

Could just be defective.

---

### Post by k3lt01 on 2010-03-22
Yeah sorry for not being around around much., I have been working on plymouth and ureadahead problems the last few days. I love getting into the nitty gritty stuff but it is so time consuming.

I know my mouse setup somtimes mucks up and if I change the battery and reboot it works again.

---

### Post by Chris Edgell on 2010-03-23
...I've embarrassed myself so many times but I press on...

I need to know if the wireless mouse is only for special technology in a LAPTOP?

I've found a few articles that talk about laptops and bluetooth technologies and wonder if this wireless mouse is really for use with regular desktop computers.

---

### Post by warfacegod on 2010-03-23
> **Chris Edgell said:**
> ...I've embarrassed myself so many times but I press on...

I need to know if the wireless mouse is only for special technology in a LAPTOP?

I've found a few articles that talk about laptops and bluetooth technologies and wonder if this wireless mouse is really for use with regular desktop computers.

There are Bluetooth mice around but they shouldn't be just for laptops. There are desktops that have Bluetooth capability. I have a "laptop" mouse. The only thing that makes it that is it's size, its a little baby one! but it still works on desktops.

Wireless mice tend to not like having unfresh batteries. Some are worse than others. Both of my mice will stop working well at about 50% which is more than enough to run a flashlight or even a walkman!

---

### Post by JKyleOKC on 2010-03-23
> **Chris Edgell said:**
> I need to know if the wireless mouse is only for special technology in a LAPTOP?The generic answer is "no" but any specific mouse might be...

When I installed the machine that's handling my Email, I was in a hurry to test it out so I grabbed the wireless mouse from my laptop and plugged its USB receiver into the new machine. It "just worked" with no fiddling at all. A few minutes later I fell and broke my leg, resulting in a couple of weeks in hospital and another couple of months of rehab treatment, so the mouse stayed on the new machine. That was well over a year ago, and it's still there. I bought another for the laptop once I was mobile again, and in the meantime used its touch pad.

As I recall Kensington's line was primarily for Macs, so it's possible that your critter may be Mac-oriented -- but if it has a wheel and (at least) two buttons it ought to work with no need for special drivers. From Hardy on, Xubuntu has automatically detected most mice and configured itself accordingly...

---

### Post by cascade9 on 2010-03-23
> **ranch hand said:**
> I brought up nividia as an example of available drivers. It is for video cards made by that company. It should have no effect on your mouse. Most of the nvidia stuff should be installed anyway.

It does nothing on your AMD box as that uses its own brand of video (ATI).

Actually, unless I missed something, somewhere, the AMD box has a nVidia Geforce 2-

> chris@chris:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 14)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:0b.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
00:0c.0 Communication controller: 3Com Corp, Modem Division WinModem
00:0e.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8231 [PCI-to-ISA Bridge] (rev 10)
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1e)
00:11.4 Non-VGA unclassified device: VIA Technologies, Inc. VT8235 ACPI (rev 10)
01:05.0 VGA compatible controller: nVidia Corporation NV15 [GeForce2 GTS/Pro] (rev a4)
chris@chris:~$ [http://ubuntuforums.org/showthread.php?p=8948217&highlight=AMD#post8948217](http://ubuntuforums.org/showthread.php?p=8948217&highlight=AMD#post8948217)

But yes, agreed, in almost every case your video should have no effect on your mouse, wireless or not (normally, the only time it could would be if your PS2/USB controller IRQ conficted with the video IRQ) 

The Kensington PocketMouse Pro Wireless should be suppoted by the usbhid module. 

> **warfacegod said:**
> There are Bluetooth mice around but they shouldn't be just for laptops. There are desktops that have Bluetooth capability. I have a "laptop" mouse. The only thing that makes it that is it's size, its a little baby one! but it still works on desktops.

Wireless mice tend to not like having unfresh batteries. Some are worse than others. Both of my mice will stop working well at about 50% which is more than enough to run a flashlight or even a walkman!

Which is just another reason why I never use wireless mice or keyboards. Batteries, more hassle than cords are IMO.

---

### Post by Chris Edgell on 2010-03-23
I have loved the wide view of this most recent question (problem).

I liked seeing you, warfacegod!  But I thank you all.

And now you, Cascade, have put the nail in the coffin of that little mouse... the fresh batteries didn't work and because I bought them without benefit of a sale, I've already spent nearly $5...and you know what, I'm lucky they didn't work for just the reason Cascade offered...find a freebie.  

I got one that I had, with a scroll wheel, found a longer screw...and IT works, and even though the mouse squeeks when the ball rolls, hey, I can live with a mouse squeek as long as it isn't a real mouse...so there you have it.  Thanks all.

---

### Post by audiomick on 2010-03-23
Hi Chris.
If you are still interested in the wireless mouse, something just occurred to me.
On my wireless keyboard / mouse setup, I have to "restart" them when I have changed the batteries. It is quite simple. There is a button on the receiver bit, on the mouse, and on the keyboard. They all have to be pressed one after the other in a particular sequence so that the bits can all find each other. Have a look at yours. Maybe you need to do something similar.

There is likely to be a simple "set of pictures" instructions on there somewhere. If there is a "reset" button on the mouse, it is likely to be quite small, and recessed so you can only press it with a straightened out paper clip or a pin or something.

---

### Post by Chris Edgell on 2010-03-23
I have tried and tried, and looked and looked.

I did restart, reload, and tried to find the code.  I pushed something on the USB stick (whatchamacallit), I pushed the small button on the mouse (the only possible thing to push --  not that small but somewhat recessed) and didn't for the life of me know what to push on the keyboard.  I went to the Kensington web site and they aren't talking about old model numbers, at least not where I can find.  Do you have any point of guidance after I've tried what I have tried?

---

### Post by audiomick on 2010-03-23
Not really, I am afraid. I would have to see the device and fiddle with it.
Are you able to ask the previous owner if there is some "reset" procedure?

---

### Post by warfacegod on 2010-03-23
You could always go get your local 15 year old. Teenagers today aren't worth much for raking lawns but at least they can fix electronic doohickys.

---

### Post by ranch hand on 2010-03-23
> **warfacegod said:**
> You could always go get your local 15 year old. Teenagers today aren't worth much for raking lawns but at least they can fix electronic doohickys.
The ones I know are scared to death of Linux.  Chicken little buggers.

---

### Post by Chris Edgell on 2010-03-23
Well, I do have a friend with a 13 year old boy who wants to come over here and see about all these computers, I'll save that for him to fiddle around with.

Me, I must say I have spent a lot more time with all this hardware than with anything about software.  Yesterday I had the dubious opportunity of going through a box of electrical junk.  (That's where I got that mouse).  I do have all this half broken stuff; I'm trying to get at least three machines up and running, but it's been like playing Twister on a bubble wrap mat.  Push one down, another pops up and so on...  That's how MY computer world is right now.  My one working set of speakers MAY not be working...I've fooled around with that a lot.  I have another set that I got for a couple of bucks in that box of junk, I got about 3 AC Adaptors to try with them, but found out that it's much more specific than that.  It reminds me of my friend who was so excited to find a great pair of black wing-tip shoes for her husband...then she discovered she'd come home with two-left-feet shoes.  

I came home with one adapter: 120 AC 15 W, 9 volt, class 2 transformer -- but it's for a breast pump; are these things interchangeable?  I have read TOO much about adapters today...I know what I have to do, I have to go tomorrow and get a cheap set of speakers that really work and then I can know what works and what doesn't.  As it is, I'm just ricocheting all over the place trying to get a sound. (Besides me cryin'...) no I'm just kidding...I'm having a ball. LOL

It must be the speakers; they were sounding like a short was happening, intermittent sound at times.  So my primary Dell, only the internal speaker is working.  You know I never got sound from the AMD until I got it "externally" with that PCI card; and that Dell #2 was sometimes singing and sometimes not...and remember last time I spoke of it, it was getting sound and no picture.  I've studied a lot today.

So you see, I've got a lot of stuff to work on and it's just as well because MY CAR WOULDN'T START TODAY.....that's okay... maybe THAT'S just the battery and I had no place I had to be this week so it couldn't have happened at a better time.

So there you have my life in a nutshell...but I'm smiling... NO...NOT like I've lost my marble..... (I should make that plural)  lol

Laugh and the world laughs with you... it's been a heck of a day.

But nice to hear from you all.

Chris

---

### Post by Rasa1111 on 2010-03-24
:lol:

 your thread has been a joy to read, Chris. ...
 you do make adventures that would drive many crazy... seem fun. lol
good stuff,  and good luck. itll all pay off soon enough, i know it. 
 thanks. :) <3

---

### Post by Chris Edgell on 2010-03-24
I thank God you landed here, I see your avatar.. you brought me back to a world that doesn't include MY problems.  (Reminds me of a line  by Renee Z. in "Chicago")

I just commented about doing all this stuff with hardware and I explored YOUR posts, Rasa, and I found "The 10 best things to install"  (Start on page 34)...and that's JUST WHAT I needed ...  to think about software; to get a fuller view of what's available, and I sure will be exploring your choices.  (And I want to bring them up and find out about them...the virus thing, the firewall thing, those grabbed my attention...)  And I realized that I haven't been exploring any threads but my own....I used to see more around me.  It seems that lately I just occasionally read a few posts in the absolute beginners forum. 

So thanks again, Rasa

---

### Post by audiomick on 2010-03-24
Hi Chris.


> **Chris Edgell said:**
> Well, I do have a friend with a 13 year old boy who wants to come over here and see about all these computers, I'll save that for him to fiddle around with.Good idea...;)

> 
I came home with one adapter: 120 AC 15 W, 9 volt, class 2 transformer -- but it's for a breast pump; are these things interchangeable? They are, with three reservations: The plug has to fit, or be changed. You should pay attention to which contact the positive is, and which the negative.

The power supply has to deliver the right number of volts for the device: To many will fry the device, too few and it won't work

The power supply has to be able to deliver enough Amperes (Amps) i.e. current, usually written as something like 3.5A, ( 3 and a half Amps) 15mA (15 milliamps). If the power supply can deliver equal to or more amps than the device needs, it will work. If the power supply is rated at less Amps than the device draws, you will most likely fry the power supply.


> It must be the speakers; they were sounding like a short was happening, intermittent sound at times.Number one candidate by a long way is the plug on the end of the cable where it plugs into the computer or into the speakers. This is likely to be a &#8539;" moulded jack plug, i.e. one that you can't take apart. A sad fact of life is that moulded plugs always break eventually, and it is not possible to repair them. Your choices are to cut the plug off and solder a new one on, or replace the cable.

To test this, hold the plug so that it can't move in the socket and wiggle the cable. If you can't make it crackle that way, wiggle the plug in the socket whilst trying to prevent the cable from moving in relation to the plug.

The theory behind this is that there is very likely an intermittent contact in there somewhere. What you are trying to do is provoke movement at only one point. If you just grab the cable and shake it around, you will probably be able to cause it to crackle, but wont know exactly where the problem is. You need to systematically go along the chain of connections and provoke movement at only one point to isolate where the problem is.

The problem could be:
In the output socket: If the speakers crackle no matter what they are plugged in to, this is not likely to be the problem. Unless all your machines have a broken output socket...;) 
If the problem is restricted to one machine, this could well be the cause, and should show up if you wiggle the plug in the socket.

That the front part of the plug, i.e. the silver bits that plug in, have become unstable. This will show up when you wiggle the plug whilst keeping the cable still in relation to the plug. This happens, but is less common.

That the connection between the cable itself and the contact inside the plug is faulty. This is the cause of something comfortably over 90% of all cable problems. This will show up if you hold the plug steady in the socket and wiggle the cable around in the back of the plug.

If the problem can be isolated to the cable, as I expect, there are two possibilities. If the cable is not permanently connected to the speakers, i.e. has a plug on each end, your best bet is probably just to buy another one at you nearest discount electronics store (take the old one with you to compare with, so you know you get the right one).

If the cable is permanently connected to the speakers, you would have to replace the plug on the end, if that is where the problem is, or repair the connection inside the speaker, if you should be able to determine that the problem is there.

Note: whilst I consider the audio connection cable to be the most likely culprit, it is also possible that the power supply is at fault. The fault finding procedure is identical: wiggle the various connections and see where it crackles. The most likely place is where the cable goes into the power supply. Because people tend to pick the things up by the cable, they usually break there. This can often be fixed if it is possible to take the power supply apart, but is nearly always a fiddly job.


Good luck with your car. I hope it is just the battery.

---

### Post by warfacegod on 2010-03-24
...or the speakers could just be blown?:p

---

### Post by Rasa1111 on 2010-03-24
> **Chris Edgell said:**
> I thank God you landed here, I see your avatar.. you brought me back to a world that doesn't include MY problems.  (Reminds me of a line  by Renee Z. in "Chicago")

I just commented about doing all this stuff with hardware and I explored YOUR posts, Rasa, and I found "The 10 best things to install"  (Start on page 34)...and that's JUST WHAT I needed ...  to think about software; to get a fuller view of what's available, and I sure will be exploring your choices.  (And I want to bring them up and find out about them...the virus thing, the firewall thing, those grabbed my attention...)  And I realized that I haven't been exploring any threads but my own....I used to see more around me.  It seems that lately I just occasionally read a few posts in the absolute beginners forum. 

So thanks again, Rasa


hehe :lol: Hiyah Chris, thanks....
 Earth looked nice from geosynchronous orbit, 
figured id stop down and see what was happenin. lol

Im happy my aimless wandering around the forums has brought a flash of 'insight' to someone other than I..... maybe. lol :)


in regards to the firewall, and virus scanner doohickeys... 
i think they are both essential for 'newbs' (even if only for peace of mind) lol

 ClamTK is a simple virus scanner, with a nice graphical interface, (easy for newbs)
and its really simple to use. (even easier than the many antivirus programs i had in window$)  It can also scan files from the net before downloading/installing them onto your system. 

 the Simple Firewall thing,  is just the Graphical interface, 
( the firewall is already in ubuntu, just not 'on' as default)
 This just makes it easier to turn on and off, and to allow/deny ports without having to use the terminal and type lines of cryptic text.  lol

 Once I downloaded the simple firewall interface, i just opened it from the System>Admin menu,  put a check mark iin the box, and the firewall turns on to "enabled".  Then it can be forgotten about, unless one needs to allow/deny specific ports, but even that is easy with this firewall GUI. 

 Thanks for the nice message.
 best of luck.  :KS  :) <3
  Rasa

---

### Post by warfacegod on 2010-03-24
This might be worth reading: [http://ubuntuforums.org/showthread.php?t=510812]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by Chris Edgell on 2010-03-24
Audiomick, that long post was just what I wanted.  It was great, you covered all the points; you answered all my questions.  It helped me a lot.  After all I went and bought a set of speakers for $20 and they worked... I don't know if it was the connector or if I blew the speakers as warfacegod suggested.  I liked the thread about the "Ubuntu Security" and as Bodhi said, "Don't try to read this all at once."  I'm trying to understand it.

Today I burned the Alt-CD for Lucid and tried to put it into the AMD.
First I tried "Install"  It seemed like I was minutes away from the end when I got the message.  "Select and Install Software: An installation step has failed.  You can choose to run the failing item again from the menu or skip it and install something else."  (Same thing happened the second time).

Then I tried check CD_Rom and got the message:  ./pool/universe/m/murrine-themes_0.90.3.3ubuntu2_all.d
eb file failed the MD5 checksum verification.  Your CD-ROM or this file may have been corrupted.

Right away I reinstalled the Karmic and it all went fine, including sound and all.  I have to look back and see if there is another check for the CD-ROM...seems like. I suppose I should cool my heels and wait on the Lucid, but I am chomping on the bit to see it.

I can't tell you all the parts and pieces of my day today, but I will say,  after all is said and done...I feel like I wrestled with an animal...and I won... just barely.  The car's okay.  Everything turned out okay but it sure drained me.  That just means I'll sleep well..... Thanks all!

---

### Post by ranch hand on 2010-03-24
I am not sure that you want to install 10.04 at this point of development.  We only had 35Mb of updates today.  I would say that is below average.  Yesterday was over 90Mb of updates.

Some of the updates probably will break the OS on some hardware.  That is a big part of the reason for testing.  Have it break now so that it doesn't break at release time.

But, unless you dual boot so you can chroot and update from another OS or want to chroot from a LiveCD (a pain because of the slow boot of the CD), the only option you would have is to download the next days "daily build" and install it hopping whatever broke has been fixed.

About this time in 9.10-testing I had one install that wouldn't boot for about 10 days (that is when I learned to chroot into the bugger).

Testing is a lot of FUN.  It is also a great place to learn a lot in a hurry.  I would recommend to you that you do it sometime when you have a box that is set up and working with a stable OS so that you can dual boot.  It would also be a good idea to have another drive or computer that you can depend on in case things really go south on the test drive.

The folks on the testing forum are generally really great folks and can work around a lot of stuff.  They are a fun bunch generally speaking.  A couple of the mods are real cool too.

You have a bunch on your plate right now with what you have going and testing really does take time.

You may want to lurk over on that forum a bit to see what FUN you are missing.

[http://ubuntuforums.org/forumdisplay.php?f=377](http://ubuntuforums.org/forumdisplay.php?f=377)

The sticky on testing is a good thing to read (the first post) as is the warning about Update Manager.

I think you would enjoy it, I just wonder if this is the time.  A new test cycle will start in May for Mangy Moose (or what ever they are calling 10.10).

As an aside, a bunch of us on the 9.10-testing forum decided that Lounge Lizard was what 10.04 should have been called.  Now that I have Lounge Lizard I am looking forward to Naughty Newt (11.04).

---

### Post by k3lt01 on 2010-03-24
I agree with the crux of what ranch hand said.

I've been using Ubuntu since 7.04 and have only just felt comfortable enough to get into the testing side of things. It is an extremely steep learning curve. I'm not trying to discourage you from trying it but I am trying to suggest that you follow RH's advice by reading the Lucid forum he linked to to see the types of things that can go on. Then when you feel comfortable in yourself jump in but have a spare machine or drive to use that is stable.

---

### Post by ranch hand on 2010-03-25
And watch out for k3lt01.  He is another one of "them" from the testing bunch.  Some come and go.  The truly strange ones stay.

But we do have FUN.

---

### Post by k3lt01 on 2010-03-25
> **ranch hand said:**
> And watch out for k3lt01.  He is another one of "them" from the testing bunch.  Some come and go.  The truly strange ones stay.

But we do have FUN.I'm the smart mouth who tends to !@#$ people right OFF!

---

### Post by cascade9 on 2010-03-25
On the speakers...audiomick has given you an exhaustive list (thanks!). It took me a while to figure some of that out. It could be, like warfacegod said, that they are blown, but in my experience, even blown speakers make some sort of noise (normally a muffled 'omph' or a high pitched whine). Its probably the connector or the wire (I've had the leads to the speakers break in all sorts of places, not just at he speaker or conenctor end. Makes it a rigth pain to find the flippin break :|  ) 

+1 to ranch hand...testing can be fun, but if you've got any other issues, its not. You never know if its the hardware causing the problem, some new update breaking things, or (sorry to put it this way) user error. BTW, I vote that 11.04 should be 'nubile numbat' :D 

> **Chris Edgell said:**
> Me, I must say I have spent a lot more time with all this hardware than with anything about software.  Yesterday I had the dubious opportunity of going through a box of electrical junk.  (That's where I got that mouse).  I do have all this half broken stuff; I'm trying to get at least three machines up and running, but it's been like playing Twister on a bubble wrap mat.  Push one down, another pops up and so on...  That's how MY computer world is right now.  My one working set of speakers MAY not be working...I've fooled around with that a lot.   

If it makes you feel any better....I've been playing with hardware for well over a decade and a half (and using computers a lot longer than that) and I find that the 'box stuff' can be a horribly fustrating expereince. On a good day, your 'twister' analogy is exactly right.....on a bad day its like everything is dead. On the bad days, I just avoid playing with the stuff at all, its just to annoying. 

I wouldnt be surpised if your USB wireless mouse was in there for a reason. If that reason is 'its dead, jim!' or if its just troublesome is questionable. 

IMO, once you get something thats ever been in the 'troublesome' pile working, just dont touch it. Its amazing how often I've tried to do something simple, like installing a video card on a computer thats using on-board graphics and had all manner of stupid things pop up. 

Rigth, well, now its time to go back downstairs and fiure out what is working on my current 'box of stuff'. Hopefully I can get one of the P4/Athlon motherboards working, I've got enough RAM, HDDs network cards, sound cards and video cards to fill a small truck LOL. Someone I know has just had machine death, so I've trying to get something going for her.

---

### Post by warfacegod on 2010-03-25
Hopefully I can get one of the P4/Athlon motherboards working, I've got enough RAM, HDDs network cards, sound cards and video cards to fill a small truck LOL.

Surely salvaged from the side of the road?:p

---

### Post by Chris Edgell on 2010-03-25
> **audiomick said:**
> 

They are (Ed. note.  i.e. adaptors are interchangeable) with three reservations: The plug has to fit, or be changed. You should pay attention to which contact the positive is, and which the negative.

audiomick, can you elaborate on this point, I have NO idea what you mean, are you talking about the 1/8" moulded jack plug that plugs into the computer?  Should I "pay attention" to the rings around it as to whether THEY are positive or negative? (and how to tell...and why?)

> **audiomick said:**
> The power supply has to deliver the right number of volts for the device: To many will fry the device, too few and it won't work.

Does it have to be exact: my new speakers take 9 volts; my old take 7.5; is that close enough or MUST be EXACT?


> **audiomick said:**
> The power supply has to be able to deliver enough Amperes (Amps) i.e. current, usually written as something like 3.5A, ( 3 and a half Amps) 15mA (15 milliamps). If the power supply can deliver equal to or more amps than the device needs, it will work. If the power supply is rated at less Amps than the device draws, you will most likely fry the power supply.

So the breastpump adaptor puts out 9 V and 1.0 Amps and one other set of speakers need 15 V and 1.1 Amps, if the voltage matched could the amps vary by .1 ?  Or are we basically talking about exact matches?  I see loads of nice looking speakers at thrift stores and want to know the parameters for replacing the adaptors.

Also you've said "solder" new plug jacks on, CAN'T they be matched and twisted and well-wrapped with electrical tape.  (See how I am? I was once called the "Makeshift Queen"...so don't say anything to Cascade, warface, about where the stuff may have been salvaged from.) LOL  

I admit I don't stay on topic but I rarely just throw remarks in, in the bantering back and forth style.  I really DON'T want to get this thread moved to the Cafe for too much of that. 

I must say I appreciate your participation, Cascade.

Again, thanks all.

---

### Post by cascade9 on 2010-03-25
> **warfacegod said:**
> Hopefully I can get one of the P4/Athlon motherboards working, I've got enough RAM, HDDs network cards, sound cards and video cards to fill a small truck LOL.

Surely salvaged from the side of the road?:p

Aww, you remembered! 

Most of the side of the road stuff was actually fine, I tended to just install some distro and then give them away.  Not in the this case, though. The 'side of the road' stuff I've run out of, this is actually stuff I got given...in a 'box of stuff' LMAO. 

Its being a right pain as well. I've got 2 dead P4 boards (got taken to the e-waste place late this afternoon), one workign P4 (well, celron currently but not for long...) a P4 thats being very annoying (boots sometimes, not others) and an athlon that I'm hoping has a dead CPU (I cant find my testing athlon 2200+). Thats the way of he box of stuff though.

> **Chris Edgell said:**
> Does it have to be exact: my new speakers take 9 volts; my old take 7.5; is that close enough or MUST be EXACT?

Not close enough IMO, but audiomick would have a better idea than I would I think. 

> **Chris Edgell said:**
> So the breastpump adaptor puts out 9 V and 1.0 Amps and one other set of speakers need 15 V and 1.1 Amps, if the voltage matched could the amps vary by .1 ?  Or are we basically talking about exact matches?  I see loads of nice looking speakers at thrift stores and want to know the parameters for replacing the adaptors.

If the voltage matches, the plug fits and the positive/negative are the same, but your only out but 10-15% on the amps you should be fine. With speakers, you might get sound issues if your turned it up to full, but thats about it.

> **Chris Edgell said:**
> 
Also you've said "solder" new plug jacks on, CAN'T they be matched and twisted and well-wrapped with electrical tape.  (See how I am? I was once called the "Makeshift Queen"...so don't say anything to Cascade, warface, about where the stuff may have been salvaged from.) LOL  

I admit I don't stay on topic but I rarely just throw remarks in, in the bantering back and forth style.  I really DON'T want to get this thread moved to the Cafe for too much of that. 

I must say I appreciate your participation, Cascade.

"Makeshift Queen"- thats a badge of hunour as far as I'm concerned :KS Yep, the electrical tape trick should work- I've done it when I didnt have a soldering iron handy. 

As you can see from warefacegods post, and my reply, I've run stuff I've found by the side of the road..and out of bins, truth be told. Recycling! 

I doubt that this would get moved to the cafe, it shouldnt anyway. Its still on subject- 'chris's adventures/learning curve in the world computers'. ;) 

LOL, no problem, hopefully I dont drag the tone down TOO much :D

---

### Post by Chris Edgell on 2010-03-25
Cascade, thank you for getting me on track with this.  I should have known from the tone that you and warface knew each other.  I'm so cautious about insult, and I didn't want you to be insulted for the side of the road stuff...(I loved that senator who said her mother has served people fresh road kill...hates to see it go to waste if its good...lol).  Cheers warfacegod, sorry, I should have known.

I liked your responses about the audio stuff, Cascade.  I still am wondering about "the positive and negative being the same"...what's that about?

---

### Post by ubunterooster on 2010-03-25
> **Chris Edgell said:**
> 
Does it have to be exact: my new speakers take 9 volts; my old take 7.5; is that close enough or MUST be EXACT?  I say no
>  So the adaptor puts out 9 V and 1.0 Amps and one other set of speakers need 15 V and 1.1 Amps, if the voltage matched could the amps vary by .1 ?  Or are we basically talking about exact matches?  That is under in both amperes and voltage, but if Voltage equalled I would do it, but be aware that life expactancy of the adapter would be shortened.
>  Also you've said "solder" new plug jacks on, CAN'T they be matched and twisted and well-wrapped with electrical tape.  (See how I am?)  I've done both methods but twisted wires can lead to noticeable distortion, esp over time as they untwist

>  I admit I don't stay on topic but I rarely just throw remarks in, in the bantering back and forth style.  I really DON'T want to get this thread moved to the Cafe for too much of that. 
[offtopic] I mark all offtopic posts like this [/offtopic]

---

### Post by Chris Edgell on 2010-03-25
Hi, ubunterooster, I think, way back when, you were the first responder on this thread.

Thank you for your knowledge on that subject of electrical stuff.  I'm makeing a note card of the parameters...so I'll be ready, this hit and miss is for the birds.  (Brings new meaning to "hit and miss" knowing these pidgeons around here. LOL

(On that first response do you mean "I say no" that it IS NOT close enough?)

---

### Post by ubunterooster on 2010-03-25
> **Chris Edgell said:**
> Cascade, thank you for getting me on track with this.  I should have known from the tone that you and warface knew each other.  I'm so cautious about insult, and I didn't want you to be insulted for the side of the road stuff...(I loved that senator who said her mother has served people fresh road kill...hates to see it go to waste if its good...lol).  Cheers warfacegod, sorry, I should have known.

I liked your responses about the audio stuff, Cascade.  I still am wondering about "the positive and negative being the same"...what's that about?
In most modern speakers if you reverse the two wires it simply won't work and you can just swap them.

---

### Post by ubunterooster on 2010-03-25
> **Chris Edgell said:**
> Hi, ubunterooster, I think, way back when, you were the first responder on this thread.

Thank you for your knowledge on that subject of electrical stuff.  I'm makeing a note card of the parameters...so I'll be ready, this hit and miss is for the birds.  (Brings new meaning to "hit and miss" knowing these pidgeons around here. LOL

(On that first response do you mean "I say no" that it IS NOT close enough?)
I have found a 10% difference in voltage to be about the cutoff for whether it works

---

### Post by cascade9 on 2010-03-25
LOl, not a problem. Wareface might have a big, scray avatar (OK, its the same size as everybodys *Edit- no its smaller!) but he (she?) is just a pussycat :P (sory warefacegod) I really dont mind being instulted anyway. 

As for the 'positive/negative' issue- its a pain. Just because the plug fits doesnt mean that the voltage is 'the rigth way around. Hmm, easier to use a pic- 

[IMG]http://www.dansdata.com/images/averfotoplay/rear640.jpg[/IMG]

See how next to the 'DC in' socket there is a little symbol, with a '-' negative sign on the outer ring, and a '+' positive sign on the pin in the middle? That means that it needs nagative to the outside, and the inner side is positive. You could very well find something, somewhere, that uses the exact same sized plug but with negative in the centre and positive on the outside. 

How much that actually happens, to be honest, I dont know. I try to avoid things with a AC/DC adapter, in part because of *slaps forhead* I once blew up a set of speakers from using the wrong AC/DC adapter. *Edit, mainly for ubunterooster- and the voltage was right, the amps were within 10%. Maybe I was just really unlucky? 

The other reason why I try to avoid them is because the 'power birck' in most cases always draw current, even when the item it is powering is truned off. I've you've got anythign that uses a AC/DC power brick, you can feel it is warm even when its not powering anything.

---

### Post by Chris Edgell on 2010-03-25
But in the reference to the positive and negative, the only time it would pertain to this subject at hand would be if I were to REPLACE the plug (jack) -- that seems like the only time I would be facing two wires, one + and one -
Is this what audiomich, and now you, are referring to?

[color=blue]Cascade your post intervened since my question to rooster...I LOVE your post. I get it!!  Very good!![/color]

---

### Post by cascade9 on 2010-03-25
Hmm, wires crosed. ;) 

For the speaker plug, you will actually have 3 wires. The 'tip' is left, the 'ring' is right, the 'sleve' is ground. 

[http://en.wikipedia.org/wiki/TRS_connector#Tip.2Fring.2Fsleeve_terminology](http://en.wikipedia.org/wiki/TRS_connector#Tip.2Fring.2Fsleeve_terminology)

I was refering ('m pretty sure that both audiomick was as well) to the DC input plug (like the pic I posted above)

---

### Post by ubunterooster on 2010-03-25
@cascade: I think (it seems likely those were speakers you salvaged) that the speakers were discarded because they were faulty. Speakers would not blow with correct voltage otherwise, normally.

@chris edgel: Yes, it only pertains to replacing when you face + and - where they can interferre.

---

### Post by warfacegod on 2010-03-25
Look for this symbol on your adaptors and on your speakers, if they match then you're good to go. At least in the +/- area.

Voltage should be exact.

Amps can be somewhat different but not too much. For example: if your speakers need 1 amp then 0.7 - 1.3 should be fine but don't range too high. My sister (unbeknownst to me) tried to use the AC adapter for my laptop to run her laptop. She fragged her entire laptop because it only needed 1.4 amps (or in that area anyway) and my adapter puts out 6.3 amps. It was bad. Everything cooked.

Twisting together the wires and using electrical tape is fine. Just make sure the connections are tight and ***don't*** reverse the +/- wires. Usually when I wrap a wire in electrical tape, being certain that no metal is visible by wrapping about two inches to either side of the new connection. I then soften the tape with a lighter and squeeze it so that it seals better. (Just don't do this on the wiring to your house!)

---

### Post by Chris Edgell on 2010-03-25
Oh, that must be a "power brick" for my flat-screen monitor, (yes, it's always quite warm).  Does it use MUCH electricity, shall I ever unplug this computer at night?)

I don't see any such marking +, -, for the AC devices I have.  

I'm thinking that MOST things in the USA are AC, but maybe not.

Cascade THAT is a great article at the link.  Thanks.

---

### Post by warfacegod on 2010-03-25
Most consumer electrical in the U.S. is AC. Some DC appliances are available to consumers but they are generally meant for running off of solar panels.

---

### Post by cascade9 on 2010-03-25
You wont need to unplug your computer at night. It doesnt use that much power, its just something I try avoid. With my curent speakers, I've got a power birck as well..and the way I deal with it is to either use a power board with anoff switch, and turn that off when I'm not using the computer. Or, because my good power board doesnt have a switch, I turn off the switch for the power point when I shut down my computer. 

I dont know if you have a switch on every power point in the US, if you dont, you can just unplug the power brick if it worries you. 

> **ubunterooster said:**
> @cascade: I think (it seems likely those were speakers you salvaged) that the speakers were discarded because they were faulty. Speakers would not blow with correct voltage otherwise, normally.

Nah, they werent 'found item' :D speakers. I'm pretty sure that the speakers were fine, I blew the thing that they were calling an amp. I might have made a mistake, it was a logn time ago (1997) when I knew far less than I do now, so I migth have made some other mistake. I wouldnt mind knowing what audiomick says about that, I'd bet he knows more about eletrickery than I do.

---

### Post by ubunterooster on 2010-03-25
most plugs for ac only fit one way so they are not marked. As for power bricks they should be unplugged at night. (actually you should have a surge protector that has a switch)
Amperage is reccomened to not exceed 50% of needed power, but with devices such as  speakers they should have resistors to stop an overly strong current.

---

### Post by warfacegod on 2010-03-25
> **ubunterooster said:**
> @cascade: I think (it seems likely those were speakers you salvaged) that the speakers were discarded because they were faulty. Speakers would not blow with correct voltage otherwise, normally.

Play them loud enough and they'll blow.:p Except maybe Klipsch, those can take an unbelievable amount of punishment.

---

### Post by ubunterooster on 2010-03-25
Allow me to correct/clarify what I meant. The vast majority of devices have resistors to stop too much power. However, if you more than double it *sometimes* the power archs around the transistors frying stuff below

---

### Post by Chris Edgell on 2010-03-25
One more question, concerning the size of the wire, could I splice a plug jack from one speaker set to another with a different v. and/or amp amount?

---

### Post by warfacegod on 2010-03-25
> **Chris Edgell said:**
> One more question, concerning the size of the wire, could I splice a plug jack from one speaker set to another with a different v. and/or amp amount?

Assuming the plug is the correct size then yes.

---

### Post by ubunterooster on 2010-03-25
Are you trying to splice a power cord for two speakers that use different amperage and voltage? Not a good idea.

---

### Post by audiomick on 2010-03-25
> **ubunterooster said:**
> Are you trying to splice a power cord for two speakers that use different amperage and voltage? Not a good idea.

This is true, but only in one direction. 

The critical thing is how much copper is in the wire. The plastic around it is not that relevant.

It is not a good idea to put a plug that has a thin wire onto a power supply with a fat wire, because the thin wire and the plug might not be able to take the current that the power supply can deliver.

Putting a plug that has a fat wire onto a power supply that has a thin wire is not a problem, because the plug and it's wire should easily be able to handle the current that the power supply can deliver.

Remember, the amount of copper is the relevant point, not the plastic.

I think your questions have otherwise been answered, haven't they?

---

### Post by ubunterooster on 2010-03-25
@ edgell: Oops, I was thinking you wanted to split the wire for use on two different kinds of speakers at once.
  Yes, you can splice it, the likelyhood of the wire not handling the power is quite low in home settings [vs rock concert speakers]

---

### Post by nikef on 2010-05-03
Hi Chris  hope you are well ? ,just popped in to catch up on your post ,sorry its been a while .

I am contemplating weather or not to upgrade to the new version ubuntu 10.4 but i see there are lots of problems and mostly to do with wubi install ,i have used wubi ever since ubuntu 7.04 on my laptop and each time i have upgraded without any problems , my downfall is i never back up and i know that i really need to do this this time ,i have been very lucky not to have been caught out , i am not in a rush to upgrade to new version as i a very happy with 9.10 :D

---

### Post by warfacegod on 2010-05-03
It was essentially the same thing when 9.10 was released. Lots of people saying how buggy 9.10 was and that they were happy with 9.04. Have you considered creating a dual boot? Ubuntu with a separate /home partition doesn't need to be backed up. All of your settings will be in your Home folder so, if you frag your OS somehow, all you'll need to do is reinstall it if you can't fix it. Of course your Home folder should be backed up occasionally.

---

### Post by Chris Edgell on 2010-05-04
Hi all,

I am somehow touched and gratified to see that you have revived this thread.  I have missed very much being able to come here with my problems and receiving kind and well-rounded opinion and advise.

There were a couple of reasons I have not been here.  One: I began feeling embarrassed by my continuing display of a childish lack of understanding of the way computers work; 

Let me say here that another reason is that I have been waiting for Lucid to get smooth, because I WANT to use that - as it is supported for three years.  I'd like to rely on that long term support and go on from there.  IS this a good idea?  Does each new release keep expanding the size so that my 20 GiB hdd will become obsolete on its own with passing years of updates?

I DID put Karmic into my friends computer because it was full of viruses. ...that seems to have worked out well; but I still feel so limited by never having put two systems in -- side-by-side.  I DID do it one time but could never work out the boot for each.  I DO have that 4th Dell - I have left it alone - I want to keep the MS but again I don't have the password -- but still I'd like to put another OS in side by side, although even as I think about it...I hit upon the third reason you haven't seen me...THE WEATHER IS NICE...I am not so likely to be holed up in here 2 or 3 days at a time.... so that's a good thing.

Well, nice to be here again, I'll try to look back here soon, now that the ice is broken.  Hope all is well with you all.

---

### Post by ranch hand on 2010-05-04
Glad the weather is good for you.  We have 45 to 65 mph wind today.

If I were you I would wait to install 10.04 for a while.  It works pretty good.  I am on it now.

It is, as you say, an LTS release.  I still use 8.04 (last LTS) as my secure OS.

This does mean, however, that while it was put out in the same time as the "regular" releases, it will be treated differently.  There will be a new ISO released for 10.04.1 on July 29.  This will include all the updates and fixes up to that date.  It should be a better, more reliable thing to install at that time.

You could get the Live CD and try the current one out to see if it works with your hardware.  There are still some problems in that regard.  If you install it and keep it updated it will, of coarse, be the same as the 10.04.1 release when that comes out.

It is a very nice OS.

I would look into getting a bigger drive than what you are using.  They are fairly inexpensive in sizes under 150Gb because everyone wants a BIG drive.  20Gb is plenty to run the bugger on but leaves a lot to be desired for storage space.

Also a drive of 80Gb or bigger gives you room to dual boot and try out the current OS in development.  Testing for 10.10 starts very soon.  Or you could have another OS on the thing just as a backup.

I started dual booting so that I had one small install that I could try things out on before doing it to the OS I actually used (both were 8.04).  This is a good way to mess around and learn things without having to worry if you are going to mess something up on your main OS.

---

### Post by Chris Edgell on 2011-01-24
I use this opportunity to show newbies how thing persist.  When I have encouraged you to put an informative title to your post, it is because you may want to look back for that answer and if it is in the title you can easily find it -- and also others will see it -- more TOPIC than TITLE.

And here , for you to see how for months, even years, people search for tag words and go and read there again, long after the thread was solved or had at least sunk into what YOU might think was oblivion... but here I've revived this one more time, in the odd occurrence that this this thread has had 10,000 views.  It's hard to believe that so many foolish things I've said and done are still viewed...to any extent.

---

### Post by Rasa1111 on 2011-01-24
Yes Chris,
 and they will be viewed forever! :lol: lol
 ;)
<3

---

### Post by migs73 on 2011-01-24
> **Rasa1111 said:**
> Yes Chris,
 and they will be viewed forever! :lol: lol
 ;)
<3


They should rename it 'The Chris Edgell Megathread', I have to say I had to bow out at post #235 and jump to the end.

I now know the best things to do if I get hold of and old desktop.... wiggle all the wires!!

:lol:

---

### Post by Chris Edgell on 2011-01-24
I  was not looking to resuscitate THIS thread but only to commemorate the 10,000 viewings.

But still...I'm amazed you went as far as you did, Migs73...I myself had to go through it one time and make a "single post favorites" file folder, to mark the main things I learned and wanted to be able to refresh my memory about.  Even as I brought it up, I thought I'd read it again, I and started...but felt embarrassed at my absurdity at times...the ignorant and the foolish...but still, it was me and I learned a lot.

Just today, I took that original old Antec, that I called the Junk Yard Dog, as I'd bought it at a yard sale, and hooked up a good hard drive... and it still works...back when I gave it up, I hadn't been able to see that just because the hard drive gots ruined, that everything else usually is still working.  I'm glad I didn't throw it out...I'll get one of those huge old monitors that cost $5 right now...and set somebody else up with a computer.

Now my misadventures are on the thread about "Where are the uninstalled when it says ALL"  I don't really intend to spin a long one this time but rather to ask individual questions.  As I've said there, I have finally understood a lot about the hardware in these old boxes.

My next real project will be to get going with Lucid for the Long Term Support...I never got it off the ground and just finally had reverted to the Jaunty, when I had thought I'd messed up my MAIN machine, and then didn't have a second one going to experiment with.

Bye now...

Chris

---

### Post by overdrank on 2011-01-24
Move along nothing to see here. :)

---

