---
title: "need help installing nvidia driver"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by bluepowder7 on 2009-05-09
hi all,

i need help (badly) installing my nvidia drivers.  i think my last attempt was done wrong, and i've been living with crappy 800x600 resolution on my 24" screen for nearly 2 months now.

ok, what do i need to do?  can someone PLEASE give me step-by-step instructions on how to remove my last install attempt, what files and utils i MUST have in order to make it work (and how to install them), and lastly how to actually go through the process?  i'm mostly a user, so i won't know how to "just do this this and this" 

i have the 180.51-pkg2.run file downloaded today, but my last install attempt was using 180.29 so how do i undo that?  if i just try to "sudo sh ./NVIDIAxxxxx" i get an "Extraction failed.  Signal caught, cleaning up" and nothing more.

---

### Post by bumanie on 2009-05-09
Have you gone to System --> Administration --> hardware drivers and tried to install the proprietary driver from there - only in rare cases is the .run file from the nvidia site. However, if you want to use the manual method, [look here]("http://swik.net/Ubuntu/Only+Ubuntu/Howto+install+manually+nVidia+drivers+in+Ubuntu/cc5gw"). To get rid of what you have tried to do so far > sudo aptitude purge < name of package> Don't use the greater and less than signs, only the name.

---

### Post by -kg- on 2009-05-09
You might also want to check out [Envy:]("http://albertomilone.com/nvidia_scripts1.html")

> Envy" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) install the right driver for your card and all the required dependencies
3) configure the Xserver for you

This, of course, presupposes that the installation of the normal restricted drivers doesn't work to your satisfaction, as above.

---

### Post by bluepowder7 on 2009-05-09
> **bumanie said:**
> Have you gone to System --> Administration --> hardware drivers and tried to install the proprietary driver from there -

i would if i could - in Xfce (Xubuntu), the box is totally empty and it clearly says that no proprietary drivers are installed (or available as far as i can tell, cuz they're not even listed for me to "enable" them)



> **-kg- said:**
> You might also want to check out [Envy:]("http://albertomilone.com/nvidia_scripts1.html")

hmm, ok, i installed and ran envy, and it (a) only installs an old driver, judging by the number, and won't let me manually say "hey, install this one that i downloaded here", and (b) the driver it installed doesn't drive, as in on reboot i get a dead black screen, no login prompt and Ctrl-Alt-F1 doesn't get me anywhere either.



i'm only able to do stuff now cuz i rebooted into recovery mode, took the "fix xorg / xserver" option, and i'm now somehow sitting with some higher resolution, maybe 1280x1024.  still a far cry from 1920x1200, though.

i did notice that while envy was doing stuff, it said that there's too many nvidia entried in the kernel.  no idea what that means or what it wants me to do about that...

---

### Post by Efros on 2009-05-09
You could try this thread [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) I used the tricky tricky method on 8.04 IIRC successfully.

---

### Post by bluepowder7 on 2009-05-09
> **Efros said:**
> You could try this thread [http://ubuntuforums.org/showthread.php?t=880787](http://ubuntuforums.org/showthread.php?t=880787) I used the tricky tricky method on 8.04 IIRC successfully.

ok, that i think MOSTLY worked.  removed a ton of stuff, and during a reboot was able to get the "nv" driver to work with a 1920x1200 resolution.  somehow, i wasn't able to get the "nvidia" driver that i installed going, because if i try to now use the "Nvidia X Server Settings" tool, it tells me i'm not using the "NVIDIA X driver".

ugh, at least i have the resolution.  no idea if i'm using the driver properly, especially the graphics memory.  how can i be SURE that i'm using the right type of driver and making most use of the card?

---

