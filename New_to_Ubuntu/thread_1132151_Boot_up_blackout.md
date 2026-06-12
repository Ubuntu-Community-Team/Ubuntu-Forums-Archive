---
title: "Boot up blackout"
date: 2009-04-21
forum: New to Ubuntu
---

### Post by Midgetprawn on 2009-04-21
Hey Folks
I have been runninh Ubuntu 8.10 succesfully for a year but recently at bootup the screen freezes just as it goes into GDM. Prreviuosly I have just rebooted and it has bypassed this but now it is frozen and only cntrl-alt-del gets me to restart. I am currently online off the live 8.04 Cd as 8.10 CD had blotchy graohics.
Running a radeon X300 on a Dell Dimension 5150

Any suggestions?

---

### Post by LiamWilson on 2009-04-21
Have you tried booting into recovery moode and resetting the X server?

---

### Post by Midgetprawn on 2009-04-21
Yup
Went into recovery console and tried all the fixes but it still jams :(

---

### Post by LiamWilson on 2009-04-21
Try editing the grub menu

```
sudo gedit /boot/grub/menu.lst
```

And on your ubuntu line, delete the words 'quiet' and 'splash' and reboot.

This will remove the graphical splash screen, and you may be able to see if any error messages occur during the boot.


Are you using the Propiatary Driver by any chance?

---

### Post by Midgetprawn on 2009-04-21
I don't run the boot splash so I can see the boot lines and it gets to the end of the commands and goes into that pre-desktop screen and instead of running the desktop it freezes in a big rectangle frieze.
I have the proprietary drivers for ati and it was working OK until today.

---

### Post by LiamWilson on 2009-04-21
Hmmm, sounds like it could possibly be a problem with the Ati card/drivers. However, unless you can do a command line login and run aptitude, I know of no other way to remove them. What you may want to do AS A LAST RESORT is backup all of your data to an external hard drive or whatever, and do a re-install. But this will mean you'd have to update and all that again...

Can you boot from another kernal image and if so, does that work?

---

### Post by Midgetprawn on 2009-04-21
I have tried a previous kernel with no success but I will try another kernel
I had anticipated a backup suggestion and have done so already
I can run a command from recovery mode can't I? Which commands do I need to run to resolve the drivers?

---

### Post by LiamWilson on 2009-04-21
You'll need to run 'aptitude' and look for your 'fgrlx' drivers. I've done it once a while back, but it may take a while to look through all of you're packages and mark them for removal. I think you press ? for help.

If you need any help with aptitude, don't forget to post here! Good luck!

---

### Post by Midgetprawn on 2009-04-21
Cheers

I'm off to bash the keys a bit and see if I have any success.

Thanks for your support Liam

---

