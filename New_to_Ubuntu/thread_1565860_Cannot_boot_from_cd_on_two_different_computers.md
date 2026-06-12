---
title: "Cannot boot from cd on two different computers"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by captainiom on 2010-09-01
]I thought I would have a go at seeing how Ubuntu measures up. I am familiar with several versions of Unix (and currently run a couple of Sco Unix systems), and have computers running every version of Windows since 95 thru to W7.

So I followed the instructions to download and create an ISO on CD. I then wished to get a feel for the O/S simply booting from CD to avoid installing in parallel or stand alone which would require a free m/c.

So far I have tried a W7 m/c which has:
AMD Athlon 64x2 6000+, 2GB, default monitor 1024x768 and graphics on ATI Radeon HD3400 series.

Cd starts to boot and I see a logo at bottom of screen with a stick figure surrounded by a circle. There is considerable CD activity but it then shuts the computer down completely. This is repeatedly consistently.

Assuming this might be video card related I switched to an XP m/c which has:
AMD Athlon 64x2 4600+, 1gb, default monitor 1024x768 on VIA Chron9 HC IGP.

CD gets further moving to a second screen with UBUNTU and 5 radio buttons which change from white to red over about a minute. They then freeze on red and m/c hangs. This also repeats consisitently except for one time when it moved to another screen which I suspect what is called 'splash' - multicolor rather like Windows aero. It then froze.

I would really like to try out this O/S so how do I proceed please?

---

### Post by Rex Bouwense on 2010-09-01
Did you md5sum the download before you burned the ISO?  It sounds like you got a bad download or a bad burn.  I would try another download.

---

### Post by walt.smith1960 on 2010-09-01
I tried burning a DVD-RW and had something similar happen.  Burned a CD-R from the same .iso file and that worked properly.  In my experience CD-Rs are sorta wasteful but seem the most reliable.  I had burned DVD-RWs in the past and they worked okay but that one time failed.  Bad wipe?

---

### Post by Snark1994 on 2010-09-01
When you get to the bit with the 5 "radio-buttons", you can press a key (I'm pretty sure it's Esc) which tells you what it's trying to do... It's not certain, but it might contain some error messages which tell you what it might be upset about.

From personal experience, the only time I've been unable to boot from CD is on my gran's PC, and it worked fine when I replaced the CD drive (though the CD drive worked acceptably in XP and would even start booting, it would never finish and would either hang or shutdown. Go figure.)

Hope that helps...

---

### Post by NoNameWill on 2010-09-01
It could be bad cd-r's I have some cheapies that my emachines burner will read and burn to but my laptop will not read/burn them. I had to use a name brand disc to use. And I also slowed the rate of burn down.

---

### Post by cariboo on 2010-09-01
@Snark1994, is correct, press any key when you see the keyboard and the man, this will bring up the menu. Once you've selected your language, press F6 and select nomodeset. Press ESC, then press enter to start the process.

---

### Post by captainiom on 2010-09-02
> **cariboo907 said:**
> @Snark1994, is correct, press any key when you see the keyboard and the man, this will bring up the menu. Once you've selected your language, press F6 and select nomodeset. Press ESC, then press enter to start the process.
 
Followed this precisely on the W7 m/c.  This brings me to same position as on the smaller XP m/c i.e. the UBUBTU name and radio buttons come up and there is cd activity while the buttons change left to right white to red.  It then freezes consistently with the keyboard two right hand lights flashing together about every second.
I can go back to start and download/burn again if you think that might be problem.  The burn was to a cd/r from a pack which has not given trouble in past.

---

### Post by Snark1994 on 2010-09-02
> **captainiom said:**
> Followed this precisely on the W7 m/c.  This brings me to same position as on the smaller XP m/c i.e. the UBUBTU name and radio buttons come up and there is cd activity while the buttons change left to right white to red.  It then freezes consistently with the keyboard two right hand lights flashing together about every second.
I can go back to start and download/burn again if you think that might be problem.  The burn was to a cd/r from a pack which has not given trouble in past.

Did you try pressing ESC when it gets to this stage? It should tell you the things that the CD is trying to do in the boot process, including any errors it has encountered...

---

### Post by captainiom on 2010-09-02
> **Snark1994 said:**
> Did you try pressing ESC when it gets to this stage? It should tell you the things that the CD is trying to do in the boot process, including any errors it has encountered...
 Yes - no joy.
 
So I considered other replies and decided to check the ISO and re-burn - this time using the built-in W7 burner with verification.
 
Just done that and am pleased to report that providing you do the breakout to menu the O/S loads the splash? screen and then a GUI.  It took a long time though   (:
 
Looking forward to an evaluation.

---

### Post by captainiom on 2010-09-08
Please mark thread as solved - not sure how to do this.
 
Evaluation now complete ex CD.  Very impressed with ease of use.  Have now installed on a clean 500gb drive with 1gb memory.  Installation was just about the simplest of any O/S I have encountered ( and that is a hell of a lot!)
 
I find the documentation a bit difficult to penetrate.  For example, the lock screen requiring a password to start up again is far too soon - a few minutes - so I want to either change the time or perhaps disable the facility altogether.  Using the search facility in help has me flouindering around in Gnome setup etc etc but so far nowhere obvious that simply says "Set timeout on lock screen to ???"
 
Other than that problem I am impressed and will continue to evaluate seriously with a view to discussing options with some of my clients.

---

### Post by captainiom on 2010-09-08
But I DID find the answer by searching the forums within a few seconds.:p

---

### Post by Snark1994 on 2010-09-08
It's at the top, under "Thread tools".

And to disable the screensaver lock/change screensaver timer, go System -> Preferences -> Screensaver :D

Yeah, I've found the default help application to be less than enlightening in most cases. However, the web in general and this forum in particular have always managed to solve any problems I've encountered :)
[URL="http://ubuntuforums.org/showthread.php?t=1481764"]
[/URL]

---

### Post by captainiom on 2010-09-08
> **Snark1994 said:**
> It's at the top, under "Thread tools".
 
And to disable the screensaver lock/change screensaver timer, go System -> Preferences -> Screensaver :D
 
Yeah, I've found the default help application to be less than enlightening in most cases. However, the web in general and this forum in particular have always managed to solve any problems I've encountered :)
[URL="http://ubuntuforums.org/showthread.php?t=1481764"]
[/URL]
 
 
Thanks.

---

