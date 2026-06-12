---
title: "Difference between Hibernation and Suspend"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by JockVSJock on 2009-06-25
Weird question, what is the difference between hibernation and suspend?  

Also these are typically for laptop users right?  However I would like to put my computer in either hibernation/suspend when I am not around during the day.  

Once I do that how do I get it out of hibernation and suspend? 

Also if I were to put it in hibernation/suspend overnight, will cron jobs that are scheduled overnight run ok?

thanks

---

### Post by 3rdalbum on 2009-06-25
Hibernation saves the contents of RAM to hard disk (your swap partition), and then turns the computer off fully. When you turn the computer back on, the state is restored.

Suspend is much simpler: Everything is turned off (or into a very low power state) except the RAM, basically. When you press the power button on your computer, everything turns on. Suspend seems to work more reliably, in my experience.

If you have a desktop computer, you'll probably prefer to suspend as it's quicker to suspend and quicker to unsuspend. Laptop users may prefer to hibernate, because hibernation uses no battery power.

To get your computer out of suspend or hibernate, just press the power button. For suspend, you can often press the space bar or move the mouse.

No code runs while the computer is in suspend or hibernate. Cron jobs will not run, not even when the machine comes back up to full power. Any Anacron or "at" jobs scheduled to run during the low-power state will run after the computer comes back up.

---

### Post by Revolutionary101 on 2009-06-25
In hibernation mode all of your RAM is put on your hard drive and the computer "shuts off" and restores itself to it's previous state when you turn it back on. When your computer goes into sleep mode it will only use enough energy to keep the RAM active. To get out of either of these modes just press any key on your keyboard. If you have a laptop and want to save the most energy put into hibernation mode. Both of these modes will return you to your desktop just like you left it.

Hope that is helpful.

Didn't see the guy post the same thing until after I posted this.

---

### Post by kpkeerthi on 2009-06-25
If you loose power while in suspend mode, you will loose the state.

---

### Post by prvteprts on 2009-06-25
FYI: Hibernation is also known as suspend-to-disk. Suspend is also known as sleep. With Ubuntu, there may be some issues with these two features (especially for laptop users). Test your system using these two features before applying them day to day. You don't want to lose any data... you know.

---

