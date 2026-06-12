---
title: "Full screen games freeze Hardy"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by Bearly Able on 2009-03-16
I've just installed TuxMath and Angry Drunken Dwarves, using synaptic.  TuxMath ran fine until I tried to quit, when it froze.  I eventually managed to reboot with ctrl+alt+del.  A short while later, I tried Angry Drunken Dwarves, but as soon as I tried to open it, my monitor displayed "Out of Timing [analogue]" and I couldn't get any further response.  In the end, I had to turn off the power and restart.

We've been running Ubuntu 8.04 as a dual-boot (XP is on a different hard drive) for four or five weeks now, with no problems at all.  As far as I can see, the only thing different about these games is that they run full-screen (I'm having to guess about Angry Drunken Dwarves, as I've never seen it), and we have no other full-screen apps.

Obviously, I'd like a fix if there is one, but I'm more concerned about what is causing the problem so I can avoid it in future.  Anybody have any ideas?

---

### Post by finer recliner on 2009-03-16
if you have compiz running, try (temporarily) disabling that before going into full screen mode.

use fusion-icon (its a gnome tray icon) to quickly go back and forth between metacity and compiz
```
sudo apt-get install fusion-icon
```

---

### Post by stchman on 2009-03-16
Yes, when I play games like Nexuiz and Openarena I have to disable Compiz as well.

---

### Post by Bearly Able on 2009-03-16
Thanks for the hint. Sorry to be really thick here, but I'm not even sure what compiz is, so how do I know if it's running?

---

### Post by finer recliner on 2009-03-16
oops, sorry! compiz is a window manager that gives you added "special effects" to your desktop (ever see a youtube video of the "spinning cube"?) basically its a lot of unnecessary eye-candy.

go to system > preferences > appearance > visual effects tab

set it to "none" if it isnt already.

---

### Post by Bearly Able on 2009-03-17
Thanks for the explanation.

I've set visual effects to none, but I still have the same problem in TuxMath.  I haven't tried Angry Drunken Dwarves again because I don't like having to power off the system to quit.

---

### Post by finer recliner on 2009-03-17
i dont have a solution for you yet. this bug report may be related to your problem though: 

[https://bugs.edge.launchpad.net/ubuntu/+source/tuxmath/+bug/269082](https://bugs.edge.launchpad.net/ubuntu/+source/tuxmath/+bug/269082)


also, next time your computer freezes, you probably don't need to do a hard-restart (holding the power button to force the computer off). First try doing ctrl+alt+F1. this will switch you to tty1 (a new console). log in, and type the command "top". I'm going to assume you'll see tuxmath at the top of the list using all of your CPU cycles. take note of its PID in the first column. press 'q' to quit "top". once back at the shell prompt type "kill <PID>" (where <PID> is the PID of tuxmath). Use "top" again to see if tuxmath was killed successfully. If not, use "kill -9 <PID>" to force it dead. switch back to your normal desktop using ctrl+alt+F7.

If the above didnt bring your desktop back from a frozen state, you can also do ctrl+alt+backspace, this will restart your X-server (which draws all the graphics/images on your screen). It will log you out of your current session, but will at least save you from doing a full restart.

Also check your system logs (System > Administration > log manager, i think) for anything that may be related to your problem

---

### Post by Bearly Able on 2009-03-17
Thanks for that, First Recliner.  I'll check out the bug report, and also keep a copy of your instructions handy in case I need them.

---

### Post by Bearly Able on 2009-03-18
OK, well, armed with the instructions for restarting, I tried Angry Drunken Dwarves again (with "visual effects" set to "none"), and got exactly the same result as before.  At least this time I managed to kill the process and restart the X-server, so thanks again for those instructions.  Guess I'm just not meant to play games!

I've just realised that since I restarted, I've had no sound - I don't know if that's significant?

---

### Post by Bearly Able on 2009-03-19
I've just tried both games on my Lenovo 3000 laptop, which is also running Hardy, and had no problems with either.  Tuxmath on the desktop runs silently, but on the laptop I get audio, so I'm guessing my problem has to do with the way the audio is set up on the desktop.  Unfortunately, I'm a bit lost where to go next; I did the desktop install, but the laptop was pre-installed and I don't know where to start to try to sort out the differences.

Does anybody feel able to assist?

---

