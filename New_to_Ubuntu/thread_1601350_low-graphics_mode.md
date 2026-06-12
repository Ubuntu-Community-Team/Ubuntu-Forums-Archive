---
title: "low-graphics mode"
date: 2010-10-20
forum: New to Ubuntu
---

### Post by laz777 on 2010-10-20
I've read through some posts on this issue, and I've gotten a bit confused.
updated the kernel today in lucid desktop on my eee pc 1005ha, everything was running smoothly through several reboots. my last resort is to post, sorry if it is repetitive.
my first inkling of a problem was when I was going for another reboot using cairo's shut down. no options there except log out and suspend.
manually rebooted and got the low graphics mode warning, followed what looked like it could be a help in solving the issue and came up with a continuous loop.
booted to usb and found a possible solution with grub, entered the nomodeset and rebooted into a gui, install backround with a dialogue box with my user name and asking for my pass.
entered that and got the same thing back, just a continuous loop of the same screen and dialogue box.
I've seen a post here:
 [http://ubuntuforums.org/showthread.php?t=1484137&highlight=low-graphics+mode+lucid+1005ha](http://ubuntuforums.org/showthread.php?t=1484137&highlight=low-graphics+mode+lucid+1005ha)

that looks like a solution, but I cannot boot into anywhere where I can connect to the net, download and install this package.
I am mostly certain it has to do with the kernel update and my video card, but the looping issue has me wondering.
is there any solution to fix this that I can boot from a live cd and work through?

---

### Post by mastablasta on 2010-10-20
connect to internet with cable and boot to comandline (CLI) only (instead of to gui). the insctructions in the thread are in command line anyway.

---

### Post by GabrielYYZ on 2010-10-20
indeed, all those things in that thread don't require a gui 

```
things in here are usually terminal commands
```

some people add $ at the beginning of commands, but that's just the prompt, as in "user@user-desktop$" everything after $ are commands.

if i were you, i'd boot with the live cd and would try to check the logs (i think they don't need root to let you check 'em but my memory's failing me now) that way you could get a much better idea of what's wrong.

---

### Post by laz777 on 2010-10-20
> **GabrielYYZ said:**
> in
if i were you, i'd boot with the live cd and would try to check the logs (i think they don't need root to let you check 'em but my memory's failing me now) that way you could get a much better idea of what's wrong.

am looking at log files right now from the live cd, under system/administration/log file viewer
not certain that these apply to anything but the liive cd

and thank you as well mastablasta, used the CLI with ethernet connection, didn't solve the problem, but that worked ....

I would like to work through this instead of a reinstall. I had my system tweaked and looking very nice, hate to do it all over again, it was much work :)

---

### Post by mastablasta on 2010-10-20
basically you are saying you can't enter to gnome environment (or are you maybe using netbook edition?) but up until the login screen everything works as normal. you could try to install desktop environment from command line. i dont' know what's the command.
 
have you tried
> startx
from command line. this command starts the GUI.

---

### Post by laz777 on 2010-10-20
forgot to mention I am running 10.04.1 desktop on my eee 1005ha.
startx will bring me a very basic gui, with the original install backround, and a dialogue box with my user name. when I enter my password, all it does is open the same dialogue box over and over again, with my only other option available is to restart or shut down.

---

### Post by laz777 on 2010-10-20
thank you both for offering your suggestions.
I have opted for the easy way out..blah
I have installed 10.10 desktop and lost my settings, but I learned a few lessons.
in retrospect, I believe I had as many if not more problems with win 3.1 on my 486/50 when I was brand new to computing.
this is almost an entirely new experience for me. the only familiarity I have in linux is with playing with BT3 and Slax. and I do mean playing.
I decided to get rid of windoze, move forward and not look back...I don't regret having made that decision.

---

