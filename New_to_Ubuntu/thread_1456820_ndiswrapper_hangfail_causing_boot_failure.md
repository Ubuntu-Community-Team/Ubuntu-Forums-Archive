---
title: "ndiswrapper hang/fail causing boot failure"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by solutionorppt on 2010-04-17
I am trying to install the drivers for a Belkin wireless USB dongle through ndiswrapper.

First I installed the common, util-1.9 and ndisqtk packages.

Next I blacklisted b43 and ssb in /etc/modprobe.d/blacklist.conf and rebooted;
lsmod returned no active wireless driver modules

I copied the XP driver's .inf and .sys files into a folder I created called /drivers and used the System>Admin>Windows wireless drivers interface to select the files.  When I selected the .inf file, the application responded with the following:

"WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release."

and proceeded to hang; I could not close it or terminate it manually in the system monitor.  Upon rebooting, Ubuntu will not load and is stuck on the load screen with 'Ubuntu' centered with the glowing bar beneath it.

I just installed 9.10 on the machine (a Dell w/Pentium 4) last night, so reinstalling it is not much of an issue to me, but I would really like to know where I went wrong here.

---

### Post by anewguy on 2010-04-17
First off, we can ignore the warning from the modprobe for conf files for ndiswrapper.  What we need to do foremost is get you running, then we can install your wireless driver.

When you boot you hopefully get a grub menu.  On that menu select the option for recovery mode.  When that does it's thing a little menu will come up - select drop to root shell.

do the following:

(1) type:

ndiswrapper -l <press enter> where "l" is a lower case "L" for list.

(2) if anything is returned in (1) do the following:

ndiswrapper -e xxxx <press enter> where xxxx is the driver name returned in the list from (1)

Repeat (1) and (2) until (1) doesn't return anything.

(3) type:

cat /etc/modules <press enter>

If ndiswrapper shows in that list:

nano /etc/modules <press enter>  This will call up an editor with the /etc/modules file opened.  Go to the line that says ndiswrapper and delete it, save the file and exit.  BTW - the command menu on the bottom of the editor shows "^" followed by something - this means to hold down the Ctrl key and press the key following the "^".

(4) Reboot - hopefully your system will come up.

Post back with what ever the results are. If the system doesn't come up we'll do some more work, but if it does come up we'll work on loading your wireless driver.

Dave ;)

---

### Post by solutionorppt on 2010-04-18
Booted, but the thing is now running like molasses in January... oh, wait, it's a Dell from 2004.

Anyway, I'm in a normal boot and can go ahead with installing drivers, but I'm still not sure where I went wrong the first time.

---

### Post by Bucky Ball on 2010-04-18
Plug in an ethernet cable (if you haven't already), get online, then plug in the Belkin. See what happens. It may get picked up and you will then be offered restricted drivers and firmware if necessary.

---

### Post by solutionorppt on 2010-04-18
Buckminsterfullerene-

That's not really a feasible option right now... I've been putting drivers on USB flash sticks because running them up + down the stairs is actually less work than moving my modem and router or the PC itself at the moment. My house is fairly heavily networked - we have 3 desktops and 2 notebooks, and we're slowly switching over to all Linux machines (or at least all dual-boot).  This is the first real problem I've had; I'm on #3 of 5, and of course it starts with the one that's integrated into a large cabinet that's set up in the basement.

Sorry if you're upset that I used your full(erene) name... if you're wondering, my handle is a reference to the one-liner, "If you're not part of the solution, you're part of the precipitate."

---

### Post by solutionorppt on 2010-04-19
OK, so now I'm following pytheas22's ndiswrapper troubleshooting guide found here:

[http://ubuntuforums.org/showthread.php?t=885847](http://ubuntuforums.org/showthread.php?t=885847)

When I type 'ndiswrapper -l' into terminal, it just hangs there indefinitely.

Help?

---

### Post by solutionorppt on 2010-04-19
Also, the device is not listed if I "lsusb".

Am I missing a driver for my USB hub?  This seems a bit drastic since I haven't had to install or configure such a thing on my other machines to get Ubuntu to recognize USB devices.

---

### Post by Bucky Ball on 2010-04-20
Ndiswrapper is superseded basically, shouldn't be required. As I say, if you could only get a cable down there. What happens when you plug your USB dongle device into one of the other Ubuntu machines when it is online with a cable? If it finds some drivers and the USB device is recognised, then I would get rid of ndiswrapper asap and start again by searching for the correct drivers by finding which ones the online machine downloads. 

Ndiswrapper is a fully qualified nightmare which is close to obsolete on Ubuntu. Avoid where possible.

... and yes, Buckminsterfullerene is fine if you could be bothered typing it!

---

### Post by ubunterooster on 2010-04-20
> **Bucky Ball said:**
>  Ndiswrapper is a fully qualified nightmare which is close to obsolete on Ubuntu. Avoid where possible.
True. The commercial application [linuxant]("http://www.linuxant.com") is a lot better. But still not perfect. [Hence the free trial]

Personally though, it seems better to get a new device.

---

### Post by anewguy on 2010-04-20
Personally, I would try getting back to a more or less clean slate:

- unplug the USB adapter

- using synaptic package manager, remove ndiswrapper and ndisgtk

- edit the blacklist.conf file and comment out (put a "# " at the front of the lines) your blacklist of b43 and ssb

- plug the USB adapter straight into a USB port, *not* a USB hub

- now try the lsusb again -> if it works please post the output back here so we can see the dongle type and chipset

Also - did you try it without adding a driver?  I'm not sure now what model it was, but I had a Belkin USB wireless adapter a year or so ago and it worked right out of the box.

Also - we can assume you did some homework before you tried installing the driver with ndiswrapper.  Can you tell us what made you decide to blacklist the broadcom drivers and try to install with ndiswrapper?

And just a personal aside, there are still plenty of adapters out there without native support, and ndiswrapper, being free, is the best option yet for getting those working.  Don't get me wrong - I'm all for using built-in drivers, firmware images, etc., but sometimes ndiswrapper is the best choice.  Sometimes it is also easier for some users to just follow the step-by-step instructions for ndiswrapper as long as they are laid out in a way they can copy and paste to use.  Not sure why - I assume it probably has to do with them being new yet from Windows and seeing a Windows driver makes them feel "safe".  Please - I'm not advocating ndiswrapper as *the* solution for most people, but in some cases it is the easiest and fastest way to get a newbie going. ;)

Dave ;)

---

### Post by anewguy on 2010-04-20
> **Bucky Ball said:**
> Ndiswrapper is superseded basically, shouldn't be required. As I say, if you could only get a cable down there. What happens when you plug your USB dongle device into one of the other Ubuntu machines when it is online with a cable? If it finds some drivers and the USB device is recognised, then I would get rid of ndiswrapper asap and start again by searching for the correct drivers by finding which ones the online machine downloads. 

Ndiswrapper is a fully qualified nightmare which is close to obsolete on Ubuntu. Avoid where possible.

... and yes, Buckminsterfullerene is fine if you could be bothered typing it!

Hey - just wanted to add here, I agree with you on ndiswrapper, but wanted to mention that sometimes it is still needed.  My previous post wasn't an attack or anything, so I hope you didn't take it that way (maybe I'm just too paranoid when I post like that ;) ).

Hadn't heard buckminsterfuller in a long time - thought I'd add something we used to do *years* ago as the message of the day on the mainframes I worked on:

!ebut siht edisni evitpac dleh m'I  !!!!!PLEH

;)

Dave ;)

---

