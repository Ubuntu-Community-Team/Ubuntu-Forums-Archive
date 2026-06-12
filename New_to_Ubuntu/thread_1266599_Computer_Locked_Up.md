---
title: "Computer Locked Up"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-09-14
Hello,

I just installed Google Earth using the Synaptic installer and all went well I thought.

When I opened it, it ran real slow and the tip box kept flashing on and off.

I switched to full screen and it locked up completely, now I can't do anything with it or get out of it.

I really don't want to do a hard shutdown, any suggestions?

---

### Post by dearingj on 2009-09-14
Try this:
-Press Ctrl+Alt+F1 and log into the terminal
-Enter the command "ps -aux | more" and look for a command that might be Google Earth, and note its process ID number
-Enter the command "sudo kill id", replacing id with the number you just found
-Press Ctrl+Alt+F7 to get back to a graphical interface, which hopefully will be showing your desktop.

If your graphical interface is screwed, which can sometimes happen when killing fullscreen programs, go back to the terminal and enter "sudo /etc/init.d/gdm restart"

---

### Post by barnaclebill18 on 2009-09-14
> **dearingj said:**
> Try this:
-Press Ctrl+Alt+F1 and log into the terminal
-Enter the command "ps -aux | more" and look for a command that might be Google Earth, and note its process ID number
-Enter the command "sudo kill id", replacing id with the number you just found
-Press Ctrl+Alt+F7 to get back to a graphical interface, which hopefully will be showing your desktop.

If your graphical interface is screwed, which can sometimes happen when killing fullscreen programs, go back to the terminal and enter "sudo /etc/init.d/gdm restart"
 
I did that and it wont let me log in, says incorrect password.

Thanks

---

### Post by barnaclebill18 on 2009-09-14
[QUOTE=barnaclebill18;7950087]I did that and it wont let me log in, says incorrect password.


I think I just got logged in, it is in full screen and the last thing showing is bill@bill-laptop:~$

I put in the first command given and a whole page of stuff came up but it means nothing to me, like A all processes, N negate selection

---

### Post by barnaclebill18 on 2009-09-14
I think I got it, used the shutdown command.

Now about Google earth doing that, any ideas?

---

### Post by dearingj on 2009-09-14
> **barnaclebill18 said:**
> [QUOTE=barnaclebill18;7950087]I did that and it wont let me log in, says incorrect password.


I think I just got logged in, it is in full screen and the last thing showing is bill@bill-laptop:~$

I put in the first command given and a whole page of stuff came up but it means nothing to me, like A all processes, N negate selection

I think you typed the command wrong. That's a pipe character (on most keyboards it's right above the enter or return key; it may look like a solid line or a dashed line), not a letter I or a number 1.

"ps -aux | more"

What that should show you is a bunch of columns labeled "user", "PID", "command", and some others. Look for a command like "googleearth" or "g-earth" or something like that, and note its corresponding PID. You can use your space bar to scroll down and show more of the processes/commands, since the list will be too long to fit on one screen.

---

### Post by tripolitan on 2009-09-14
what is your version of ubuntu and your hardware (video card, video memory, ram, processor etc?

---

### Post by barnaclebill18 on 2009-09-14
> **tripolitan said:**
> what is your version of ubuntu and your hardware (video card, video memory, ram, processor etc?

I have Jaunty, with the latest updates.

My computer is a Lenovo 3000C 200,Intel Celeron M CPU 430 @ 1.73GHz, 299 GB of RAM.

I am not a computer whiz, I really don't know what video card, the one the comes with this laptop, I think it is built in.

I don't know what video memory is.

Thanks

---

### Post by steve161 on 2009-09-14
If compiz is enabled, disable it (system-preferences-appearance-effects-none.  Then start up googleearth and under "view" in the toolbar, uncheck atmosphere.  When you re-enable compiz, it should run alright, but still may be a little choppy. If this and all other suggestions fail, you may want to take a look at   [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582).  Although I used the optimal method for other reasons, it did solve any issues I had with googleearth.

---

### Post by barnaclebill18 on 2009-09-14
Hey Steve, thanks, that did it, seems to be working good now.

It was set on normal, it is off now but I don't see any difference on the desktop, looks fine to me.

---

### Post by barnaclebill18 on 2009-09-15
[QUOTE=steve161 you may want to take a look at   [http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582).  Although I used the optimal method for other reasons, it did solve any issues I had with googleearth.[/QUOTE]

I looked at the tutorial and was completely lost a third of the way into it.

It is going to take this old guy a long time to figure this stuff out.

---

### Post by steve161 on 2009-09-15
It is an extreme move if googleearth is the only issue you are having.  It was just a suggestion but maybe I should not have posted it.  Try unchecking atmosphere per my previous thread, then re-enable compiz (normal effects) and see how it runs.

---

### Post by barnaclebill18 on 2009-09-15
The only other issue that I know of is trying io get my Sprint air card to work on Ubuntu, I haven't been working on it much because I have the card in an air card router and connect with an ethernet cable.

No one seems to know the answer, I have Googled it every way I can think of. It gets right to "connecting" and just sits there.

I found one post on the EVDO forum that the guy had the same exact problem and they did not get it resolved.

I am still working on that one.

---

### Post by barnaclebill18 on 2009-09-15
> **steve161 said:**
> It is an extreme move if googleearth is the only issue you are having.  It was just a suggestion but maybe I should not have posted it.  Try unchecking atmosphere per my previous thread, then re-enable compiz (normal effects) and see how it runs.

I am glad you posted it, shows me how much I have to learn.

I did uncheck atmasphere as you said and turned off compiz and Google Earth worked great,

I just turned it back to normal and GE did not work good at all, but I was able to close it OK.

I did not see any difference between off and normal.

I just thought of one more issue i am having, my extended desktop does not work right, but I never use that.

Thank you for the interest.

---

### Post by tripolitan on 2009-09-16
If your laptop is stock and you have not added any ram (unmolested laptop), then Jaunty is going to run sluggish on 512RAM and a celeron M cpu with visual effects.

You might want to completely disable compiz (uninstall it if you wish, as well) and when you're more comfortable, open Synaptic and start removing software and services that have been installed by default and that you do not intend to use.

Frankly, for your laptop, I would add more RAM or scale UP to the more-supported Hardy Heron 8.04 LTS version of Ubuntu.

---

