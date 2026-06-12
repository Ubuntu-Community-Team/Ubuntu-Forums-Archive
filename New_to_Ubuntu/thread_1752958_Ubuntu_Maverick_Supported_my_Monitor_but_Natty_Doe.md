---
title: "Ubuntu Maverick Supported my Monitor but Natty Doesn't. Help Please"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by Mindswap1 on 2011-05-08
Hey guys this is very depressing, because it now takes me 2-3 minutes to get to the desktop. Whenever I turn on the computer a small screen saying "Not Optimal Resolution Recommended Screen Size is 1360x768 60Hz" and the sign stays there for 1 minute or so, and then takes me to the log in screen. Its so annoying since it takes forever to get to the log in screen now. I never had this problem in Maverick, and I know for a fact that my monitor is at optimal resolution because I checked the NVDIA application, and it says it is Picture below. However the monitor application doesn't find my monitor pic below. What to do? The reason it says 82 refresh rate in the monitor application picture below is because 60 is not an option its goes 50,51,52,82.

---

### Post by rosencrantz on 2011-05-08
This looks like a driver issue. If I inferred your graphics chip model correctly from the screenshot (it always helps to post as much hardware info as possible) as GeForce 6150SE,
try [this thread]("http://ubuntuforums.org/showthread.php?p=10751607") and the experimental drivers.

---

### Post by Mindswap1 on 2011-05-08
I did a bit of searching, and found out to get the experimental drivers I would have to go a fresh install of 11.04, and not install the updates during the installation, I really don't have anything to backup my data so this is kinda impossible for me at the moment. As for my specs I have a Compaq Presario SR5710F, with a AMD Athalon X2 4450e Dual Core Processor. And My Graphics card is NVIDIA GrForce 6150 SE Graphics.

EDIT: I tried using the other proprietary driver available, and my computer would no longer boot, and so after banging my head against the wall I just did a fresh install, and lost some of my documents, because I didn't have anything to back them up with :(. Anyhow I got the experimental 3D drivers now, and I still have that stupid error message coming up, but now the monitor application detects everything picture below. Ubuntu is starting to be a real pain :/, but theres no way I'm going back to Windows.

I have a Samsung Sync Master 933 monitor.

---

### Post by Not unique on 2011-05-08
I read something similar, is this what you did (drivers)?

[http://ubuntuforums.org/showthread.php?t=1745940](http://ubuntuforums.org/showthread.php?t=1745940)

I quote from the page "They were listed right in the additional drivers section. I use different repos, so maybe that is why I see the option for those drivers" so is that it?

---

### Post by Blasphemist on 2011-05-08
> **Not unique said:**
> I read something similar, is this what you did (drivers)?

[http://ubuntuforums.org/showthread.php?t=1745940](http://ubuntuforums.org/showthread.php?t=1745940)

I quote from the page "They were listed right in the additional drivers section. I use different repos, so maybe that is why I see the option for those drivers" so is that it?

Here are the manual instructions for installing the current proprietary drivers if you don't see them in the additional drivers. 

OP, have you tried setting different resolutions and seeing if the message goes away or changes? I'm wondering if a kernel option setting might get rid of the issue. If that is the case, I don't expect the issue will change no matter what resolution you choose in nvidia.

---

### Post by Mindswap1 on 2011-05-09
I have tired setting different resolutions, and that did not do the trick, I do the have main proprietary drivers installed now. I'm going to just wait till 11.10 comes out, hopefully my Mouse will start working again without having me to constantly unplug and replug it. One can only hope :/.

---

### Post by jtarin on 2011-05-09
Upgrade!! We just need to break things. I'ts our right and duty as humans.

---

### Post by talisman.26 on 2011-05-11
> **Not unique said:**
> I quote from the page "They were listed right in the additional drivers section. I use different repos, so maybe that is why I see the option for those drivers" so is that it?
 
How do you load different repos on Unity?  I'm not sure I like it...it's more difficult to navigate for me unlike GNOME.  Anyway, it's better than windows, but full screen won't work and I've run the gamut of video drivers for my system too.  I've an old card, Nvidia GeForce Go 6600 and everything works except every video program crashes when I go to full screen, or resize to something bigger than 600x400.  Resoultion looks right, and the other driver (not the recommended with Jockey) won't work at all.
 
So...again my question, How do you load different repos?

---

### Post by wildmanne39 on 2011-05-11
> **talisman.26 said:**
> How do you load different repos on Unity?  I'm not sure I like it...it's more difficult to navigate for me unlike GNOME.  Anyway, it's better than windows, but full screen won't work and I've run the gamut of video drivers for my system too.  I've an old card, Nvidia GeForce Go 6600 and everything works except every video program crashes when I go to full screen, or resize to something bigger than 600x400.  Resoultion looks right, and the other driver (not the recommended with Jockey) won't work at all.
 
So...again my question, How do you load different repos?

Hi, I have the same card and the same problem with the screen at boot up, but if you hit the enter button it will go ahead and load ubuntu instead of waiting that extra time. I also had problems with going to full screen also, the solution is to use the proprietary 173 driver not the most current one. I hope this helps made mine work pretty good.:D

---

### Post by wildmanne39 on 2011-05-11
> **talisman.26 said:**
> How do you load different repos on Unity?  I'm not sure I like it...it's more difficult to navigate for me unlike GNOME.  Anyway, it's better than windows, but full screen won't work and I've run the gamut of video drivers for my system too.  I've an old card, Nvidia GeForce Go 6600 and everything works except every video program crashes when I go to full screen, or resize to something bigger than 600x400.  Resoultion looks right, and the other driver (not the recommended with Jockey) won't work at all.
 
So...again my question, How do you load different repos?

Hi, to load different repositories open synaptic package manager click settings,repositories, you will see at the top under ubuntu software make sure you have main,universe,restricted, multiverse checked. under other software you can put a check by any of them that you want to also.):P

---

### Post by talisman.26 on 2011-05-14
THX!!  Will try video driver and repost.

---

