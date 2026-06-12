---
title: "A few questions from a beginner..."
date: 2009-07-18
forum: New to Ubuntu
---

### Post by mattshiloh on 2009-07-18
First I would like to say hello.  I am a Ubuntu neophyte, as I have just recently installed it on my portable and decided to use it as my primary day to day, as I felt it was time for me to learn Linux.

I have run into a few problems thus far and wondered if anyone had any ideas or solutions to these that I might learn from:

A) I am wanting to get this Compiz I keep hearing everyone talking about working on my system to I can do the 3D Alt+Tab thing.  It looks cool and I admit I do like aesthetics as much as the next person.  I am not sure how to go about this however, as it appears I have everything installed dealing with Compiz according to Synaptic, but perhaps not.

B) I am getting this VERY annoying loud beep when I shut my computer down.  I have already disabled the error beep which I found equally annoying, but this one is the only real nusiance I have, especially when shutting down at night and not trying to wake my roommate.

C) I tried installing this Virtual World Simulator called Second Life on my portable as I have a friend who does her music in SL and I like to go to listen to her.  I am not really wanting to switch over to my Windows HDD several times a week just to do this, so I installed the Linux port of SL on my machine and attempted to run it.  Doing so however corrupted my video driver and I was unable to fix the issue through the boot up recovery options, which necessitated a reinstall of Ubuntu from scratch.  This is not a desired action again.  I have an ATI Radeon Mobility Card in my Dell Inspiron 1501 that I am working with.  I believe the model is X1150.  Does anyone have any advice on this, as if I try it again, it is a one shot attempt incase it screws my driver up again, due to not being able to see anything on reboot (does a scrambled screen like a bad video card).

Thank you in advance, and I hope I have not annoyed anyone too much with my noobish questions.  I am a techie in the Windows world, but Linux is something new to me and I am trying to learn slowly.

---

### Post by doas777 on 2009-07-18
A) Rclick the desktop, and select "Change Desktop Background". go to the rightmost tab "Visual Effects", and check which radio button is selected. if it's off, try turning it on, or to extra. if you can enable either of those, then you have a good vid card driver installed and are capable of running 3d accelerated applications. the easiest way to see if compiz is going, is to select "Extra" under visual effects, and then try to move the window. if it jiggles like jello, then you've won.

I haven't found anwers to B that i am satisfied with (almost all involve completely disabling the speaker in the kernel) but if you search, you will find the answers.

never tried second life. you may be able to run the win version over wine:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=4619&iTestingId=16751](http://appdb.winehq.org/objectManager.php?sClass=version&iId=4619&iTestingId=16751)
it's only silver rated though, so it'll run, but will prolly crash somewhere or lack a feature.

---

### Post by LewRockwell on 2009-07-18
Killing The Beep...

These guys gave it a work-out...

[http://ubuntuforums.org/showthread.php?t=977018](http://ubuntuforums.org/showthread.php?t=977018)

.

---

### Post by T-Train on 2009-07-18
To configure the Compiz settings go into System > Preferences > CompizConfig Settings Manager.

---

### Post by bug67 on 2009-07-18
> **mattshiloh said:**
> "...I am wanting to get this Compiz I keep hearing everyone talking about working on my system to I can do the 3D Alt+Tab thing.  It looks cool and I admit I do like aesthetics as much as the next person.  I am not sure how to go about this however, as it appears I have everything installed dealing with Compiz according to Synaptic, but perhaps not..."

In the upper left hand of the top panel:

Applications > Add/Remove... > In the search box type in "compiz"

The very first hit should be something called, "Advanced Desktop Effects Settings (ccsm)."

Check the check box and click Apply Changes.

After it's installed go to:

System > Preferences > CompizConfig Settings Manager.

Happy tweeking!  :D

---

### Post by pme 72 on 2009-07-19
Not particularly technically experienced with Linux or Windows but Second Life would just run for me with my ATI x1550 on my desktop with Hardy Heron 8.04 and the proprietary drivers. It would not open for me with Jaunty and the available open source drivers for my x1550. There may be tweaks a more technically savy person could recommend for the open source driver that might help. You could pose the question again to the Ubuntu Video and/or Gamers forums. You might have more luck with Hardy or Intrepid Ibex 8.10. I think both will offer you the option to install the proprietary fglrx driver for your video card. 

Also I just saw a link to linuX-gamers.net mentioned in Ubuntu User Magazine:"with tips for Wine/Xorg configuration for various games". No experience with that link though.

---

### Post by mattshiloh on 2009-07-21
I have managed to get Compiz installed correctly thanks to the wonderful advice listed here.  Unfortunately, my ATI card driver does not like the 3D aspect of it when I try to use the "cube" look, and immediately locked up when pressing Cntrl+Alt+Arrow.  I am hoping to find a better driver for my card, as I know my card is capable of handling 3D, but this is just aesthetics, so I am not overly concearned about it.

I have not yet attempted to fix the beep with the link provided by Lew, but I will take a look at that this afternoon after work.  I got slammed busy over the weekend which prohibited me working on much at all.

Doaz and PME, thank you for the responses on SL. I am hoping to find a viable alternative for this with the current version of Jaunty, as I do not relish the thought of reinstalling Ubuntu yet again until I have managed to get an image made, and even then I am not sure if I want to back up to a previous version yet or not.  I have installed Wine, but am curious if I need to install Windows ontop of Wine or whether Wine will just run Windows apps.

I think I might end up reformating and dual booting however to provide an alternative for this, as well as to try something a friend of mine talked about in that I can create a shared folder between Linux and Windows to drop files into incase I need to attempt recovery of the Linux side.  Does anyone have any thoughts on this?  Is dual booting a good way to go, or are there some cons to this?

---

### Post by snakeman21 on 2009-07-21
No, you don't install windows on Wine.  Wine simply runs some windows applications natively.  Unfortunately, it doesn't work for everything, and I doubt it will run the windows version of second life.  Couldn't hurt to try, though.  Good luck!

To use Wine, right-click on the .exe file and verify that the first option is "Open with Wine Windows Program Loader" and click it.  A window will come up that looks like a regular windows app.  Install the program as you would on a windows system, then find it under Applications > Wine > YourProgramName

---

### Post by Paddy Landau on 2009-07-21
> **mattshiloh said:**
> I have installed Wine, but am curious if I need to install Windows ontop of Wine or whether Wine will just run Windows apps.
Wine is a Windows API, in other words it allows Windows programs to run on Linux. It is neither a Windows emulator nor a virtual box.

Some programs work well under Wine, some work with problems, and some don't work at all. I believe that SL is one of those that won't work under Wine.

If your computer is powerful enough (and it will need to be powerful), you can run a virtual Windows machine inside Linux and run SL in it.

I'm guessing here: I suspect that your problems with SL are because your video card is designed specifically for Windows. I could be wrong on that, though.

By the way, if you want to use Wine, I strongly recommend that you install [PlayOnLinux]("http://www.playonlinux.com/") and use that. It's a sort-of Wine manager that makes it easy to install, run and uninstall Windows programs on Wine.

> **mattshiloh said:**
> I think I might end up reformating and dual booting...
Great idea. I dual-boot my computer for the one program I need that doesn't work on Linux or Wine.

> **mattshiloh said:**
> I can create a shared folder between Linux and Windows to drop files into
There's an easier way. Ubuntu will easily see your Windows partition. It's built in. If you install [Ext2Fsd]("http://ext2fsd.sourceforge.net/projects/projects.htm#ext2fsd") on Windows, then your Windows will easily see your Ubuntu partition. Therefore, all your files automatically will be shared. (Warning: Ext2Fsd is not yet compatible with ext4.)

Just be sure to do your usual backups, and you will be fine.

---

### Post by snakeman21 on 2009-07-21
I'm going to jump in and say that yes, everything the person above me said is true, but there is a downside to dual booting, especially if you'll be sharing files.  Ubuntu isn't compatible with 99.99% of viruses, but if you download a file with ubuntu and then share it with Windows, you may have problems.  My suggestion is to install a Linux virus detector and scan your files before giving them to the windows side.  You'll save yourself a lot of hassle that way.

---

### Post by SunnyRabbiera on 2009-07-21
as for graphics cards ATI has crap support for linux, so if you cant get it working dont blame linux, blame ATI/AMD

---

### Post by devildoc5 on 2009-07-21
A good place to try and get some advice for ANY windows program you are thinking about trying out on linux (or any other OS for that matter) is [http://appdb.winehq.org/](http://appdb.winehq.org/)   this it the AppDB at WineHQ.

That has almost every program anyone has thought about running in Wine, as well as how to handle common problems and special work arounds.

---

### Post by 3rdalbum on 2009-07-21
> **mattshiloh said:**
> I have managed to get Compiz installed correctly thanks to the wonderful advice listed here.  Unfortunately, my ATI card driver does not like the 3D aspect of it when I try to use the "cube" look, and immediately locked up when pressing Cntrl+Alt+Arrow.  I am hoping to find a better driver for my card, as I know my card is capable of handling 3D, but this is just aesthetics, so I am not overly concearned about it.

I'm glad - the X1150 is not supported by the ATI proprietary driver, so the open-source driver is your only option for acceleration. Or you could go back to Intrepid (Ubuntu 8.10) and use an old version of the ATI driver that supports your card.

Alternatively, you can get the latest development version of the open-source driver, but I can't guarantee that it will improve things, and I can't guarantee that you won't possibly spoil things.

---

