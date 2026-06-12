---
title: "Very minor issue in 10.04 - session control"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-05-05
I did the upgrade to 10.04 and that went fine. I'm not a huge fan of the IM service that is defaulted up near the session indicator (where you shut down/suspend/hibernate, etc). I avoid IM - it's irritating. So, I right clicked and hit "Remove From Panel". Imagine my surprise when my session indicator disappeared along with it. WTH?

I've got a session indicator back - along with that obnoxious IM applet that's apparently become an evil conjoined twin - but now it's hanging out in the middle of the upper panel and refuses to move back to where it should be. I's like to have my upper right corner icon back - any way to get it?

And bonus points if anyone can tell me how to get it back without IM linked.

---

### Post by Jon Monreal on 2010-05-05
To move the indicator-applet, try middle-clicking (or right-clicking and selecting "Move") the **small space** right to the left of the applet. You might need to uncheck "Lock to panel" first.

If you want the little mail icon gone entirely, you can type in a terminal
```
sudo apt-get remove indicator-messages
```and press enter.

If you mean the drop-down where you can select status, you can always remove that and then add the "Shut Down" applet where it used to be.

---

### Post by Temposs on 2010-05-05
You want to add "Indicator Applet Session" to the panel.

To move stuff on the panel, right click, choose Move. If you're unable to move something past other panel applets, or the applet you're trying to move has "Move" greyed out, that's because those have the option "Lock to Panel" checked. Uncheck the "Lock to Panel" option for all of the panel applets you're trying to rearrange so that everything is movable.

---

### Post by peculiar penguin on 2010-05-05
Uninstalling the "indicator-me" package and rebooting will nuke the IM/"social" status thingy.

---

### Post by Calash on 2010-05-05
indicator-messages removes the mail icon, not the MeMenu items (Picture at the top, set status under, entry field for broadcast at the bottom).

If you are looking to get rid of that type the following in the terminal

```

sudo apt-get remove indicator-me

```

Restart, or just remove and add the indicator-session applet to the panel.

---

### Post by ScottinSoCal on 2010-05-05
Excellent! It looks like all my questions are answered.

---

