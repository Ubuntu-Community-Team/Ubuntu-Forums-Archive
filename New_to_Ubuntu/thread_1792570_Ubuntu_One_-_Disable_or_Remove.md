---
title: "Ubuntu One - Disable or Remove"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by rs321 on 2011-06-28
Folks,

11.04 (32) was working beautifully until I installed an app that brought Ubuntu One with it, and now neither Firefox nor Banshee will work beyond getting to a white screen.  I have no doubt in my mind that Ubuntu One is a valuable and viable addition but I'm not ready for it yet so is there any way to remove it or at least disable it (temporarily or otherwise) until I learn the system well enough to use it?

-Randy

---

### Post by Frogs Hair on 2011-06-28
Ubuntu One is installed by default on 11.04 and can be removed from the software center . I don't know how Ubuntu One would affect the internet browser or music player.

---

### Post by coffeecat on 2011-06-28
Ubuntu One doesn't really do much at all until you set up an Ubuntu One account.

> **rs321 said:**
> 11.04 (32) was working beautifully until I installed an app that brought Ubuntu One with it, and now neither Firefox nor Banshee will work beyond getting to a white screen.

As Frogs Hair says, Ubuntu One is installed by default, so I don't undertsnd this bit. What was the app that apparently brought U1 with it? This might be the problem.

---

### Post by rs321 on 2011-06-28
Folks,

Sorry to take so long to get back but I went back to Ubuntu to check a few things.  The download was Stellarium, which I removed last night when the problem first occurred.  I just tried Janitor but that gave me only the white screen, as did System, unless you think giving them each a minimum of two minutes to open was being impatient.

So far as I can determine, nothing functions anymore since Ubuntu One became my "home page".  I want it relegated to the background if nothing else because when I tried to create an account, thinking that might help, that didn't work either.  The system worked flawlessly until Ubuntu One came to the forefront and I simply am not ready to deal with it yet.

-Randy

---

### Post by rs321 on 2011-06-28
Folks,

I have, since my last posting, tried everything on every menu I can find with all the same results:  Ubuntu One has frozen my system!

"Free Space" won't open
"Repair Broken Packages" says everything is just hunky dory
"Failsafe Graphics Mode" reboots the computer
"File System Check"  freezes
"Update Grub Bootloader" reboots the computer

I figured that since Ubuntu One is the only new addition since a flawless installation I'd go along with the program and create an account, but it stops where I need to enter the coded words and says they were entered wrong, and did so six times.  Granted those squiggly letters are sometimes confusing but not six times.

A re-installation is not an option:  I ran into this problem last time I installed it, which is why I installed it again.  Should I take this to an advanced forum?  I'm not going to give up but I'm sure getting scarce with options.

Does anybody have a clue?

-Randy

---

### Post by coffeecat on 2011-06-28
> **rs321 said:**
> I figured that since Ubuntu One is the only new addition since a flawless installation

But it's not a new addition. As Frogs Hair and I have already pointed out, the Ubuntu one client would already have been installed on your system from when you first set it up. And even if you had uninstalled it, I can't see how it could have been dragged in by stellarium. It is not listed as a Stellarium dependency.

I don't doubt that you are having a problem, but I cannot follow what this is beyond Firefox and Banshee giving you a white screen. By "white screen" do you mean just the app window or the whole monitor area? What do you mean by Ubuntu One becoming your "home page". Do you mean in Firefox? If not, what do you mean?

I think you had better explain exactly what happens from the time you login and why you think Ubuntu One is involved.

---

### Post by rs321 on 2011-06-28
coffeecat,

Thanks for the reply.  By saying Stellarium brought it in I guess I was wrong, but it did not become the page to which Ubuntu opened (my "home page") until such time as I downloaded it.  If my verbiage isn't exact I'm sorry but that's why I'm at the beginner's forum.  When I say white page what I mean is whatever I'm trying to open appears with its name up in the corner and absolutely nothing else is shown on the page.  If, in example, I open Banshee and insert an audio CD nothing happens.  I need to close Banshee then go to the audio player in apps and find the CD, at which point I can play one selection at a time manually.  Before Ubuntu One took control I could open Banshee and it would play just fine.  I could open Firefox and it would run.  I could open any of the apps and they would work swell but with Ubuntu One nothing functions.  It is a detriment to my system and I'd be tickled pink to be shed of it if only temporarily.

There must be a simple answer to this because nobody else seems to have had this problem but I've had the same problem with two different installations, which is why I think a re-install would be a waste of time.  I did figure out how to set up an account with Ubuntu One and got everything in sync, but I have a life away from a cell phone and I wouldn't give a nickle for the lack of maturity on Facebook so they are of no use to me.  If there is any other reason for having Ubuntu One I'd like to be told what it is, and lacking that I'd like to know how to get rid of it.

Thanks for the interest.

-Randy

---

### Post by Frogs Hair on 2011-06-28
Open the software center , go to installed software , select Ubuntu One and select remove . Ubuntu One is a service for online storage of music and files and only works if you have set up an account . You can change web browser home page in Firefox from preferences > general . Is it possible that another user changed settings on your computer ? I have no idea what Ubuntu One has to do with playing cds in Banshee .

---

### Post by rs321 on 2011-06-28
Frogs Hair,

Thanks for the tip but the "installed Software" folder is the same as every other folder in Ubuntu in that it won't do anything other than open a blank page with its name on the top.  Ubuntu has, unfortunately, become useless since Ubuntu One joined the party, which is why I want to remove it.

Is it possible to remove it from somewhere than Ubuntu itself?  I mean is there some root directory I might be able to access without actually opening Ubuntu One?  That's a long shot, I know, but I don't see any alternatives.  Should I go through the hassle of installing Ubuntu 10.xx over the top of 11.04 if that is even possible?

-Randy

---

### Post by rs321 on 2011-06-28
Frogs Hair,

I found a way to sneak into Ubuntu without activating Ubuntu One and was able to remove it as per your instructions.  Everything is once again up and functional, and I want to thank you very much for your interest and contribution.

-Randy

---

### Post by rs321 on 2011-06-28
Folks,

I spoke too soon.  I did two restarts and Ubuntu reverted back to where nothing works anymore unless I start in safe mode.  This really sucks!  I abhor using Windows and was really looking forward to using Ubuntu but it seems as though it is simply not meant to be.  I'll try a third installation of 11.04 (unless anybody has a better suggestion) and two days later I'll need to erase it and install something else, just like the last two times I've installed it.  This is getting really old really fast!

It would be nice if anybody was willing to give me any more advice first.

-Randy

---

### Post by travisHAZE on 2011-06-28
New to Ubuntu myself, but honestly I would just try a fresh install imo. Like they said, Ubuntu One is just a storage facility, it activates nothing on your system (which they repeated over and over and over)

Before the fresh install, you could try two commands

sudo apt-get remove [Stellawhatever]
Or
sudo apt-get autoremove (removes cache files is what I've been able to notice)

If they don't produce results, and nobody else has any ideas, try a fresh install =/

---

### Post by dFlyer on 2011-06-28
My first suggestion is if you have the original iso you downloaded, run md5sum to verify you have a good download. If so run the live desktop cd and open a terminal and run this command to make sure your hardware supports Unity.

/usr/lib/nux/unity_support_test -p

All your answers should be yes, otherwise you will have to run the classic desktop or work through issues to get your hardware configured correctly. I really don't think UbuntuOne is your problem as that is default installed and doesn't activate until you create an account.

Another suggestion is to log out of Unity and at the login screen click you name and than select classic ubuntu and login to see if you can navigate folders and web pages.

Being a new user mean there is a learning curve, so I recommend you go slow, have fun and ask questions by providing as much information about your hardware, software and error message as possible.

---

### Post by Zlatan on 2011-06-28
I'd suggest to use Ubuntu 10.04.2 LTS- it will be a bit older release but you should not miss anything there. More bugs fixed and support will be longer (Long Term Support release).

---

### Post by rs321 on 2011-06-28
Folks,

Thanks to all of you for your suggestions and support.  I should also apologize for my negative demeanor in my last post; I had been working on the problem for seven straight hours and must admit I was a bit fried but that's no reason to be negative.  I took a shower, watered my garden, and had a beer so I'm a bit refreshed and I'm ready to get back at it until it's time to make dinner for the visiting relatives.

I'll figure out where to run the suggested commands and if that doesn't fly I'll go with 10.04.2 LTS.

-Randy

---

