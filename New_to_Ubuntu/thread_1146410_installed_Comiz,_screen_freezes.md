---
title: "installed Comiz, screen freezes"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by jmedoro on 2009-05-02
Hey everyone, just installed Compiz and the settings manager. I enabled the little cube effect, the little fire effect, some kind of water effect, and the last thing i remember doing was fooling around with the cube settings (rows/colums for the desktop screen, maybe?)...

Then withtout really clicking anything else, my screen starts flashing purple/green for about 5 seconds. After this, i get a new desktop screen, asking me for my username (which doesnt happen on normal startup). i enter it, and the purple/green screen comes up again.

The thing is...for the brief moment my desktop screen is up, i see that the whole appearance has changed (as if some of the compiz settings where enabled). the wallpaper is different, font is different, i have the 'start/restart/hibernate' button in the lower left corner as in Windows. It looks awesome, its a shame that its freezing.

1. I'm guessing my laptop cant handle compiz...is this what happens when this is the case?

2. how to i disable compiz, now that i cant really log in?

3. what is my laptop required to have to run compiz without this happening?

thanks everyone...

---

### Post by bardophile on 2009-05-02
1. Not in the case of my desktop. My whole screen would just go black. :)

2. You reboot, and select "recovery mode". Then choose to "drop to root" (I think that's the option). Then you're at the root prompt, and should be able to "apt-get remove compiz compiz-fusion"

3. You might want to check out [Compiz-check]("http://forlong.blogage.de/entries/pages/Compiz-Check"), a script that helps you figure out whether your computer can handle Compiz. It does a series of tests, and offers you suggestions on why any of them may not have checked out ok...

Good luck

---

### Post by jmedoro on 2009-05-02
thanks...

ok, did what you said. i got a message saying 'could not find compiz-fusion,' so i just retyped the command as 'remove compiz' and left it at that. seems like it worked, until i restarted and had the same problem.

i'm wondering if i did not uninstall it properly, or if its uninstalled but any of the settings it may have changed are what is causing the problem.

---

### Post by bardophile on 2009-05-05
Sorry to ditch you mid-stream. 

Try this:
Reboot in recovery mode again
Drop to root
sudo apt-get remove compiz-core
resume normal boot

I hope this works, because I've just exhausted the limits of my (lack of) Ubuntu expertise. Good luck. If this doesn't work, but you find another solution, you may want to post it here to benefit other users.

---

