---
title: "Screen goes blank- hardware or software?"
date: 2010-04-11
forum: New to Ubuntu
---

### Post by popejimbo on 2010-04-11
Okay, first let me say that although I have been getting by nicely until now, I do still consider myself a beginner in the ways of Linux. 

Basically the problem is my screen going totally blank at different times. Sometimes it will be after the computer has been on for a while, and recently it has been happening within seconds of booting. I've been a Ubuntu user for around 2 months after losing patience with windows, and ditching it altogether. For the most part it has been a happy two months, with any problems being solved with the help of this excellent forum without too much effort. Until 3 days ago.

I was checking my emails through FireFox and the screen just went inexplicably blank. I tried all the usual keyboard combinations, to no avail. After trying all i could think of for 5 mins or so, I gave up and just did a hard restart. The computer then did a filesystem check, which i was expecting, and found an error, which i tried to fix with the "fsck" command.

Halfway through the "fsck" function, the screen went blank again, and my screen informed me that there was "no signal". In frustration, i restarted with ctrl, alt, delete. I then went through the same cycle twice, having to restart again. I then decided to see if i cud go through the fsck command blindly without the screen. so i gave the scan a long time to complete, and then just started blindly jabbing away at "Y" to fix any of the filesystem errors, then after about 20 mins of this i restarted. 

After this Ubuntu started booting with no problems. I signed in and thought the problem was over, but then about 3 mins later the screen went blank again, and informed me that it wasn't receiving a signal. Once again i tried to reboot in all the usual ways...nothing. So another hard reboot, this time no filesystem problem, but upon signing in a few mins later...lo and behold....blank screen!

I looked around this forum, and tried everything that i could find...no joy.
So then i decided to reinstall. I thought i'd get all my data backed up circumventing ubuntu altogether to avoid the blank screen problem. To do this I booted Puppy Linux form a live CD. It booted up without any problems and i thought that the problem was definitely with Ubuntu. However, just as this entered my head...yep you guessed it... BLANK BLOODY SCREEN:lolflag:.
That led me to wonder if it was a hardware problem. So i tried another screen, an old 15 inch one. Same problem...so its not my LCD screen. 
So I got to wondering if it could be a problem with my graphics card: an Nvidia Geforce 220. So I did a quick Google search and did find a Windows 7 forum where someone had the same problem with Ubuntu nowhere in sight, where it turned out the Nvidia 220 was found to be the problem.

So, as far as I can tell, the problem IS a hardware problem, and I need to get in touch with PC World since my computer is only  3 months old and still under warranty,

The reason I post this, is just to make sure I'm not missing something obvious.
Is this, from this evidence, looking like a hardware problem to everyone else too?

Thank you in advance for any answers/advice:)

---

### Post by LewRockwellFAN on 2010-04-11
Yes. Sounded like the graphics card even at the beginning of the story. By the end of it, sounds like a 3 to 1 bet.

---

### Post by popejimbo on 2010-04-11
Thanks LewRockwellFAN. A problem with the graphics card did seem to be the logical answer. However I'm still learning not only with Ubuntu, but computers in general, so I wouldn't put it past me to miss something that would be glaringly obvious to someone in the know. Up until December my acquaintance with computers was passing at best, and since I'm still such a novice I thought it would be best to double check. 

Anyone else care to second LewRockwellFAN's diagnosis? Any and all replies are much appreciated.:)

---

### Post by 3rdalbum on 2010-04-11
Go into the BIOS setup screen and stay there, and if the problem occurs it's a graphics card problem.

---

### Post by popejimbo on 2010-04-12
@3rdalbum: Cheers for the suggestion, I didn't think of that one. More often than not the simplest ideas are the best. I'll try that out later.

If the screen doesn't go blank while in BIOS, what other possibilities could there be for the problem? I know that's getting ahead a bit, but I'm only asking out of curiosity. I know for sure that it isn't the screen itself because I'm using it now on my back up Puppy Linux computer without any issues what so ever.

(On a side note, if anyone is looking for a small distro for an old computer I cannot recommend Puppy Linux enough. It runs beautifully on this 10 year old box!)

---

### Post by quadproc on 2010-04-12
> **popejimbo said:**
> @3rdalbum: Cheers for the suggestion, I didn't think of that one. More often than not the simplest ideas are the best. I'll try that out later.

If the screen doesn't go blank while in BIOS, what other possibilities could there be for the problem?)
There is a chance that you might have a memory that is going bad.  Does your memory do error detection?  Error correction?  If so, then memory problems would likely be reported if they occur.  If not, then strange, bizarre, and unpredictable things can happen.  A frequent suggestion to wring out memory problems is to run memtest instead of the normal system, and to let it run overnight.  With a little luck the test will catch memory errors before the system blanks out.

You could also try removing some of the memory and seeing if the problem still happens.  Often, you have to remove (or install) the memory boards in pairs.

I presume that you are not overclocking, and that the system has good cooling.  High temperatures can cause intermittent problems.

Your problem does sound like a video board with an intermittent.

I once worked for a computer company and from them I learned that the greatest failure rate they had was due to printed circuit boards failing.  The boards had higher failure rates than the components on them.  I guess that PC board technology is not as robust as semiconductor technology.

Good luck!

quadproc

---

### Post by popejimbo on 2010-04-12
> **quadproc said:**
> 
I presume that you are not overclocking, and that the system has good cooling.  High temperatures can cause intermittent problems.



Nope, no overclocking and as far as I can tell the system has good cooling. Its kept in a well ventilated area and never does anything too taxing. The highest demand it ever has put upon it is from a game my younger brother plays online called Evony, although to be fair the strain could just be on our internet connection. The only other things that seem to register significantly are when I record my desktop, or when I'm converting files.

Thank you for the help and good wishes quadproc.

---

### Post by 3rdalbum on 2010-04-12
> **popejimbo said:**
> The highest demand it ever has put upon it is from a game my younger brother plays online called Evony

Lol, a bit off-topic here, but have you seen the ads for Evony? I hope your brother isn't playing the game with the hope that he'll actually be able to meet the girls in the ads :-)

> The only other things that seem to register significantly are when I record my desktop, or when I'm converting files.

I'd also suggest a memory test. Run Memtest86 from the GRUB menu. Run it overnight.

---

### Post by popejimbo on 2010-04-12
Okay, I tried to go into my BIOS to see if the screen would go blank, but every time I hit esc (what it was telling me to press to get into "setup", which I'm assuming is BIOS) it kept going to the GRUB loader. So I decided to run the memtest. I set it up running and settled down to watch a film (incidently Crank- Not that good to be frank), and the screen was blank when I came to check it about half way through the film. Does this prove that it is a graphics card problem?

@ 3rdalbum: I know, lol. But as anyone in advertising will tell you: "sex sells"lol. I would imagine that that's what drew him in in the first place. The poor fool.

---

### Post by quadproc on 2010-04-14
> **popejimbo said:**
> Okay, I tried to go into my BIOS to see if the screen would go blank, but every time I hit esc (what it was telling me to press to get into "setup", which I'm assuming is BIOS)
"setup" is part of your BIOS's functions.  BIOSes vary in their operation but most of them will put you into setup mode when you press the DEL, ESC, F2, F8, F10, or F12 keys before you get to the grub screen.
>  it kept going to the GRUB loader. So I decided to run the memtest. I set it up running and settled down to watch a film (incidently Crank- Not that good to be frank), and the screen was blank when I came to check it about half way through the film. Does this prove that it is a graphics card problem?
Pretty much so.  The problem might be in some other hardware but that is really unlikely.

Seeing the failure while running memtest does rule out all of the Ubuntu/linux software because memtest is a standalone program which only uses the really simple "glass teletype" functions of the video card.  You might want to make one other hardware check if it is reasonably convenient to do so: measure the power supply voltages while the system is running.  A voltage that is off by more than 5% is suspect.  Most systems use +12 and +5 volt supplies.  You might also find +3.3, perhaps -5, perhaps -12.  Please be careful while probing around inside a powered on system - it is possible to fatally damage every subassembly in the computer if you accidentally bridge some points.

quadproc

---

### Post by popejimbo on 2010-04-14
Well that's good news. If its a hardware problem then its going to be free to get sorted because the computer is still under warranty:). I'll be calling PC World in the morning to get them to fix it. I won't mark this as solved until I've actually got the computer back in working order with some kind of repair report to post, just so people in the same situation can see this from beginning to end. 

I did find it odd that hitting esc took me to the GRUB screen though. Is this normal?

Thanks again for all your help guys, I'll keep you posted on the overall outcome:)

---

### Post by quadproc on 2010-04-14
> **popejimbo said:**
> 
I did find it odd that hitting esc took me to the GRUB screen though. Is this normal?

Good question - it depends on your BIOS and on when you hit the ESC key.  The usual sequence of things as seen by the user is:

Some kind of initial announcement screen, usually with mfg. logo
Another pretty screen with the setup and POST options listed on it (<-ESC here)
The grub menu
If you do nothing then the top grub menu entry is loaded and executed
Probably a few lines of kernel startup messages
If X windows is part of the loaded code then a login screen

Normally, there are delays of a few seconds between each of these items.  The line that says (<-ESC here) is when you would need to type an ESC or whatever character your BIOS wants to go into setup mode.

Apparently, your BIOS does things a little differently.

One thing that is certain: if you are using a standard installation then grub is the first thing that executes after the BIOS has finished its startup stuff.  In fact, at that time what your system is executing is stage1 of grub.  This will be followed by the appropriate stage1_5 of grub, and that will be followed by stage2 of grub.  You should be able to find these files under /boot/grub.  They are located on your boot disk.  There are several stage1_5 choices because there are several possible file systems that contain the kernel and the system will use the appropriate file.

You may be interested in seeing more information regarding the boot partitions, files, etc.  If so then you can get a very well written script from Sourceforge:```
sudo sh boot_info_script055.sh
``` which produces a neat report in the file RESULTS.txt (or whatever name it reports for you).

I hope that at least some of this is useful.

quadproc

---

### Post by ed-koala on 2010-04-14
I just fixed this exact same problem with my PC ...

It was severely dusty/dirty inside, which kept the cooling from working properly.  It was overheating!

Now here's a tip everyone laughs at, but works!  Use a leaf blower to clean out your PC case!!!  Yup, just don't start by having it right up close.  Fire that sucker up from a couple steps away and move in.  The dust will FLY!

---

### Post by tom66 on 2010-04-14
I wouldn't recommend a leaf blower or any kind of vacuum/suction device, because of the potential for static buildup. Just get a can of compressed air and spray the PC out, if it's dusty.

For the OP's problem it sounds like the graphics card is defective. The fact that it blanked out during a memory test pretty much means it's a hardware issue.

---

### Post by ed-koala on 2010-04-14
Well, overheating of the CPU will shut things down no matter what you are doing, but I only listed this as a possible because it was my problem. My fans were all clogged and my liquid cooling radiator was being blocked ... it was filthy.

Also, I've used a leaf blower on multiple PCs, multiple times.  As long as you are careful not to get super close and blow your wiring apart, or knock something loose, it does work and work well.  There is no static from wind.  I don't touch it to my PC, just wave it around near enough to clear dirt and dust.  Of course, the usual precautions must be taken when moving the PC to protect against static.

<< Proud owner of a now very clean PC case >>

ps - Temps before cleaning - 125-130 F
     Temps after cleaning - 85-89 F

---

### Post by quadproc on 2010-04-14
> **ed-koala said:**
>   There is no static from wind.
Au contraire.  Wind generates static electricity and fast wind generates LOTS of static electricity.  Semiconductor manufacturing places know this and they actually use ionized air when they have to expose electronic parts to moving air.  The ionization makes the air weakly conductive and this provides a leakage path to drain away the static electricity.  Fortunately, installed components _almost_ always have good immunity to static electricity due to the nature of the circuits, but not always.

I generally use a small vacuum cleaner to get rid of accumulated dust in equipment.  Compressed air has both the static electricity problem and the physical damage problem.

Now that my curiousity has been aroused, I got out my 3M ESD meter (which looks like a ray gun because it is) and measured a stream of 50 PSI compressed air from a nozzle at a distance of about 1 foot.  It measured very close to -1000 volts, that is, 1 kilovolt.

quadproc

---

### Post by ed-koala on 2010-04-15
I stand corrected.  Never knew plain old air might cause static electricity.

Hmmm, still lots of folks use compressed air cans to clean their PCs, so I doubt it's much of an issue, though caution is always advised.  I'd also guess climate could also be an issue, I live where static isn't much of a problem due to humidity levels.

I'm careful not to touch components without grounding first, always, so I've never had any problems from static.  And I always take my PC outside to clean it, as lots of flying dust in the house isn't a very nice thing.

One last bit of advice ... it is easier to remove dust if you don't try to manually wipe it off.  It blows away easily if it is just sitting there ... trying to wipe it just packs it down and grinds it into delicate components, even slightly, and makes getting it off harder, so I never touch the dust myself just blow it off.

---

### Post by popejimbo on 2010-04-18
Okay, I've contacted PC World and even THEY have admitted it sounds like a graphics card problem. That's pleasantly suprising because I honestly thought they would try to wriggle out of it. Well its booked in for Thursday this week, so I'll post and let you know if the problem is solved on Friday. Hopefully this thread will be getting a nice big SOLVED at that time:)

---

### Post by popejimbo on 2010-04-26
Okay, my computer is back from having a new graphics card fitted, and the problem seems to have gone completely. Ubuntu boots up perfectly and there have been no issues what so ever. In fact, my Compiz effects are noticeably smoother and the system seems to be running even quieter despite being a very quiet machine to start with.

Thank you to everyone who has replied on this thread. You have all been huge helps:)

Now... do I mark this as solved, or is that the job of a mod? I'm such a noob, lol.

---

### Post by popejimbo on 2010-04-26
Okay never mind.... I just worked out how to mark as solved.

So it is with great pleasure that I declare his thread...SOLVED! Lol.

Thanks again everyone for all the advice:)

---

