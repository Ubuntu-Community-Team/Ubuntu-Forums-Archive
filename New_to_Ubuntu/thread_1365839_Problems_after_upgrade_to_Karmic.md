---
title: "Problems after upgrade to Karmic"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by blues2use on 2009-12-27
Running 2.6.31-16-generic and 2.6.31-15-generic...problems occur with either kernel...

About half the time (every other boot regardless of which kernel I choose), the desktop does not load the top and bottom panels. The boot process just stops...it doesn't freeze...if I CTRL/ALT/DEL to force a restart, I can see that the Loading Panels process is not complete and, no matter how long I wait, it just sits there...the desktop is populated as it should be but the panels never do load...

Second - I don't have a listing for Sound in System/Preferences/Sound...I do have an entry called Pulse Audio Preferences which is nothing like being able to make the choices with the applet that should be in there (it's worthless as far as I am concerned)...Sounds existed for several boots and then...

The desktop started to not boot to completion, there's no login sound, there's no Sound applet in System/Preferences...just wondering what the next step(s) might be to fix these errors. I had thought about removing Pulse and reinstalling -or- removing it and using ALSA. As for the panels not loading or the login sounds or System/Preferences problems, I have no idea what to do to fix them.

Your suggestions are most welcome

---

### Post by LuisGMarine on 2009-12-30
I'm not sure, but I had similar problem where panels wouldn't show up and the drivers to my nvidia card would flat out not work.  For me 9.10 on my laptop was an experience from hell.  4/5 times trying to install it it would hang with little information about what the problem could be.  

This might be an unconventional fix, but I would recommend downgrading to Jaunty (9.04) it's pretty darn good, and you still get a lot of the new packages coming out.  Like I said not the best fix, but trust me there are tons of people having problems with sound, I myself don't have the time to mess with it, so I just downgraded.

---

### Post by Tahakki on 2009-12-30
Hi - was this upgraded from a previous version through the Update Manager, or a complete wipe-and-reinstall?

---

### Post by LuisGMarine on 2009-12-30
Ah see that could be a problem.  I've read a few articles and listened to a few podcasts that a lot of users are complaining about the actual upgrade from 9.04 to 9.10 through update manager.  

If you are still keen on installing 9.10 I would do a wipe fresh install.  Can't go wrong with that.  If that *still* doesn't work I would just go back to 9.04 fresh install.

---

### Post by Buuntu on 2009-12-30
I had lots of little bugs like this when I upgraded to 9.10.  I eventually got fed up with it and ended up just backing up my home folder and re-installing.  This would mean you would have to re install all of your programs, but you can do this if you want to avoid installing everything all over again:
From your 9.10 partition (before wiping your partition) run:
```
sudo dpkg --get-selections > ~/packages
```That will make a list of all installed packages and store it in a file in your home folder called packages.

Then once you back up your home folder to your new 9.10 partition you can run:
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < ~/packages
sudo apt-get update && sudo apt-get upgrade
```Now you will have an exact copy of all your applications and your home folder in a working Karmic install.  Hope this helps.

P.S.
If you need help backing up your home folder, let me know - I can guide you through it.

---

### Post by blues2use on 2009-12-30
> **Buuntu said:**
> I had lots of little bugs like this when I upgraded to 9.10.  I eventually got fed up with it and ended up just backing up my home folder and re-installing.  This would mean you would have to re install all of your programs, but you can do this if you want to avoid installing everything all over again:
From your 9.10 partition (before wiping your partition) run:
```
sudo dpkg --get-selections > ~/packages
```That will make a list of all installed packages and store it in a file in your home folder called packages.

Then once you back up your home folder to your new 9.10 partition you can run:
```
sudo dpkg --clear-selections
sudo dpkg --set-selections < ~/packages
sudo apt-get update && sudo apt-get upgrade
```Now you will have an exact copy of all your applications and your home folder in a working Karmic install.  Hope this helps.

P.S.
If you need help backing up your home folder, let me know - I can guide you through it.

This was a fresh install of 9.10 after a buggy failed upgrade from 9.04. I'm considering a re-install of 9.04...9.10 is still giving me video problems, keyboard input is lagging for some reason, web pages ae sluggish to load and sometimes don't load at all (using Firefox, Chrome, Opera - doesn't matter)...

On the other hand, I had some video problems and never-ending sound problems with 9.04. I may just jump ship and try Mint 7 or another distro until ubuntu stabilizes a little more.

---

