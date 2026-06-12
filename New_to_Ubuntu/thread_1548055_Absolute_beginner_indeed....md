---
title: "Absolute beginner indeed..."
date: 2010-08-07
forum: New to Ubuntu
---

### Post by Jedcurtis on 2010-08-07
[LEFT]:KS **First off, thanks for the help, past, present, and future.  This community thing is AWESOME!!!** :KS
[/LEFT]

OK, thought I had it solved, but alas I guess not.

When downloading a particular file or document from the web, it of course wants to know what to do with it.  When I tell it to choose what to use when opening that particular type of file, all I get is a folder list of all the files and folders on the computer.  i.e. the file explorer dolphin opens and shows me the view of everything in my home folder.  This would be terrific if I knew where things like gedit or transmission or openoffice's executable's were located amongst all of the CLUTTER!!!
:popcorn:
Don't get me wrong, forget Windows.  That has been a 25 year long nightmare.  Ubuntu seems exceptionally well built and designed and for the most part does all I need it to do.

Just please tell me it installs all the applications like the above mentioned to a centralized place on the hard-drive.  If not I may rethink my Ubuntu decision.

Where is everything????? gettin' confused....
Jed

---

### Post by GregBrannon on 2010-08-07
I can't tell you where EVERYTHING is on your computer, but MOST programs you'd want to use to open a file are going to be in the path.  Instead of actually having to locate the program you want to use in the file structure, you can simply type the name of the program in the field provided.  For example, if you want to open the file with gedit, you simply type gedit in that editable box and hit OK (or whatever it is in that dialogue).

Hope that helps.

---

### Post by Jedcurtis on 2010-08-07
Actually, thanks for the quick response.  No I've tried that to no avail.  i.e. the torrent program Transmission.  I've typed it in where your saying and it does nothing.  When I save the file to the HD then browse to it right click on it and select either 'open with' or from there I can click on Transmission.  However, the next time attempting to download a torrent file, I have to go through that whole thing again.  Arhg!!!  There has to be a permanent way to "Associate" a particular program/application to a particular file type.  That is what I'm looking for here.  That's why I was wondering where the programs on my drive typically get installed to.  I'm a noob to GNU/Linux/Ubuntu.  Not a noob totally though. 25 plus years spent in the industry.  Ergo some of this is getting kinda frustrating!  I should just know some of this right?  Also, (as if that weren't enough) what is the equivalent of a linux executable?  As in windows, the .exe, or .com, etc etc etc...

---

### Post by qyot27 on 2010-08-07
> **Jedcurtis said:**
> Also, (as if that weren't enough) what is the equivalent of a linux executable?  As in windows, the .exe, or .com, etc etc etc...
Executables on Linux don't typically have a file extension comparable to .exe, as file extensions aren't used in nearly as much frequency as they are on Windows (text files don't need them either, and their use on text files is generally a matter of the user putting them in there when naming the file).

Instead, you have the *format* of the executable, the real way the executable is packed and organized so that it can run.  Windows' .exe files are in Portable Executable (PE) format, OS X uses Mach-O format, and Linux distros typically use Executable and Linkable Format (ELF).  The system can recognize these types of applications without a file extension being present, and treats them as executable if the right permissions flag is set on them (said same flag can also be set on shell scripts, and then said scripts can be used just like normal programs can be).  *However*, if the applications/scripts/etc. are not somewhere on the PATH, then the user must use ./ preceding the name of the program in order to run it - this is for security reasons.




With the association stuff, what happens when you double-click on the torrent file normally?  I would think Transmission is already set as the default BitTorrent client and should come up when you double-click the .torrent.  That's certainly easier than having to right-click all the time.  Otherwise I seem to remember there being a 'Make default program' or something similar on the usual Open With dialog where you can select Transmission from the list.

---

### Post by corrytonapple on 2010-08-07
This may be a simple solution that you have tried but..............
If these files all have the same extension, go to where you downloaded them, say Downloads, and right click on it. Then go to Properties. Click the tab "Open With" and select the program from the list. For now on it should open files with that extension with that program.

---

### Post by Jedcurtis on 2010-08-08
> **qyot27 said:**
> With the association stuff, what happens when you double-click on the torrent file normally?  I would think Transmission is already set as the default BitTorrent client and should come up when you double-click the .torrent.  That's certainly easier than having to right-click all the time.  Otherwise I seem to remember there being a 'Make default program' or something similar on the usual Open With dialog where you can select Transmission from the list.

Absolutely Transmission starts when double clicked on from a saved state.  Just figured out I was having some issues with old KDE stuff laying around.  (It kept trying to load KTorrent)  Un-installed and all is well.  I will be sticking with Gnome.  The KDE stuff was still trying to load even though I've been back to using Gnome for a while.  Anyway KDE totally gone.  Situation seems resolved.

Thanks for the informative help about the extension stuff.  Very informative...

Also thanks to Corrytonapple.

---

### Post by linux18 on 2010-08-08
you might have some broken packages if your system is confusing uninstalled and installed packages, that can be dangerous try these commands to fix broken packages
```
 sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center && sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade 
 
```

---

### Post by corrytonapple on 2010-08-08
> **Jedcurtis said:**
> Absolutely Transmission starts when double clicked on from a saved state.  Just figured out I was having some issues with old KDE stuff laying around.  (It kept trying to load KTorrent)  Un-installed and all is well.  I will be sticking with Gnome.  The KDE stuff was still trying to load even though I've been back to using Gnome for a while.  Anyway KDE totally gone.  Situation seems resolved.

Thanks for the informative help about the extension stuff.  Very informative...

Also thanks to Corrytonapple.
You are welcome. ;) Be sure to mark your thread as solved in thread tools at the top of the page.

---

### Post by Jedcurtis on 2010-08-08
> **linux18 said:**
> you might have some broken packages if your system is confusing uninstalled and installed packages, that can be dangerous try these commands to fix broken packages


Thanks much!  Ran the advised commands and it took care of a few things.  Lots to learn.  Obviously eh?  Been 10 years since the last Linux workout.  It sure has came a long way.  That goes for the community as well...

---

### Post by linux18 on 2010-08-08
were happy to help, thinking back ten years ago, linux forums had very "if you don't know how to do this, go back to windows" attitude. I think linux has matured much faster than any other OS in the last 10 years and will advance farther than windows/mac in everything they are still ahead on (new hardware support, new codec support, etc.)

---

