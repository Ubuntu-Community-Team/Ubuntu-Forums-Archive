---
title: "Lost network manager applet."
date: 2007-08-16
forum: Networking &amp; Wireless
---

### Post by nickajeglin on 2007-08-16
I feel really dumb now, as I was using the network manager applet, but stupidly managed to remove it from my panel. Now it's lost and I can't for the life of me figure out how to get it back. I can still connect to all my networks just like normal. It's just that the nice little applet is gone, and I liked it better than the default gnome one. I tried "nm-applet --sm-disable" but it just sat there and didn't do anything until I just got tired of it's smug grin and ctrl+c'd it.

---

### Post by unisol on 2007-08-16
try this;  System > Preferences > Sessions

Under Startup Programs, check for Network Manager. If it's there, make sure it's checked off. If it's not there, you may need to re-add the entry:

1) Click New
2) Make name "Network Manager"
3) Make command "nm-applet --sm-disable"
4) Click OK
5) Hit Ctrl + Alt + Bksp to restart GNOME

---

### Post by nickajeglin on 2007-08-18
Nope, didn't do a thing. I also tried reinstalling the network-manager-gnome package, and I still see the default one.

---

### Post by joegiampaoli on 2007-08-18
Just right click on your taskbar, go to Add to panel>Network Monitor

---

### Post by nickajeglin on 2007-08-18
I don't want network monitor, I want network *manager*. And I still haven't been able to get it back.

---

### Post by joegiampaoli on 2007-08-18
Ok, try running in a shell either networkmanager NetworkManager or network-manager
I don't know the propper command for it but it's something like that. then log out or best reboot and I guess it should pop back in your taskbar, hope that helps.

---

### Post by nickajeglin on 2007-08-18
Hmm, that didn't work either. I looked in system>proferences>sessions>current session and nmapplet --smdisable has a question mark where all the others have gear wheels, Is this significant?

---

### Post by joegiampaoli on 2007-08-18
Well I have it exactly the same way as you do in there, by the way I do have the applet's icon on my tasbar, but mine seems not to be configured properly, sonce it says there is no network connection, although I do.

Check in System>Preferences>Sessions>Start Up Programs and make sure in that list you have "nm-applet --sm-disable" in the list, if you don't add it up and restart your session.

QUESTION: How do I configure my Network Manager?:confused:
(I just installed it to help you out a bit on this, but I would like to know more about it)

EDIT: Hmmm I think I just gave you the same tip as unisol did, and you said that didn't work either.....(thinking)

---

### Post by n0ctem on 2007-08-21
I had this same problem. Make sure you add "Notification Area" to your panel. That's where the applet shows up. And if more than one NetworkManager is open, just reset the xserver with Ctrl+Alt+Backspace.

---

### Post by lhtown on 2007-11-16
Thanks for the tip. I have used Ubuntu since Warty, and I have been scratching my head for a week over this.

Maybe we should lobby either Ubuntu or the Gnome people to make this a little less non-obvious.

---

### Post by nickajeglin on 2007-12-11
Wow, You're amazing! The notification area thing did it. That's sort of silly though. I had given up completely. Thanks!

---

### Post by drbusch on 2007-12-14
I think I have the same problem, but the notification area addition didn't solve it.  Further suggestions?

---

### Post by NilsE on 2007-12-14
> **drbusch said:**
> I think I have the same problem, but the notification area addition didn't solve it.  Further suggestions?
Make sure nm-applet (network manager) is in the Systems (preferences or Administration). If not you can add it by using nm-applet as the executable.

---

### Post by drbusch on 2007-12-14
> **NilsE said:**
> Make sure nm-applet (network manager) is in the Systems (preferences or Administration). If not you can add it by using nm-applet as the executable.

In System-Preferences-Sessions, I have nm-applet --sm-disable under startup programs.  Is this what you mean?

---

### Post by NilsE on 2007-12-14
> **drbusch said:**
> In System-Preferences-Sessions, I have nm-applet --sm-disable under startup programs.  Is this what you mean?
Yup, and it should be checked on.

Also, check in the current to make sure it is running.

---

### Post by drbusch on 2007-12-14
Yes, checked and in the current session.

---

### Post by ccezar2004 on 2007-12-20
i have this problem also... the thing is that all it is correct... and still nothing... i have the icon but not the speed.... this is pasted from a separate topic i have made 

*i made a new clean install of ubuntu on my dell xps m1710... i tried to make it like before... among other things i put back the network monitor in the upper panel... along with wether and system monitor... the thing is that before reinstalling the network monitor showed me near the little icon with the 2 computers also the speed of my connection with in and out... it was very good... but noe it only shows the icon... anyone knows why this happend?*

---

### Post by BattleKat on 2007-12-28
> **n0ctem said:**
> I had this same problem. Make sure you add "Notification Area" to your panel. That's where the applet shows up. And if more than one NetworkManager is open, just reset the xserver with Ctrl+Alt+Backspace.

OMG...I could kiss you!!!!!  I've been looking for days all over the place for a solution to my disappearing nm-applet.  Thank you sooooooooo much! :)

---

### Post by jlh on 2008-07-16
I too thank you for the Notification area fix.  I did a good deal of messing around to no avail before seeing this explanation.

---

