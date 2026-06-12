---
title: "Scangearmp won't start"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by Newbie2910 on 2011-05-09
Using 10.04LTS.

I had scangearmp set up so my Canon Pixma MX330 would scan documents... worked fine for a while, but I have not had need to use it for a while.

So now, attempting to use it I cannot get it to "start".  Meaning I attempt to start "Canon MX330 Scanner" by selecting it from the menu, but nothing happens.  I tried starting it manually from the user/bin/ folder, but no luck there either.

Then, I reinstalled the driver.  No difference.

The PC can print to the printer just fine- just will not see the scanner attached, I guess.

Suggestions?

Thanks.

---

### Post by klytu on 2011-05-09
> **Newbie2910 said:**
> Using 10.04LTS.

I had scangearmp set up so my Canon Pixma MX330 would scan documents... worked fine for a while, but I have not had need to use it for a while.

So now, attempting to use it I cannot get it to "start".  Meaning I attempt to start "Canon MX330 Scanner" by selecting it from the menu, but nothing happens.  I tried starting it manually from the user/bin/ folder, but no luck there either.

Then, I reinstalled the driver.  No difference.

The PC can print to the printer just fine- just will not see the scanner attached, I guess.

Suggestions?

Thanks.

For an alternative, see my post (#7) in this thread: [[COLOR="Blue"]_http://ubuntuforums.org/showthread.php?t=1488850&highlight=mx330_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1488850&highlight=mx330") You might not need to change any permissions to get it working; I think that was a Kubuntu issue. If you find the steps confusing, post back and we'll try to help.

I don't know why scangearmp isn't working for you; I've used it on Ubuntu Lucid without any difficulty, but it has been a while. Could be that an update is causing some unusual conflict. I'll try it out when I get home; maybe I have the same problem and just don't know it yet!

---

### Post by jtarin on 2011-05-09
Have you done any upgrades to your system since you last used it? I assume it's USB? Try the command ```
lsusb -v
``` and see if the device is listed.

---

### Post by klytu on 2011-05-10
Unfortunately, I wasn't able to replicate your problem. You mentioned that you tried running scangearmp from the /bin folder, but did you try running it from a terminal window? I ask because if you double-clicked an icon from the GUI, you won't get any feedback as to what might be going wrong. If you issue the command from a terminal window, the output of the failed command may give you some clues as to why it is failing. Try: ```
scangearmp
``` from the terminal.

---

