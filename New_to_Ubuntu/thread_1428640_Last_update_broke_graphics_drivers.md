---
title: "Last update broke graphics drivers?"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by Cleveland Rock on 2010-03-13
The last Linux update, whatever that was, seemed to screw something up. Suddenly, my screen goes black and freezes whenever I try to view a slideshow in Digikam, trying to enable OpenGL transitions in said slideshow gets me the error message "OpenGL support is not available on your system.", and trying to update my drivers fails. Specifically, to install the drivers from the NVIDIA website, I need to disable an X server or something, and the usual command to stop the X server doesn't work. Trying to install the drivers via PPA gets me an error about failing to download or something; sorry, I forget.

Whew. For now, mostly, I just want to get that slideshow feature working in Digikam. Also, if you can suggest what to do when my screen goes black and freezes other than restart the system, that may also help.

Thanks.

Edit: By "Linux update", I mean the one from 2.6.31-19 to 2.6.31-20, apparently.

---

### Post by halj32 on 2010-03-13
every time you update your kernel you will have to re install your graphic drivers etc.. to get round this problem install DKMS first it will recompile all your drivers when you update.
You can install dkms with synaptic

---

### Post by 3rdalbum on 2010-03-13
> **halj32 said:**
> every time you update your kernel you will have to re install your graphic drivers etc.. to get round this problem install DKMS first it will recompile all your drivers when you update.
You can install dkms with synaptic

DKMS is preinstalled, and it only rebuilds drivers that have registered themselves with the DKMS system.

The graphics drivers that you get from the repositories will automatically use DKMS, but the ones from Nvidia's website don't. You'd need to reinstall the driver every time you update the kernel, or use a PPA for the Nvidia drivers that will use DKMS.

---

### Post by Cleveland Rock on 2010-03-13
> **3rdalbum said:**
> You'd need to reinstall the driver every time you update the kernel, or use a PPA for the Nvidia drivers that will use DKMS.
When I use a PPA for the NVIDIA drivers and try to activate them via Hardware Drivers, I get the error message "SystemError: installArchives() failed".

Installing via the NVIDIA website requires that I stop the X server, and the usual command of "sudo /etc/init.d/gdm stop" doesn't work.

Thanks for the help so far.

---

### Post by Cleveland Rock on 2010-03-13
Bump.

---

### Post by Cleveland Rock on 2010-03-13
Please?

---

### Post by achase79 on 2010-03-13
> Installing via the NVIDIA website requires that I stop the X server, and the usual command of "sudo /etc/init.d/gdm stop" doesn't work.
do you go to a terminal shell (ctrl+alt+F1) to execute that stop command?  If you don't I believe it will be ignored

---

### Post by Cleveland Rock on 2010-03-13
> **achase79 said:**
> do you go to a terminal shell (ctrl+alt+F1) to execute that stop command?
Yes, except I used ctrl+alt+F2.

I could give you the exact error message that command gets me, but I wouldn't know how to get out of the terminal shell.

---

### Post by stoomaroo on 2010-03-14
Same issue here.

I am trying to roll through all the past changes in the last week.  I have an nvidia card with the 190.53 drivers.

With kernel changes I regularly dropped to the shell (CTRL+ALT+F1) and issued the ```
/etc/init.d/gdm stop
``` command to stop Gnome & proceed with the installation.

This seems to have recently changed, and I am now unable to do so.

I am being informed that:

```
** (gdm-binary:2525): WARNING **: Could not acquire name; bailing out

```

Will post back if I discover the problem.

-stoomaroo

---

### Post by Rayve on 2010-03-14
Every time I upgrade to a new kernel, I have to rebuild the Nvidia drivers.  I've downloaded 190.53 from nvidia's website, and these are the steps I go through:

When I first try to boot into the new kernel, it gives me an error about not having the graphics properly installed / running degraded, and I choose the final option which is to "Exit to console login".

From there, I log in like normal - username and password - and then switch to the directory to where I downloaded the drivers.

```
 cd Downloads 
```

Then I enter ```
 sudo sh /N
``` and I hit the tab key to autocomplete the Nvidia package name.  After the name of the file is there, I enter ".run" at the end which is the extension.

Then I press enter, and select "yes" to all the screens that come up with the Nvidia installer, including the x-config at the end.

Then once that is done, I'm back at the terminal, so I do ```
 sudo shutdown -r 0 now
``` to reboot and come back in the kernel, with Nvidia drivers all installed.

I got these steps from one of the threads on this forum, I'll see if I can't find the link.  But when I first did it, I was in the new kernel already, like some of you, so I had to press Ctrl + Alt + F1 to get to a console.  From there, I entered ```
 sudo /etc/init.d/gdm stop 
``` and it would give me an error about the wrong syntax or something, so I think then it was ```
 gdm stop 
``` or vice versa stop gdm but in any case, it went through with no troubles and I was able to continue from the steps above.

Hope this helps!

Edit: see the thread here [http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978)

---

### Post by stoomaroo on 2010-03-14
Rayve,

thanks for this -- but what we're saying is that the "gdm stop" no longer works.  For some reason we cannot bind to the display.

As root, or not...

-stoomaroo

---

### Post by Rayve on 2010-03-14
Hmm... I'm in the middle of something so I can't check right now, but I seem to recall getting that error as well, though I was still able to install the drivers.

If I get a chance before I go to work tonight, I'll try to check it out further.

---

### Post by Cleveland Rock on 2010-03-14
I was able to get "sudo /etc/init.d/gdm stop" to work this time, but I get this error three times during the installation:
```
ERROR: Unable to open '/usr/lib/nvidia/libglx.so.xserver-xorg-core' for reading
       (No such file or directory)
```

---

### Post by Rayve on 2010-03-15
Cleveland Rock,

Hopefully something here will help: [http://ubuntuforums.org/archive/index.php/t-1035873.html](http://ubuntuforums.org/archive/index.php/t-1035873.html)  particularly the 17th January post.

Or this one [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100807.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100807.0)  where it sounds like perhaps not all of the old nvidia drivers have been removed...?

Just a thought.  Hope it helps!

---

### Post by Cleveland Rock on 2010-03-15
> **Rayve said:**
> Cleveland Rock,

Hopefully something here will help: [http://ubuntuforums.org/archive/index.php/t-1035873.html](http://ubuntuforums.org/archive/index.php/t-1035873.html)  particularly the 17th January post.

Or this one [http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100807.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3100807.0)  where it sounds like perhaps not all of the old nvidia drivers have been removed...?

Just a thought.  Hope it helps!
I'm not sure I did everything correctly, but nothing's different…

---

### Post by Rayve on 2010-03-15
This isn't an error you can just "hit enter through" and bypass?  I don't remember getting that particular error, but that seems the gist of some of what I read last night.

Alternatively, have you removed all previous drivers?

Good luck!

---

### Post by Cleveland Rock on 2010-03-16
> **Rayve said:**
> This isn't an error you can just "hit enter through" and bypass?
It is, but it doesn't show up in "Hardware Drivers" afterwards.

> **Rayve said:**
> Alternatively, have you removed all previous drivers?
I don't know how. That second thread lost me.

---

### Post by Rayve on 2010-03-16
> but it doesn't show up in "Hardware Drivers" afterwards.

It won't, because you didn't install it through that way (I think, anyway).  The 190.53 is sort of a beta, I believe, and not available through the hardware driver section, hence the "downloading right from nvidia and compiling yourself" deal.

If you've gotten through the installation errors and been able to say "yes" to the final "do you want to edit x-org config" question or similar that the nvidia setup asks, then you should be good to go.

[copied from that second link I posted, here are the steps it will ask -
   a. Accept the license
   b. Remove prior driver? = Y
   c. Download a kernel interface? = Y
   d. Compile a kernel interface? = OK
   e. Install Nvidia's 32-bit compatibility OpenGL libraries? = Y
   f. Run the nvidia-xconfig utility? = N  (if you already have a good xorg.conf -- Y if not)

I always say "y" to the xconfig question because so far I've been installing on an updated kernel.]

When I go to System > Preferences > Display, I get a pop-up asking me to use my vendor's display tools, which I Accept.  I can then see Nvidia's X Server Settings window and I see my video cards (as well as the integrated one on my motherboard since it is also nvidia).

If you can get here, I think it means your video cards are all set up and installed and ready to go!

However...

> I don't know how. That second thread lost me.

Sorry about that!  If you still feel you need to do so:

Entering ```
 sudo rm -rf nvidia* 
``` at a command prompt will remove anything that begins with "nvidia" (in your current directory, so make sure you want it removed from / or /home or whatever directory you are in).  You will not see confirmation of each file unless you remove "f" from and add "i" to the options, like so: ```
 sudo rm -ri nvidia* 
```.  I have no idea how many files it will actually delete, so be ready to confirm "yes" a bunch if you do interactively (the "i" flag).

The other steps in the post are if you have restricted drivers / older drivers installed.  If I understand correctly, ```
 sudo apt-get update && sudo apt-get install linux-headers-`uname -r` build-essential 
``` is having you make sure your headers are current for your kernel.  You may try this if you are still having troubles.

Hopefully some of this helps - if anything is unclear let me know.  I'm off to bed now, but I'll check back before work again.

---

### Post by Calash on 2010-03-16
I have the same issue with every Kernel update as well. Here is how I fix it.



- When it boots, change to a terminal (CTRL-ALT-F1)
- Login
- ps -e - Search for the X process
- sudo kill xxxx - number from the previous step
(Since 9.10 I have never been able to stop the Xserver by issuing a stop command.  It yells that I should try a different way that does not work.  If you can stop GDM, that is the better way to do this)
- sudo sh ./NVIDIA-XXXXXX -f --update - XXXX is the name of the downloaded driver.  -f will force the install and --update downloads the latest drivers first.


Lately I have had to use the -f or the drivers exit out saying I already have the latest version installed.  --update is just so I make sure I am up to date with them..you can probably skip it if you need to.

---

### Post by Cleveland Rock on 2010-03-16
Oh, duh. I thought it would show up in "Hardware Drivers". Sorry about that.

The slideshow program I mentioned in the first post works now, so I guess everything is fine. Thank you so much!

---

