---
title: "How To STOP standby and hibernate?"
date: 2010-10-05
forum: New to Ubuntu
---

### Post by Return Privacy on 2010-10-05
Hi All,
I have Ubuntu 10.04, and it is working quite well, except that it keeps going into either standby/suspend/hibernate (can't tell which) after about 45 minutes. It is not the bios settings on the computer. For some unknown reason, Ubuntu puts it in standby/suspend mode, I don't know which. If I try the keyboard or mouse, nothing happens, black screen. Machine is still powered. I have to push the power button for 5 seconds to hard shut down. I set the Ubuntu preferences for power management to turn on screen saver after 20 minutes, and to NEVER shut down computer or spin down hard drives. I set the "press power button to: shut down", NOT suspend. I set it to shut off the monitor after 30 minutes. 
I don't want Ubuntu to shut down or standby/suspend/hibernate at all. I just want it to blank the monitor after about 30 minutes if I am not using it. 
I went away and this happened. I remotely connected to another computer on the same home network and tried to Wake On Lan the Ubuntu computer from the other computer, and it wouldn't wake because it was in this standby/suspend/hibernate state. (normally  WOL does work on this Ubuntu computer.)
I couldn't force a hard shut down on this Ubuntu remotely over the net, through the other computer.  It is just this Ubuntu standby/suspend/hibernate issue. How can I just STOP Ubuntu from doing this? Thanks-:confused:

---

### Post by Return Privacy on 2010-10-05
Hi all,
How do I mark this as resolved?
I didn't figure out a way to completely stop or disable standby/suspend/hibernate, but I think
I have stopped it from causing me a problem. I went into Ubuntu's settings again, and turned 
off the screensaver. For some unknown reason that was putting Ubuntu in this weird standby/suspend/hibernate state, in which the computer was still powered, but it wouldn't
wake from the standby/suspend/hibernate state at all. (remember, I had to do a hard shut down by pressing the power button for 5 seconds and then reboot). So, it seems that Ubuntu has a bug in the screensaver/standby/hibernate section. This is a clean, new install on a formatted hard drive, of Ubuntu 10.04, and it has only been running for a couple of weeks. Like I said in my first post of this problem, everything else on this Ubuntu computer is working very well. The computer is a Dell Optiplex GX270 series, P4 intel, 2.6 speed. It's a basic machine, but has onboard gigabit ethernet, sound, and video. I can attest that Ubuntu 10.04 installed on this Dell with absolutely no problems at all. Everything worked on the first boot up, sound, video, net, everything. I can't remember the last time, if ever, I had an install of wincrap get it all working just by installing. Ubuntu 10.04 is a Far Superior OS to any version of msware.:KS
I just found how to mark as Solved in thread tools.

---

### Post by Funkey Monkey on 2010-11-13
Thanks for the tip. I am going to try to decative the screensaver.

EDIT:
Tip did not work for me.
I disabled the screensaver. And Powersettings is set to Never sleep.
But still it went to sleep. Opening a new thread to asking for help. :(

---

