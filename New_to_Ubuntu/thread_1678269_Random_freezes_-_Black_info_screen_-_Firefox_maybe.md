---
title: "Random freezes - Black info screen - Firefox maybe?"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by jd2012 on 2011-01-30
Hi, 

Ubuntu seem to be freezing randomly while in the middle of general use.
What is the black screen that displays AFTER the GRUB menu and BEFORE the login screen at start up?
It displays some info in white lettering with [OK] at the end of each line. 

THAT's the screen it goes to after it freezes.

It does it more commonly when using firefox or listening to music.

Mouse doesnt work, keyboard, nothing. Tried all Ctrl + F(button) Combos, nothing seem to work besides the infamous power button.

Heres a few specs:

ASUS K50IJ Best buy edition.
Intel Pentium Core 2 DUO @ 2.0 GHZ
[COLOR=#000000]Intel GMA X4500M Graphics
Ubuntu 10.10 MM Dual Booted W/ windoze 7

Questions/Comments?

Thanx in advance. [/COLOR]

---

### Post by ksprasad on 2011-01-30
Hi,
 
 Have you enabled desktop effects? If so, you can try disabling some of them.
 I was also facing exactly same issues and I disabled desktop effects. Now everything seems to be fine. :)
 
Regards,
ksprasad

---

### Post by jd2012 on 2011-01-30
> **ksprasad said:**
> Hi,
 
 Have you enabled desktop effects?

Howdy, 

Not sure I fully know what desktop effects are? After some quick googleing I CAN say I have a couple screenlets.

Anyone else experience problem similar to I with screenlets?

Thanx.

---

### Post by mikewhatever on 2011-01-30
Check the system->administration->appearance, Visual Effects tab. Try turning them off as suggested by ksprasad above.

---

### Post by dchrono on 2011-01-30
create this file

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```

and add this option
 
```
FRAMEBUFFER=y
```

save the file, then

```
sudo update-initramfs -u
```

cheers

---

### Post by P4man on 2011-01-30
You mean a black screen with a blinking cursor top left, or full of text?

Anyway a few things. Rather than hitting the reset button, next time your machine freezes try these keycombo's first:

```
control+alt+F1
```

If the problem is just the usermode videodriver, then control control+alt+f1 should give you a full screen terminal window where you can log in, and we can trouble shoot further. IF that doesnt work, try this instead:

hold down altgr+SysRq (usually printscreen key). WHile keeping those 2 keys down, slowly type:
REISUB

That should gracefully reboot the machine (syncing filesystems before doing so). More info here:
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

Now these are not real solutions obviously, we need some more info before we can start guessing about the cause and  how to solve it. First thing Id like to see is the output of your dmesg log. Go to system > adminstration > log file viewer. Open dmesg. Copy paste it all here (please use the forum [ CODE ] tags around it). Perhaps do the same for syslog.1

Also, next time you have a freeze, look at your watch and note the time. Then you can go in to those log files and find entries that occured at that time, which should be a great help pinpointing the problem.

---

### Post by jd2012 on 2011-01-30
Hi all, 

Thanx for replies.

I tried to disable visual effects as suggested above, no dice.
It seems to do it more often now, upwards of 20 times a day, and also while using firefox. Did it once while trying to reply to this message, tried ctrl + alt + F1, nothing.

@ P4man, logs are a no go as they are pretty lengthy. If needed i can upload them to hotfile. Request times out when putting in code tags in the reply, and they are too big to attach. 

*Side Note(s)*
1) The CAPS lock button does NOT blink, so its not a failing kernel.
2) The log viewer AND firefox became unresponsive while copying the logs, this is unusual as ive did more reasource demanding tasks, 
and this box didnt even flinch.
3) Did it again (3rd time) trying to reply to this thread, this time I got a disk check at the purple ubuntu splash screen, took all of 5 seconds.
4) New symptom, sometimes when it happens it doesnt go to the screen with text, its goes to an all black screen, with my cursor showing which is unresponsive.


Again, thank you all for looking.

---

### Post by jd2012 on 2011-01-30
> **dchrono said:**
> create this file

```
gksu gedit /etc/initramfs-tools/conf.d/splash
```and add this option
 
```
FRAMEBUFFER=y
```save the file, then

```
sudo update-initramfs -u
```cheers

Hi, 
Thanx, Didnt help with the crashing although I believe this was the reason for the black screen going from "Black splash screen with text" to "Plain black screen with my frozen mouse pointer".

---

### Post by jd2012 on 2011-01-30
> **P4man said:**
> hold down altgr+SysRq (usually printscreen key). WHile keeping those 2 keys down, slowly type:
REISUB


Thanx, but doing this had no effect at all. :confused:

This problem is very aggravating as I would hate to reinstall ubuntu, espically after tweaking it to my liking. ;)

---

### Post by P4man on 2011-01-31
We need those log files. Copy paste parts of it around the time of the latest freeze, or upload them entirely to mediafire or pastebin.
It could be anything, but Im guessing it will be a hardware problem, like a problem with the harddisk or ram.

---

### Post by jd2012 on 2011-01-31
> **P4man said:**
> We need those log files. Copy paste parts of it around the time of the latest freeze, or upload them entirely to mediafire or pastebin.
It could be anything, but Im guessing it will be a hardware problem, like a problem with the harddisk or ram.


Hey, 

Last night I booted into the recovery console with limited graphics, only to have my system hang and a blinking CAPS lock light   ](*,)
Ran memtest only to get a "too small, lower memory" error. :confused:

So I reinstalled ubuntu... still persists, thus pointing to a hardware issue as you said.
Not sure if it matters much but ive never had any problems with windoze, wonder why ubuntu is mad at my hardware, or vice versa?

On a side note I used a patch in this thread:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
To patch my wireless drivers so they support packet injection. 
Been playing around with my wireless router ;)
I hope the patch isnt the cause, but at the same time hardware failure isnt good either.

Heres the log you requested close to the time of the most recent crach/hang:

syslog
[http://pastebin.com/tGBkek53](http://pastebin.com/tGBkek53)

ALL of dmesg
[http://pastebin.com/0i5KgKTd](http://pastebin.com/0i5KgKTd)


Thanx again for your help.

---

### Post by Nickjpost on 2011-01-31
What drivers do you have selected for your video card? I had a similar issue: [http://ubuntuforums.org/showthread.php?t=1677211](http://ubuntuforums.org/showthread.php?t=1677211)
 
at the bottom of the thread, I put a link that helps idientify the proper open or closed source drivers to have installed per your computer specs. Also, if you have too many or conflicting drivers, this may be causing the issue as well.

---

### Post by ksprasad on 2011-01-31
Hi,
 
One thing I forgot to ask. Is it freezes in Windows 7 also? If so, then it is H/W problem.
 
Regards,
Ksprasad

---

### Post by quadproc on 2011-01-31
> **jd2012 said:**
> 
What is the black screen that displays AFTER the GRUB menu and BEFORE the login screen at start up?
It displays some info in white lettering with [OK] at the end of each line. 

There are actually two screens that would normally occur during that time frame: the first screen is present while the kernel is loading and initializing, then the second screen displays the splash (if splash is enabled).  On my hardware, the first screen lasts 15 seconds and the second lasts about 4 seconds.

The stuff that you described with text messages sounds like system messages and you will probably find copies of those, along with a lot of other stuff, in the system logs.

As others have noted, it is certainly possible that you have a hardware problem occurring.  I presume that you are not overclocking; if you are then I would suggest backing it down some.  You also may have a temperature problem - checking for dust accumulations, clogged filters, etc. would be advisable.  If you haven't installed a temperature sensor daemon then I would suggest running one.

The symptoms could indicate a marginal memory.  memtest86 may be able to find that.  Does your system use EDAC (error detection and correction)?  Parity?  Nothing?  Almost all electronics works more poorly at higher temperatures so warming up your computer by partially obscuring ventilation openings may be useful (edit: for troubleshooting only!).  But please don't overdo it!

The difference between Windows not showing problems while Ubuntu does could be entirely a function of how memory is allocated by each OS.  It may be that Windows has located something that you don't use in problem memory while Ubuntu does use that part of memory.

quadproc

---

### Post by P4man on 2011-02-01
> **jd2012 said:**
> Hey, 

Last night I booted into the recovery console with limited graphics, only to have my system hang and a blinking CAPS lock light   ](*,)
Ran memtest only to get a "too small, lower memory" error. :confused:

So I reinstalled ubuntu... still persists, thus pointing to a hardware issue as you said.
Not sure if it matters much but ive never had any problems with windoze, wonder why ubuntu is mad at my hardware, or vice versa?

On a side note I used a patch in this thread:
[http://ubuntuforums.org/showthread.php?t=1598930](http://ubuntuforums.org/showthread.php?t=1598930)
To patch my wireless drivers so they support packet injection. 
Been playing around with my wireless router ;)
I hope the patch isnt the cause, but at the same time hardware failure isnt good either.

Heres the log you requested close to the time of the most recent crach/hang:

syslog
[http://pastebin.com/tGBkek53](http://pastebin.com/tGBkek53)

ALL of dmesg
[http://pastebin.com/0i5KgKTd](http://pastebin.com/0i5KgKTd)


Thanx again for your help.

At first glance, those logs dont reveal anything wrong afaict, but I think those are logs from a succesful boot, and not from a freeze right? Check the older logs (ending with .0 and .1) and see if there is anything right before the last crash happened. If so, post that.

memtest not running isnt good, but to be fair, it doesnt prove a problem either, I have an OEM machine where memtest86 wont run either, even if the machine is perfectly ok.

To narrow down the problem, a few more questions and suggestions:

0) as above, check/post the log files at the time of the last crash

1) does the machine ever freeze or crash in a live session? IE, booting from USB or CD ? IF not, this might hint at a problem with the harddrive. Go to system > administration > disk utility. Select your harddrive(s) and check their SMART status. If smart status isnt available, enable it in the BIOS.

2) Try windows' ram test:
[http://www.tomstricks.com/how-to-test-your-ram-or-memory-with-windows-memory-diagnostic-tool-in-windows-7/](http://www.tomstricks.com/how-to-test-your-ram-or-memory-with-windows-memory-diagnostic-tool-in-windows-7/)

3) if none of the above shed any light on the issue, try ubuntu 10.04.

---

### Post by jd2012 on 2011-02-01
> **quadproc said:**
> There are actually two screens that would normally occur during that time frame: the first screen is present while the kernel is loading and initializing, then the second screen displays the splash (if splash is enabled).  On my hardware, the first screen lasts 15 seconds and the second lasts about 4 seconds.

The stuff that you described with text messages sounds like system messages and you will probably find copies of those, along with a lot of other stuff, in the system logs.

As others have noted, it is certainly possible that you have a hardware problem occurring.  I presume that you are not overclocking; if you are then I would suggest backing it down some.  You also may have a temperature problem - checking for dust accumulations, clogged filters, etc. would be advisable.  If you haven't installed a temperature sensor daemon then I would suggest running one.

The symptoms could indicate a marginal memory.  memtest86 may be able to find that.  Does your system use EDAC (error detection and correction)?  Parity?  Nothing?  Almost all electronics works more poorly at higher temperatures so warming up your computer by partially obscuring ventilation openings may be useful (edit: for troubleshooting only!).  But please don't overdo it!

The difference between Windows not showing problems while Ubuntu does could be entirely a function of how memory is allocated by each OS.  It may be that Windows has located something that you don't use in problem memory while Ubuntu does use that part of memory.

quadproc

Hi, thanx for your reply.

1) I only have one screen at boot, black w/white text, lasts MAYBE 2 seconds. This is the screen that im usually taken to at the time of the crash, says something about "setting sensor limits" and "checking battery state"

2) Na, havent gone into the world of OC'ing, although I did open the case of my laptop yesterday and clean it out (minimal dust/dirt) In terminal command "sensors" only shows 1 sensor (44.0c -Crit 111.0+)

3)  Any suggestions for temp sensor daemons? 

Thanx again.

---

### Post by jd2012 on 2011-02-01
> **ksprasad said:**
> Hi,
 
One thing I forgot to ask. Is it freezes in Windows 7 also? If so, then it is H/W problem.
 
Regards,
Ksprasad



Nope, windoze works flawlessly :mad:

---

### Post by jd2012 on 2011-02-01
> **P4man said:**
> At first glance, those logs dont reveal anything wrong afaict, but I think those are logs from a succesful boot, and not from a freeze right? Check the older logs (ending with .0 and .1) and see if there is anything right before the last crash happened. If so, post that.

0) as above, check/post the log files at the time of the last crash

1) does the machine ever freeze or crash in a live session? IE, booting from USB or CD ? IF not, this might hint at a problem with the harddrive. Go to system > administration > disk utility. Select your harddrive(s) and check their SMART status. If smart status isnt available, enable it in the BIOS.

2) Try windows' ram test:


Hey P4man, thanx for all you help/suggestions.

1) @ logs, I copied the part of the log on the exact minute it happened. If memory serves me right, it was 9 minutes after the hour, so my log goes from 10:06 -Crash- 10:09 and copied all the way to the end. If it doesnt indicate anything, than maybe the system doesnt get a chance to log the error before it crashes.
BTW: Magic keys NOTHING work after this system hangs so i believe the latter is pretty accurate.

2) @ live session, Im not sure, as ive never stayed on a live session long enough to kno :lolflag:

3) Just checked the SMART status of my disk, "2 bad sectors" but overall all lights are green and disk is in overall health: Attached screenshot.

4) @ windows RAM test, thanx for the link, I think im going to try that later on.

Again, thanx for your replies/suggestions

Sincerly, JD

---

### Post by quadproc on 2011-02-01
> **jd2012 said:**
> Hi, thanx for your reply.

1) I only have one screen at boot, black w/white text, lasts MAYBE 2 seconds. This is the screen that im usually taken to at the time of the crash, says something about "setting sensor limits" and "checking battery state"
That is quite speedy.  Of course, our hardware is very different so your startup probably has a lot less to do.  The note about setting sensor limits indicates that you _do_ have temperature sensors enabled already - this is good!  But I don't know why you are getting this screen without any apparent cause.
> 
2) Na, havent gone into the world of OC'ing, although I did open the case of my laptop yesterday and clean it out (minimal dust/dirt) In terminal command "sensors" only shows 1 sensor (44.0c -Crit 111.0+)
Good on the cleanliness.  Your one sensor is probably the CPU's built-in temperature sensor; 44 degrees is probably a reasonable number for that.  The system that I am using right now is a desktop in a big case with lots of air flow and it shows temperature readings ranging from 30 to 38 degrees, depending on which sensor I look at.  If I do something that makes a CPU very busy then sometimes the CPU sensor jumps up to around 44 degrees.  But this CPU has a *large* heat pipe and radiator system on it which probably weighs as much as a laptop so it could be expected to keep things fairly cool.
> 
3)  Any suggestions for temp sensor daemons? 
You don't seem to need to add any to your system so I won't suggest anything.  I found quite a bit of information on sensors by Googling for things like lm-sensors.

quadproc

---

### Post by jd2012 on 2011-02-03
****Update****

Wrote down all the info that comes up on the black screen, hopefully will help with diagnosing.

```

fsck from util-linux-ng 2.17.2
/dev/sda1/: Clean; 16664/12804096 files, 6658240/51200000 blocks (Check defferred; on battery)
*Starting AppArmor profiles                       Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
                                                                                           (OK)
Setting sensor limits                                                                      (OK)
Speech dispacher disabled; edit /etc/default/speech-dispacher
(Orange Star) * Pulse Audio configuration per user session
saned disabled: edit /etc/default/saned
* Enabling additional executable binary formats binfmt-support                             (OK)
* Checking battery state...

```

Also, im getting notifications from ubuntu on my desktop stating my battery may be broken, its only at 40% capacity.
Do you think that would have anything to do with it?

Thanx again for looking, hopefully this will help.

Suggestions?

---

### Post by quadproc on 2011-02-03
> **jd2012 said:**
> 
Also, im getting notifications from ubuntu on my desktop stating my battery may be broken, its only at 40% capacity.
Do you think that would have anything to do with it?

I have seen lots of reports that Ubuntu's battery reporting is either highly inaccurate or is completely wrong so I would not pay much attention to that report.  This problem seems to be a function of certain kinds of laptops; I don't know why some brands are troublesome.

The messages that you reproduced seem to be normal startup types of messages.  I did not see anything of concern in the messages.  The concern is that you are getting these massages on the screen when you believe that you should not.

quadproc

---

### Post by jd2012 on 2011-02-03
> **quadproc said:**
> I have seen lots of reports that Ubuntu's battery reporting is either highly inaccurate or is completely wrong so I would not pay much attention to that report.  This problem seems to be a function of certain kinds of laptops; I don't know why some brands are troublesome.

The messages that you reproduced seem to be normal startup types of messages.  I did not see anything of concern in the messages.  The concern is that you are getting these massages on the screen when you believe that you should not.

quadproc


Hey, thanx again for your reply.
I believe ive narrowed it down to a few possibilities:

1) Wireless drivers; they are ath9k Drivers patched for various reasons.

2) Firefox (Flash maybe)

3) Graphics card/drivers.

The reasons:

1) wireless drivers, after the fresh install of ubuntu i had no immediate problems, then i installed the patch, shortly after, crash ](*,) 

2) Firefox, it seems (almost) everytime the system crashes, I had firefox running, although when i bring the system back up, FF offers to restore my tabs.

3) Graphics: Funny thing is, when im running the preinstalled vista that came with this PC i use nVidia drivers, with an nVidia control panel ect, but with an off the street windows 7 cd, it seems im using intel drivers with intel control panel ect. Ditto with ubuntu, claims my graphics card is intel. The reason i say it may be causing the system crashing is sometimes when it crashes i had just tried to maximize a window the second before, or watch a video in fullscreen mode.

Again, any help/suggestions would be appreciated, and thanx for reading.

---

### Post by quadproc on 2011-02-04
> **jd2012 said:**
> Hey, thanx again for your reply.
I believe ive narrowed it down to a few possibilities:

1) Wireless drivers; they are ath9k Drivers patched for various reasons.

2) Firefox (Flash maybe)

3) Graphics card/drivers.


Here are some thoughts and suggestions that might help to narrow down the offending item.  Please note that it is entirely possible that you have more than one thing which is causing trouble so fixing one thing may not get rid of the problem right away.

Wireless drivers are certainly notorious for causing problems.  Can you run the system for testing without the wireless stuff being present?

Personally, I have not had much trouble with Firefox.  The trouble that I have seen is that Firefox sometimes loses windows that I had been using, but this may actually be an X windows problem.

Graphics card: I remember seeing some posts regarding full screen problems.  Sorry, I don't remember the details of the problems but it might be useful to search for something like "Ubuntu full screen crash" and see if someone has figured this one out.

quadproc

---

### Post by jd2012 on 2011-02-04
> **quadproc said:**
> Here are some thoughts and suggestions that might help to narrow down the offending item.  Please note that it is entirely possible that you have more than one thing which is causing trouble so fixing one thing may not get rid of the problem right away.

Wireless drivers are certainly notorious for causing problems.  Can you run the system for testing without the wireless stuff being present?

Personally, I have not had much trouble with Firefox.  The trouble that I have seen is that Firefox sometimes loses windows that I had been using, but this may actually be an X windows problem.

Graphics card: I remember seeing some posts regarding full screen problems.  Sorry, I don't remember the details of the problems but it might be useful to search for something like "Ubuntu full screen crash" and see if someone has figured this one out.

quadproc


Hey thanx again for replying.

Ive did some testing:

1) Ran the pc with network manager disabled (Right click > Uncheck enable networking)
..still crash

2) Downloaded google chrome, still crashes, although I believe chrome is using flash also, so if it IS flash, switching browsers might not help much :lolflag: Atleast i know its not solely a FF problem.

3) As far as the graphic/display drivers go, I cannot find **any** support on these. 'Additional drivers' in the admin tab shows nothing, as does google. Im starting to believe it IS these drivers, as the PC still crashes with a fresh install of ubuntu and windows runs flawlessly and shows no errors (weeding out hardware problems)

Im at a standstill ](*,)

---

### Post by quadproc on 2011-02-05
> **jd2012 said:**
> 
1) Ran the pc with network manager disabled (Right click > Uncheck enable networking)
..still crash
OK, this mostly rules out networking.
> 
2) Downloaded google chrome, still crashes
OK, that is useful to know
> 
3) As far as the graphic/display drivers go, I cannot find **any** support on these. 'Additional drivers' in the admin tab shows nothing, as does google. Im starting to believe it IS these drivers, as the PC still crashes with a fresh install of ubuntu and windows runs flawlessly and shows no errors (weeding out hardware problems)
This does make hardware a very unlikely problem but it is remotely possible that there is something wrong with the hardware which only shows up when it used differently than Windows uses it.  So please keep this in the back of your mind, in case nothing else can be identified.

I am not familiar with the Intel graphics hardware that you have, but I have noticed that Intel likes to use a chunk of system memory for their graphics system rather than putting memory on the graphics hardware.  This became a big problem in the recent Ubuntu releases because the linux kernel started to use something called kernel mode setting (KMS) by default.  Apparently, KMS does not get along well with Intel hardware.  A lot of people found that they needed to disable KMS by putting a suitable statement in the boot arguments for linux.  Have you tried this?

quadproc

---

### Post by jd2012 on 2011-02-05
> **quadproc said:**
> 
This does make hardware a very unlikely problem but it is remotely possible that there is something wrong with the hardware which only shows up when it used differently than Windows uses it.  So please keep this in the back of your mind, in case nothing else can be identified.
Understandable, and *noted*

> 
I am not familiar with the Intel graphics hardware that you have, but I have noticed that Intel likes to use a chunk of system memory for their graphics system rather than putting memory on the graphics hardware.  This became a big problem in the recent Ubuntu releases because the linux kernel started to use something called kernel mode setting (KMS) by default.  Apparently, KMS does not get along well with Intel hardware.  A lot of people found that they needed to disable KMS by putting a suitable statement in the boot arguments for linux.  Have you tried this?
@ KMS
No sir, I dont believe I have. But if it may help, under windows, in the intel control panel "Information" tab states that I have (cant remember KB or MB) but, 512 L2 cache. Not sure if this is what your reffering to as far as memory on the graphics hardware?

If it doesnt, can u point me in the right direction (tutorial wise) to a KMS info page?

Thanx again for all the help.



**Edit, Side note**

Just finished installing ubuntu (same PC, replaced HDD, fresh install)
Upon installing I decided not to download updates and run things "Out of the box"
Im noticing  sometimes (Been running PC for about 2 hrs, happened twice) that my screen will kinda lock up
everything moves slow, mouse pointer, animated images everything lags for a few seconds, stops (freezes) for a 
few seconds then comes back to life. CPU is showing no spikes ect, and not running any progs. Perhaps something in the updates,
new drivers ect? Btw, on THIS fresh install, the system has not crashed yet, but im waiting. Going to run updates then report back if it does.

---

### Post by quadproc on 2011-02-06
> **jd2012 said:**
> 
@ KMS
No sir, I dont believe I have. But if it may help, under windows, in the intel control panel "Information" tab states that I have (cant remember KB or MB) but, 512 L2 cache. Not sure if this is what your reffering to as far as memory on the graphics hardware?

No, that is a different memory.  I will try to do a brief explanation of what memories are part of a typical system, and why they are there.

The kinds of memories normally found in a personal computer these days are:
main RAM
level 2 cache
level 1 cache
processor registers
video RAM

The main RAM is the biggest amount of memory in most systems, typically 1 GB or more these days.  It might be as small as 256 MB in an older system.  It stores things like executing programs, tables of information, variables, file control information, and so forth.  This memory is usually the slowest memory in the system.

The level 2 cache is a smaller amount of memory which is used for "look ahead" purposes.  It is built inside of the CPU so that it has speedy access to the other parts of the CPU.  If you examine the code being run in a program, you will see that much of it proceeds in a "straight ahead" fashion; that is, the next thing to be done usually immediately follows the thing currently being done.  Therefore, it is useful to read the next thing while the current thing is happening.  The level 2 cache is used as a temporary place to store those things which the computer will probably need.  It is fairly large, in order that the probability of finding what the computer will need is high.

The level 1 cache is smaller than the level 2, but it is considerably faster.  It serves the same functions as level 2 cache, but because it is inside the processor it can be loaded much faster than the level 2 cache which has to get its data from the external RAM.  Also, the level 1 cache can speed up loops because all of the instructions in a loop will normally fit inside the level 1 cache so the CPU doesn't have to continually re-read those instructions.

The processor registers are actually a form of memory.  They don't hold very much data (probably a few hundred bytes) but they are really speedy, and they can interact with each other to do things such as arithmetic, comparisons, and address calculations.

The video RAM is a place which holds the values corresponding to the image displayed on your monitor.  Generally, each pixel is represented by one to four bytes of data which specify the brightness and color of each pixel.  Obviously, the video RAM needs to be several times as large as the number of pixels on your display.  Many graphics controllers have large amounts of video RAM built in to the controller; for example, the card that I am using right now has 1 GB of RAM on the card, and this RAM is independent of the system RAM.  However, in smaller or older computers, the extra size and power draw of additional RAM makes it undesirable so the designers of graphics controllers often arrange things so that the graphics controller "takes over" a portion of main RAM and uses that for the graphics display.
> 
If it doesnt, can u point me in the right direction (tutorial wise) to a KMS info page?
Here is an article that discusses KMS.  See especially  the part under **Update:** [Here's a pretty good tutorial on working with GRUB 2]("http://ubuntuforums.org/showthread.php?t=1195275").
[http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html](http://www.insidesocal.com/click/2010/02/intel-82830-cgc-830m-graphics.html)

> 
**Edit, Side note**

Just finished installing ubuntu (same PC, replaced HDD, fresh install)
Upon installing I decided not to download updates and run things "Out of the box"
Im noticing  sometimes (Been running PC for about 2 hrs, happened twice) that my screen will kinda lock up
everything moves slow, mouse pointer, animated images everything lags for a few seconds, stops (freezes) for a 
few seconds then comes back to life. CPU is showing no spikes ect, and not running any progs. Perhaps something in the updates,
new drivers ect? Btw, on THIS fresh install, the system has not crashed yet, but im waiting. Going to run updates then report back if it does.Momentary freezes are usually due to either hardware problems or to something causing the CPU to become very busy.  Sometimes a busy CPU does not show up in reporting software such as _top_ or the system monitor because either the usage is inside the kernel or because the CPU is so busy doing whatever that it never gets a chance to update the reporting software.  I understand that _htop_ is better at reporting obscure usage problems but I haven't tried it myself.

Edit: I had another thought about the intermittent and temporary freezes: you might be seeing the effects of swapping.  Have you looked at memory usage when this effect occurs?

quadproc

---

### Post by jd2012 on 2011-02-06
Thanx for the info and links.

Sorry this one's being such a pain :confused:

Been noticing something, but didnt think it was of importance until now.
It seems the problem is occuring MUCH MORE often when running on battery power.
(2-3 times in 10-15 min on battery, vs. Once every few hours on AC power)
Also, been having some trouble with my sound today, perhaps that has something to do with it?
Gonna do some googling hopefully something will turn up.

Any questions/suggestions, Im wide open.

---

### Post by quadproc on 2011-02-06
> **jd2012 said:**
> 
Been noticing something, but didnt think it was of importance until now.
It seems the problem is occuring MUCH MORE often when running on battery power.
(2-3 times in 10-15 min on battery, vs. Once every few hours on AC power)
(I think that we both posted at the same time so please reread my previous post)
The frequency of problems vs. power source suggests that there is some kind of a power supply problem.  Can you use a voltmeter to check the DC voltages being produced by the power supply?  Also, if possible, connect an oscilloscope to the power supply outputs and look for noise, oscillation, or other undesirable characteristics?

quadproc

---

### Post by jd2012 on 2011-02-06
Im going to swap HD's and use (my fresh install) of ubuntu, if the problem persists, then I can most likely confirm that it is a hardware issue.

Will post back. Thanx again.

:KS

---

### Post by jd2012 on 2011-02-07
Been running the new system for some time now and cant seem to get it to crash. 
Havent installed ANYTHING, not even updates...

Perhaps a theme (on my old sys) is causing the crash? Just spitballing here.

---

