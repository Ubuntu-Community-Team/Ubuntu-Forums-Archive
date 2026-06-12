---
title: "log in problem"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by camano on 2008-12-13
Hello all,
I have a booting problem I hope you can help me with.I had a "Windows" machine that I downloaded Ubuntu 8.10 onto.I followed the instructions on the install cd,and all seemed to go well.I had let the cd do the partions and used the whole drive.My problem is,when I tried to log back in after having shut down the computer, I could not.I did some reading on the internet, and found out that other folks were having the same problem.The finger seemed to point to "compiz" so I did what was recommened,which was to get rid of it(correctly,I hope).My trouble now is that I can't get to the "log-in" window in one single boot.What happens is,I'll turn on my computer,my monitor will come out of hibernation,and for all intents and purposes,look like it's going to boot up.then for some reason the monitor goes back into hibernation, and at that point I can't get to the log-in screen.what I do next is a hard shutdown of the computer,count to ten,then restart it.It will now go through the boot-up sequence all the way to the log-in screen,and from there on every thing is fine.Please,if you decide to reply to my inquiry please be patient with me as I'm completely new to linux and only a moderate Windows user.Thank you.

---

### Post by Moop on 2008-12-13
Have you tried typing your user name and password even though you can't see anything? 

Type your user name and hit enter and then your password and hit enter. Does anything happen?

---

### Post by camano on 2008-12-13
Sorry Moop,that did'nt help.I'm willing to try any other suggestions you may have.

---

### Post by Moop on 2008-12-13
I'm not sure. Have you tried booting into recovery mode to see if it boots ok? 

Do you have visual effects turned off in System-Preferences-Appearance? 

Do you have your video driver installed? System-Administration-Hardware Drivers

---

### Post by camano on 2008-12-14
Hello Moop,
I tried booting into recovery mode ("ubuntu 8.10,kernel 2.6.27-9-generic recovery mode")("resume normal boot"-yes) this morning and it worked!I also checked your other suggestions.Yes,I have the "basic" appearance highlighted. and in "system-administration-hardware drivers" I get a "no proprietary drivers are in use on this system" I don't know if it makes a difference,I have no video card.My video is "on board" as is my sound.What do you think?

---

### Post by unutbu on 2008-12-14
I wonder if the problem is brought about by unclean shutdowns.

Are you using hibernation, or are you doing a regular shutdown?

Also, if your machine ever hangs, try not to poweroff the machine -- it can leave the hard drive in a bad state. Try doing this first:
```

Alt-SysRq-R    # turns off keyboard raw mode and sets it to XLATE
Alt-SysRq-E    # send a SIGTERM to all processes, except for init.
Alt-SysRq-I    # send a SIGKILL to all processes, except for init.
Alt-SysRq-S    # attempt to sync all mounted filesystems.
Alt-SysRq-U    # attempt to remount all mounted filesystems read-only.
Alt-SysRq-O    # poweroff
```

Wait a few seconds between each command to give the kernel time to complete each.

You can find more info on SysRq commands here:
[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)
[http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html](http://www.brunolinux.com/01-First_Things_To_Know/Skinny_Elephants.html)

---

### Post by camano on 2008-12-15
Thanks Unutbu for joining the conversation.I tried your suggestions,read the links,tried the "skinny elephant" to no avail.I did as Pmdematagoda suggested to see if I'm suffering from "kernel freeze".I must be because after inputting the code I found no "config_magic_sysrq.Also I hope I used the right verbage when I described what my monitor does when I first try to boot up.What happens,my monitor "on" light goes from amber to green than back to amber.During this time my computer "on/off" button stays green.When I have succesfully logged on and finish what I was doing- browsing, internet, etc. I'll go ahead and "shut down" via the drop-down menu on the task bar. What I find strange is that after I've shut down the computer (Green light goes off) and my monitor light goes from green to amber, I can do a ten-count, restart the computer, and it will take me all the way to the log-in screen.Once there I'm fine, it's only after the computer's been sitting awhile that I have trouble booting-up properly. Where can we go from here? Thank you.

---

### Post by unutbu on 2008-12-16
I don't know for certain if this will work, but perhaps it is worth a try:

Next time you shutdown, turn your monitor completely off. Don't let it sit in the amber power-saving mode. Let your machine sit for a good long time, as needed to reproduce the problem. Then powerup the machine and turn the monitor on.

---

### Post by camano on 2008-12-17
Hey Unutbu,
I tried your suggestion.Sorry to say that it did'nt work.I wonder if I would be better off reinstalling ubuntu 8.10 and hope that does the trick.What would be the best way go about it?Any ideas.thanks

---

### Post by unutbu on 2008-12-17
camano, if you have your home directory backed up, reinstalling sounds like a fair idea. Good luck, and let us know how it goes.

---

