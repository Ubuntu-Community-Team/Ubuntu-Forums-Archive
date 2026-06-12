---
title: "Upgrade took the taskbar away!  And no Unity?!?"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by jlo301 on 2011-06-23
I just did the upgrade to 11.04 from 10.10 and upon reboot there's no menu bar (clock/network/mail/on/off) at the top, but a fuzzy line where it should be... and the Unity bar doesn't show up at all - not with the windows key or anything?!  However, using the guest account, everything works fine - just can't get to my stuff!

Help!  Ugh...

---

### Post by wolfen69 on 2011-06-23
I don't have a direct answer to your problem, but I would use a live cd to get all of your stuff off of the computer, and onto an external drive or something. Then, I would do a clean install of 11.04. Upgrades *can*, and *do* go wrong.

---

### Post by roololing on 2011-06-23
Are your windows working okay? When my toolbar and launcher went iffy before, the windows were also messed up. Anyway, I think Unity may be the problem, as it has been for me a few times. Try running
```
unity --reset
```

---

### Post by jlo301 on 2011-06-23
I'll try that in the terminal  --  if i can find the terminal..  the windows seem to choose when they like to show up...

---

### Post by jlo301 on 2011-06-23
> **roololing said:**
> Are your windows working okay? When my toolbar and launcher went iffy before, the windows were also messed up. Anyway, I think Unity may be the problem, as it has been for me a few times. Try running
```
unity --reset
```

that made the whole thing crash - error after error in terminal - i think it's time for a clean install...  *sigh*

---

### Post by roololing on 2011-06-23
> **jlo301 said:**
> that made the whole thing crash - error after error in terminal - i think it's time for a clean install...  *sigh*
Ah. Sorry. That's how I fixed mine when the toolbar got fuzzy and the launcher wasn't showing up.... #-o

Good luck.

---

### Post by LowSky on 2011-06-23
its a process... but this worked for me

then go into your home folder. show the hidden files (ctrl+H) then delete everything that belongs to gnome and compiz. if you are using a graphics card like Nvidia or ATI, uninstall the driver, reboot then reinstall then reboot.

---

### Post by wildmanne39 on 2011-06-23
> **jlo301 said:**
> I just did the upgrade to 11.04 from 10.10 and upon reboot there's no menu bar (clock/network/mail/on/off) at the top, but a fuzzy line where it should be... and the Unity bar doesn't show up at all - not with the windows key or anything?!  However, using the guest account, everything works fine - just can't get to my stuff!

Help!  Ugh...Hi, this problem has happened a lot with people who upgrade from 10.10 instead of a clean install, I am posting a link that should fix you up.
[http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html](http://ubuntu4beginners.blogspot.com/2011/04/missing-top-and-side-panels-in-unity.html)

---

### Post by Maheriano on 2011-06-23
There are a few hundred threads on this already. Get a fix from any one of them.

---

### Post by Super-Dan on 2011-06-23
What I did was created a launcher with this code

gnome-session-save --logout-dialog

Log out and sign into Ubuntu Classic.

---

### Post by wildmanne39 on 2011-06-23
Hi, if you go to the link in post #8 you should have unity working if your system can run unity.

---

### Post by dFlyer on 2011-06-23
ctl-alt t should get you a terminal.

---

### Post by Super-Dan on 2011-06-23
I somehow managed to disable this when I had this issue!

---

### Post by wildmanne39 on 2011-06-23
> **Super-Dan said:**
> I somehow managed to disable this when I had this issue!
Hi, did you try the link in post #8, you problem is common when upgrading from 10.10 instead of doing a clean install.

---

### Post by jlo301 on 2011-06-27
Thanks for your input, gave everything a go but no dice. Locked it up really, REALLY badly.
I ended up putting the disc image on a USB stick and doing a complete reinstall. Only thing is now I don't have trackpad mouse support!?!  I give up for today. :-)

---

