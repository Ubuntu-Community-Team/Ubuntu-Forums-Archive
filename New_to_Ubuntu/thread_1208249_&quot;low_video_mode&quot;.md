---
title: "&quot;low video mode?&quot;"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by rfsquared on 2009-07-09
ok so i just loaded 9.04 on my laptop after having been on vista for a year or so.  ubuntu worked perfectly upon loading for the first time.

then, it happened.

i was running Update Manager to get all of those stupid unnecessary updates just so it would shut up about it.  Well, it froze during the installation, i had to force quit, THEN the next time i tried to restart my computer, ubuntu wouldn't load.

it says something about 'entering low graphics mode' or something (which i've not seen before EVER and i've been using ubuntu for a couple years now on my desktop), and then whenyou try to log in on the GUI under low graphics mode, it cuts out and says 'your session lasted less than 10 seconds'

well, i slipped my ubuntu installation CD in, and when you go to "install ubuntu" it does nothing and hangs.  and you just have to turn it off.

am i just screwed out of my laptop?  i'm familiar with ubuntu and stuff but NOT as far as troubleshooting the OS, etc.

---

### Post by rfsquared on 2009-07-09
PS: this is everything on it that it says, error wise:

Ubuntu is running in low-graphics mode

The following error was encountered.  You may need to update your configuration to resolve this.

(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) [drm] drmOpen failed.
(EE) intel(0): [dri] DRIScreenInit failed.  Disabling DRI.
(EE) intel(0): Couldn't allocate video memory.

And again, it worked PERFECTLY the first time I used 9.04 after I installed it.  It only stopped working after Update Manager froze and had to be forced to quit.

Did something go haywire with my updates?  I am NOT familiar with any command-prompt side of ubuntu, and I can get to a command prompt just fine, so if I need anything like that please let me know exactly what i need to write in it. lol.  Call me a n00b.

I want 9.04 working.  Someone just PLEASE help me!

---

### Post by duanedesign on 2009-07-09
- When the machine boots up, press &#8216;Esc&#8217; to get to the Grub menu
- Select one of the &#8220;recovery mode&#8221; options. This will boot you up to a single-user root prompt.
Run
```
sudo cat  /var/log/dpkg.log
```

post the files it installed on the day it froze.

---

### Post by rfsquared on 2009-07-09
> **duanedesign said:**
> - When the machine boots up, press ‘Esc’ to get to the Grub menu
- Select one of the “recovery mode” options. This will boot you up to a single-user root prompt.
Run
```
sudo cat  /var/log/dpkg.log
```

k...it brought me back to a root prompt.  what next?

---

### Post by rfsquared on 2009-07-09
Um, it's like a huge list.  How do I make it scroll up?  Sorry, like I said, I use Ubuntu but only like the GUI part.

The last few things that I can see on the screen are all about Firefox 3.0.

status unpacked firefox-3.0-branding 3.0.11+build2+nobinonly-0ubuntu0.9.04.1
upgrade firefox-3.0 3.0.8+nobinonly-0ubuntu3 3.0.11+build2+nobinonly-0ubuntu0.9.04.1

etc.etc.etc.

it spits out a huuuumongous list though

---

### Post by duanedesign on 2009-07-09
We can try to finish the update

```
sudo apt-get update; sudo apt-get upgrade
```

then 
[B]
reboot[/B]

---

### Post by rfsquared on 2009-07-09
ok so i got the computer up and running.

now in the GRUB options (when you hit ESC) there are two bootable kernels or w/e...one ends in 11, the other in 13.  13 is the one that works, 11 i'm assuming is the old one.

how do i know that it'll boot into the one that ends in 13 if i restart?  i'm afraid to shut off my computer lol

---

### Post by Malta paul on 2009-07-09
Your problem is most likely caused buy the -13 kernel not working with you graphics. Just start in the recovery mode with the -11 kernel and it should the boot up ok.

:p

---

### Post by rfsquared on 2009-07-09
No no no...the -13 is the one that WORKS when i select it from the GRUB menu...the -11 was the one that didn't work from before...then i ran the thing in recovery mode to unpack all packages and that's when -13 appeared (after a reboot) and now it magically works.

---

### Post by Malta paul on 2009-07-09
Great you got it working, I would now use the -13 as your default boot. Try this for a while then if every thing is working O.K. you can edit the old -11 out of your grub menu.

Have fun :cool:

---

### Post by Dr Jekyll on 2009-07-17
Having the same problem as rfsquared. I installed the latest version of ubuntu network remix (almost sure it's on Jaunty) on my asus eee pc 1000H and it run once properly. Then it froze midway through the update and now I get the following error at start up

(EE) GARTI: Unable to open /dev/agpart (No such file or directory)
(EE) [drm] drmOpen failed
(EE) intel(0): [dri] DRIScreenInit failed. Disabling DRI
(EE) intel (0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel (0): Couldn't allocate video memory

I have tried changing the video ram at the BIOS but there is no such option.
I have also tried to complete the update and upgrade like suggested by Malta Paul but nothing happened
When I go into recovery mode it only shows one type of kernel (-11), or at least I guess that's what that means (noob ALERT :?)
Do I need to change the kernel to fix this low graphics mode problem?

---

