---
title: "Ubuntu 9.04 - Won't wake up from Suspend"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by ismene on 2009-07-22
Hello, 

I'm running Jaunty on a Dell Dimension 4600. I've figured out my first problem of getting video to work by reverting  the video drivers back to intrepid drivers. 

BUT, my new problem is that last night, I decided to click on "Suspend" just to see what it would do. I'm now feeling like a twit - it won't wake up. At all. I have held the power button down several times to shut the machine off totally, and when I turn it back on, it runs through the bios and I just get a black screen of nothing. 

I've searched through the forums for a fix, and everyone else's somehow seems to magically wake up, but mine isn't. What should do I? Is my only option to reinstall? 

*sigh* I'm feeling like an idiot...

---

### Post by ajgreeny on 2009-07-22
Try Ctrl+Alt+F2 to get a cli, and then login to that and issue command ```
startx
```It may get you back to a gui, but then you will need to search further on your suspend problem.

---

### Post by ismene on 2009-07-22
Thank you - I will try that when I get home tonight!

---

### Post by Mark Phelps on 2009-07-22
If you can't get into a desktop or command line, you could try booting into the BIOS, checking your power options, and disabling any sleep, hibernate, or other power saving features.  That should allow you to get to a desktop upon the next reboot.

---

### Post by ismene on 2009-07-22
> **ajgreeny said:**
> Try Ctrl+Alt+F2 to get a cli, and then login to that and issue command ```
startx
```It may get you back to a gui, but then you will need to search further on your suspend problem.

Right - the above didn't help (but thank you for suggesting it!) What happened when I pushed ctrl Alt F2 is that it gave me a different black screen with a flashing line (like a prompt) that wouldn't let me type anything. (It was just torturing me)

I did somehow figure out how to fix it though - just going to post it in case it helps anyone else. I hit ESC when grub started and then selected a safe mode kernel. It booted into safe mode and I was able to log on to the machine and then shut down properly. After that, when I booted it back up, everything was normal. 


Cheers!

---

### Post by ajgreeny on 2009-07-23
What do you mean by "safe mode kernel"?  Recovery mode is all that usually appears in the grub menu, apart from the normal boot.

---

