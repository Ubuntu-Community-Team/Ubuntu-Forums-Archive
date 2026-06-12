---
title: "beginner help: graphics card and suspension"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by snot15 on 2009-09-25
Hi, Im a beginner user to Ubuntu and everything was going fine until i configured my screen saver settings. After i selected my screensaver and the amount of time i wanted it to suspend after, a new error has constantly been popping up. My computer will display the screeensaver and then will fall asleep, but will immediatly wake up with the error message "Your computer **failed to suspend**. Check the help file for common problems". The help files go in a circle and i cannot figure out how to fix this problem.
 
Also, my graphics will randomly go out. I will be working and my file browser will glitch and look like a fuzzy tv and will remain that way until i refesh my compiz. How do i fix this?
 
-thanks for the help
snot

---

### Post by Buuntu on 2009-09-25
Have you installed the recommended drivers in System > Administration > Hardware Drivers?

---

### Post by snot15 on 2009-09-26
I checked the Hardware Drivers, and it says that "No proprietary drivers are in use on this system"

---

### Post by thiebaude on 2009-09-26
What graphics card do you have?

---

### Post by snot15 on 2009-09-26
i have no idea.  Where do i even find that out?

---

### Post by sandyd on 2009-09-26
Applications -> Accessories -> Terminal
copy and paste this in.
```

lspci

```then post the output

---

### Post by snot15 on 2009-09-26
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)


When i put the code in this is the result, so i'm guessing an intel 4 series graphics card? i have an intel dual processor so i think its the same

---

### Post by snot15 on 2009-10-01
New Development!  when i refresh my compiz manager, the screen goes black for about 30 seconds and then refreshes, with the exception of a couple times when i had to reboot

---

