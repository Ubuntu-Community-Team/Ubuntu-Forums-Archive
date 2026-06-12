---
title: "Shutdown &amp; Restart ?glitch?"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by benjamin.s.vaccaro on 2009-05-13
Hello,

I've been using 9.04 since its release and I have kept it updated. The problem I have encountered is during the shutdown. After I have selected restart or shutdown I receive the 60 second countdown prompt. Regardless of whether it finishes the countdown or I select "shutdown/restart now" I still get the same error. 

The error occurs after ubuntu boots down and before my computer is signaled to power off. Basically after the ubuntu load screen I will get a black screen with an underscore "_" in the top left. There I can type, not backspace or esc. I have tried several things and I do not believe it is the terminal or the like. 

I've encountered this error a few times and now it is occurring more than before and sadly I have been forced to cold boot which I do not like.

Also: When I restart or shutdown I do not have any applications running.

Thank you for reading this.

---

### Post by enigmaniac23 on 2009-05-13
I have no idea if this will help or not...BUT...I have what might be a similar issue on a Dell laptop.  If I restart with my Ipod connected, I will end up with a blinking underscore in the top left corner of my screen and I have to push the power button to get anything done.  This doesn't happen to my other computer, only the Dell.  I haven't really looked into resolving it, I just stopped booting, or restarting with my Ipod connected.  I thought it might at least be worth trying, if you are booting up with an external device connected.  I'm not sure if it's just an Ipod, or if this would also happen with an external drive, I haven't tried.

---

### Post by benjamin.s.vaccaro on 2009-05-13
Interesting, the only externals i have connected is a mouse and printer. But I'll try without the printer.

---

### Post by Oliver_M_V on 2009-06-04
I have a similar issue (also with a Dell laptop). Most of the time when I click restart, it manages to execute normally; however, when shutting down (or sometimes while restarting), I either am left with a blinking underscore in the top left corner or I get nasty graphical artifacts all over my screen. If I'm stuck at the underscore, only a Ctrl+Alt+Del combination will manage to unfreeze the machine (however this simply restarts the machine.... annoying when I want to shut it down!); the colorful alternative doesn't respond to any key-combination. I've gotten the latest updates and am running Ubuntu 9.04. I am a newbie to the Linux world, but I have some wise buddies to help.

P.S. There are no peripherals attached to my laptop, and my Dell Dimension 9150 Desktop seems to shutdown normally using the exact same configuration. Does it matter if I am dual-booting Windows and Linux? Any help or suggestions would be appreciated!

---

### Post by Ravernomina on 2009-06-04
try using terminal to shutdown?


```
Sudo shutdown -h now
```

---

### Post by Oliver_M_V on 2009-06-04
That didn't change anything, it still goes all the way past the ubuntu logo and ends with a black screen with weird colors; the machine then just stays like that forever. Might it help if I mentioned that during the installation of ubuntu, i had to manually configure the menu.lst in the grub folder because the ubuntu installer failed to correctly install grub? I'm really lost on this problem :(

---

