---
title: "can't get age of empires II to run right on wine"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by outskut on 2011-03-07
Hey, I've used wine to run a couple programs before, though I think I actually had problems both times.  There must be something I just don't know to do.

I'm trying to install one of my favorite games, Age of Empires II using Wine on Ubuntu 10.04.  I have Wine version 1.2.2, and a fully up to date (I think) version of 10.04 LTS.

I remember that the .exe files wine used had to be set to be executable (is this just the "chmod +x" command for regular Ubuntu?), so I set the aoesetup.exe to that and ran it using Wine.  It went through the entire graphic installation wizard and said that it installed everything correctly - Microsoft Games AoK was added to the program files list in the Wine menu in applications.  I also checked the permissions (executable flag) on all the .exe files in the program directory, they had already been set.

When I try to start up the program though it immediately pops up with this message:
"The program empires2.exe has encountered a serious problem and needs to close.  We are sorry for the inconvenience.
This can be caused by a problem in the program or a deficiency in Wine.  You may want to check [http://appdb.winehq.org](http://appdb.winehq.org) for tips about running this application.
If this problem is not present under Windows and has not been reported yet, you can report it at http://bugs.winehq.org."

I'm pretty sure it's not a problem with Wine because all it says at that site and everywhere else I go is that AoK works just fine with Wine.  I'm pretty sure it's something dumb I'm not doing.  Can someone tell me what I'm missing?  I'd really appreciate it.

---

### Post by 3177 on 2011-03-07
there no reason for your problem, try re-installing.

---

### Post by 3177 on 2011-03-07
I have downloaded and installed AOE2.
Works fine for me in 1.2.2

---

### Post by outskut on 2011-03-07
it might make a difference that I couldn't originally select the setup.exe program on my cd drive since I couldn't set the file flag to executable, so I had to copy the content of the cd to a folder and install it from there, but I just found the option to "install from cd-rom or floppy" in the wine - uninstall wine software tab, so I'm trying that out... 'let you know in a minute

...no, I still have the exact same problem.

---

### Post by outskut on 2011-03-07
hm, well is your environment the same?  I just installed wine using Synaptic, so I suppose it should be up to date, but did you need to configure it at all, or install drivers for Wine to run correctly in the first place?

I just installed a clean copy of it.

---

### Post by 3177 on 2011-03-07
So how I installed is.
*copied to desktop.
*right clicked on setup.exe
*clicked on wine program loader.
* ran, said installed.
*Cilicked on Accesories>Wine>AgeOfEmires>AgeOfEmpires.exe

---

### Post by 3177 on 2011-03-07
> **outskut said:**
> hm, well is your environment the same?  I just installed wine using Synaptic, so I suppose it should be up to date, but did you need to configure it at all, or install drivers for Wine to run correctly in the first place?

I just installed a clean copy of it.

keep in mind, even  a clean copy is 1.2.2 which is a beta.

---

### Post by outskut on 2011-03-07
okay, that's an interesting point, I'll try downgrading to a more stable release and trying it again.

it actually sounds like your version is a bit different than mine, since my Wine installed a menu directly in the applications menu.  then to play it was applications > wine > Programs > Microsoft Games > Age of Empires II > Age of Empires II (the program this time)

anyway, I'll find a stable release and update this post again.  Thanks for your reference, it's really helpful.

---

### Post by 3177 on 2011-03-07
> **outskut said:**
> okay, that's an interesting point, I'll try downgrading to a more stable release and trying it again.

it actually sounds like your version is a bit different than mine, since my Wine installed a menu directly in the applications menu.  then to play it was applications > wine > Programs > Microsoft Games > Age of Empires II > Age of Empires II (the program this time)

anyway, I'll find a stable release and update this post again.  Thanks for your reference, it's really helpful.

???
wierd.

---

### Post by outskut on 2011-03-07
I feel like I'm getting somewhere so I thought I'd document the steps I'd taken in setting up Wine:

- I downloaded Wine version 1.2 from the following link ([http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2.tar.bz2](http://ibiblio.org/pub/linux/system/emulators/wine/wine-1.2.tar.bz2))
- Then I tried to compile (I went to my downloads folder, expanded out the wine-1.2.tar.bz2 archive, navigated to it with the terminal, and executed: ./configure)
  The ./configure returned a couple packages that it said were missing, and so I installed each of them - "sudo apt-get install bison", "sudo apt-get install..." the other thing I can't remember.  This ended up with a cryptic message telling me that my X-development environment wasn't found and that I'd probably want that, but that wine would install just fine without it.
- So I ran the command:
"sudo apt-get build-dep wine"
(According to happyhamster's post at the following url: [http://ubuntuforums.org/archive/index.php/t-712028.html](http://ubuntuforums.org/archive/index.php/t-712028.html))
- Since it finished without any particular errors as far as I could see, I executed:
"make && sudo make install"

And now I'm waiting for that installation to complete.  It's taking an amazingly long time to install so I'm going to bed, and I'll update again when I've had a chance to see if it worked.

---

### Post by Anuovis on 2011-03-07
You might try installing and running it through this app: [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)
It is more like a configuration tool for Wine and has a template for AoE II. You'd have to reinstall though.

Also, from my own experience, Wine sometimes have problems with resolutions, especially if have a widescreen (other than 3:4) monitor. Emulating a Windows desktop vs. running full-screen might also make the difference. Try setting virtual desktop at the resolution the game is supposed to launch in.

Updating Wine to the latest version probably wouldn't hurt either.

Wine is a bit of trial and error every time, might be worth spending some time tinkering around if you really want a particular app. Good luck.

*EDIT:* If you are still having troubles with permissions, go to *Configure Wine*, *Drives* tab and add a CD-ROM drive there. Point it to the folder (via *Show Advanced* settings) where you mount the actual CD or .iso image. That way Wine will treat that folder as if it was a Windows CD-ROM drive and will allow you to launch all sorts of .exe files from that place.

After installation, however, it is sometimes necessary to go to the virtual C:\ drive and set permissions to "read/write" and "run files as executables" for the whole folder. Otherwise, you might have troubles running the software or saving games.

---

### Post by outskut on 2011-03-07
So no, the result is that I can't get AoK up and running.

I've tried the typical apt-get installation - installs wine 1.2.2, the synaptic installation of both 1.2.2 and 1.0, and installation by source of wine 1.2.  Each time I tried reinstalling AoK several times to make sure I wiped the system sufficiently of it (although, I'm not convinced I managed to perfectly every time).

I'll just see how it runs on VMware/VirtualBox.  Last time I tried it though, I think VirtualBox had a resizing issue.  Anyway, thanks for your help, and I'll stay subscribed to this thread in case anyone has another idea for me to try.

...wait, I didn't see Anouvis's suggestion until just now.  I'll try that out.

So PlayOnLinux installed wine version 1.2.1 and attempted to install AoE2.  I tried installing it from CD as well as from my folder, and I encountered a strange error where the installer couldn't read a host of .TTF font images, but after ignoring the error it finished the installation and failed to start up the game with the exact same error message.  Thanks for the suggestion though.  Ah, but then the wizard recognized that I needed microsoft fonts installed and did that for me - and asked me to install
$sudo apt-get install mesa-utils
That was nice of it, same problem though.

---

### Post by becatron on 2011-04-13
I am having the exact same issue, please let me know if you have managed to solve this.

---

### Post by eamonn98 on 2011-04-14
I actually registered just to respond to this. I haven't tested it on Ubuntu however on OS X and Crossover Games I'm having the same problem as per described here. I'm trying to search for a fix and when I do find one I'll post here immediately.

---

### Post by becatron on 2011-04-14
Did it work on your virtual box? That's my next step....

---

