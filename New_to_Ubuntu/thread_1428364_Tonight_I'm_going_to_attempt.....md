---
title: "Tonight I'm going to attempt...."
date: 2010-03-12
forum: New to Ubuntu
---

### Post by WhyIsLinuxSoCruel on 2010-03-12
to get two Ubuntu 9.10, aka Karmic Koala, boxes actually talking to one another on my home, wired ethernet network.  I'm hoping the communication will take place in both directions from machine A with its unigue IP address to machine B which will also have  its unique IP address.

And, because I'm a daredevil, and feeling like taunting the gods, I think I'd like to try to do more than ping one machine from another.  Please don't try to stop me!  Ping has served me and my two koalas well over the last few minutes, but I feel it's no longer doing all I need.  I'm a cruel, heartless, and demanding user, I know.

I know that telnet'ing between machines is far too complex.  I dared to try that one time using something very simple looking like telnetd, but it was a trap!  I learned my lesson that telnet'ing between machines is best left to a doctoral thesis, perhaps in Beijing or Bangalore.

In plain English, what I'd like to do is perhaps copy a file from one machine to the other, and then verify that the file was not corrupted in the process.  Because I'm a thrill seeker, I might even try copying that very same file back to the originating machine.  I'm not sure if I want to commit to taking it that far yet, but the thought crossed my mind.

Current tools at my disposal are the cp command and the md5sum tool.  I fear they will not be enough.  I've heard talk from those who have been over the horizon that there is a mysterious force out there known as a "file transfer protocol" but I fear that it, like telnet, may be simply too powerful to implement for mere humans in the land of Karmic Koalas.  I've heard that daemons may be needed.  Could be like opening Pandora's box.

What I'd like to know is, has what I envision attempting ever happened before on Earth?  If so, has it been reproduced?  If so, and anyone out there knows how I might best accomplish this task, I would appreciate any clues.

I'm probably asking too much, but, for some strange reason, it seems that two Koalas on the same network aren't all that useful if all they can do is ping each other.

Many thanks in advance to any people who may offer insight into how this is accomplished.  If successful, I promise not to soar too close to the sun like the son of Icarus.  I will be content merely to transfer some files across some cat-6 cable without introducing errors.

I anticipate this will occupy my time between 7PM and 3AM CST regardless of the outcome, but I fear not, for I am determined.  I will be sure to keep this thread updated with my trials and tribulations.  For now, though, I must rest in anticipation of my quest tonight.

Best wishes...

---

### Post by albert s on 2010-03-12
the simpliest way, for a noob like me anyway,
is to create a folder on the desktop, then right click it and make it shared.
you can then drag and drop any other file you want to into this folder and share it with any other machine on the network.
you may be asked to instal nautilus or something else to allow this, its fine, just click automatically allow.






EDIT dont know the difference between a file and a folder.

---

### Post by lisati on 2010-03-12
Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Don't worry too much that it mentions Windows, much of it will happily work if there aren't any Windows machines connected.

---

### Post by WhyIsLinuxSoCruel on 2010-03-12
> **albert s said:**
> the simpliest way, for a noob like me anyway,
is to create a folder on the desktop, then right click it and make it shared.
you can then drag and drop any other file you want to into this folder and share it with any other machine on the network.
you may be asked to instal nautilus or something else to allow this, its fine, just click automatically allow.


EDIT dont know the difference between a file and a folder.

OK, cool.  Thanks for that.  I'm more of a command line guy, but I'll definitely give your gui version a whirl to see haow it goes.  If the gui version works, then I ought to be able to copy files between machines via the command line (famous last words sometimes, though).

As for file vs. folder.  A file is a, well, file, like a text doc or a word doc or a saved game file.  A folder, also known as a directory (which I prefer) contains (or holds) files or other folders.  A folder is kinda like a drawer in a filing cabinet.  If it doesn't have any files in it, it's not very useful (Unless there's another drawer inside of it which does contain files).  HTH

Thanks!!

---

### Post by WhyIsLinuxSoCruel on 2010-03-12
> **lisati said:**
> Have a look here: [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

Don't worry too much that it mentions Windows, much of it will happily work if there aren't any Windows machines connected.

Great!  I'll be sure to have a look.  What I'm attempting certainly isn't rocket science, but I've found that sometimes the simplest things can be the hardest to find docs on because everyone seems to assume that of course everyone else knows how to do such a simple task.

What I don't like is stuff like when telnetd is there and appears to install and function fine (albeit with errors), and you find out 6 hours later that it's been superceded by:

xyz.123-UltraCoolNewTelnetd.ReallyDoesNothingNew.abc.kjsafsdjfg-v143543454.67

And, as for the one guy I saw elsewhere who said: 
"OMFG!!!  Don't use telnet!!eleventy!!  Your machine will get PWNED!!!!!  You gotta use SSH!!!!!!!"

I say:

"Chill out, Chet.  I'm on my own network that is isolated from the internet on test machines whose data I don't give two craps about.  I can always play with telnet, and uninstall it later."

Many thanks again!

Rick

---

### Post by Easy Limits on 2010-03-12
Moving files between two Ubuntu machines over a network is very easy with Giver.  Check your Ubuntu Software Center.

---

### Post by uRock on 2010-03-16
I use Samba, it works great.

---

