---
title: "PC Shut down problem"
date: 2009-08-09
forum: New to Ubuntu
---

### Post by singhs on 2009-08-09
I have just installed Jaunty on my Dell Desktop. The computer is not shutting down properly even since. Clicked Shut down option and waited for the system to shut down by itself. Never happen. Always get blank screen with blinking cursor at the top left hand corner.

Please help

---

### Post by charliehorse55 on 2009-08-09
Do you see the splash screen that you see on boot up, only in reverse?

Like this:

Click Shutdown

See Ubuntu Splash with bar decreasing

Gets stuck at Blinking Cursor

Is it like that?

---

### Post by Rocket2DMn on 2009-08-09
Can you try shutting down from a tty and telling us where it holds up?  Do CTRL+ALT+F1 and login at the terminal prompt.  Then run
```
sudo shutdown -h now
```
The system should then shutdown.  If it doesn't please tell us what the screen says (or take a picture).  If it shows the same as before, try doing CTRL+ALT+F1 again to see if it will take you back to the tty so you can see what it shows.

---

### Post by singhs on 2009-08-09
After CTRL+ALT+F1
 
Message on screen reads as follow
 
**Boot from (hd0,0) ext3    ef6dbb44-947f-4e08-92a9-ffae2a0d6912**
**Starting up ...**
**Loading, please wait...**
**19+0 records in**
**19+0 records out**
**kinit: name_to_dev_t(/dev/disk/by-uuid/0abd837e-0786-4425-98ef-03515a21c13f) = dev(8,5)**
**kinit to resume from /dev/disk/by-uuid/0abd837e-0786-4425-98ef-03515a21c13f**
**kinit: No resume image, doing normal boot...**
 
**Ubuntu 9.04 singhs-desktop tty1**
 
**singhs-desktop login:**
 
 
**The programs included with the Ubuntu system etc etc......**
 
**Ubuntu comes with etc etc.....**
 
 
**0 packages can be updated**
**0 updates are security updates**
 
[EMAIL="singhs@singhs-desktop:$"]**singhs@singhs-desktop:$**[/EMAIL]
 
 
After I did
 
**Sudo shutdown -h now**
 
Took me out from tty to previous screen
Then remain blank with blinking cursor
like before

---

### Post by Rocket2DMn on 2009-08-09
When you boot your system, does it show the splash screen with the Ubuntu logo, and the loading progress bar?  This could be a problem with usplash.

If it does show the splash screen, it could be that the system simply isn't halting after the shutdown process.

---

