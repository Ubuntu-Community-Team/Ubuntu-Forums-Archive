---
title: "A couple of (very silly) novice questions"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by smratlif on 2010-06-26
I'm somewhat embarrassed to even ask this; but I've searched the forum and haven't seen what I'm looking for... a couple of naive questions:

1. How do I tell if I'm running the 32-bit or 64-bit version of Ubuntu? A "uname -a" shows "2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux"

2. Is there a way to get volume control back on the panel at the top of the screen? I think that went away when I upgraded to Ubuntu 10.04.

---

### Post by yeats on 2010-06-26
> **smratlif said:**
> I'm somewhat embarrassed to even ask this; but I've searched the forum and haven't seen what I'm looking for... a couple of naive questions:

1. How do I tell if I'm running the 32-bit or 64-bit version of Ubuntu? A "uname -a" shows "2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 22:02:19 UTC 2010 i686 GNU/Linux"

the "i686" part tells you that you are running 32-bit.  It would say something like "amd64" if you were running 64-bit.

> 2. Is there a way to get volume control back on the panel at the top of the screen? I think that went away when I upgraded to Ubuntu 10.04.

Have you tried just adding it back with a right click -> Add to panel... ?

---

### Post by WinterRain on 2010-06-26
> **smratlif said:**
> 
2. Is there a way to get volume control back on the panel at the top of the screen? I think that went away when I upgraded to Ubuntu 10.04.

Though it won't be a typical volume control, just go to system-preferences and drag the sound menu to the panel. I'm not sure how to get the original one back.

---

### Post by techunit on 2010-06-26
You appear to be running a 32bit version of ubuntu

---

### Post by techunit on 2010-06-26
If there are alot of issues with the panels or other parts of the user interface that were caused by the upgrade reseting gnome could help. If you upgrade the gnome folders can be messed up because of changes in the software used. Here is a video that I put together to fix problems with gnome. 

[http://ubuntuvideotutorials.wordpress.com/2010/06/22/reset-ubuntus-appearence/](http://ubuntuvideotutorials.wordpress.com/2010/06/22/reset-ubuntus-appearence/)

Note: If you did a clean install don't do this because it isn't you best bet you probably can fix it by finding the missing applet in the add and remove applets thing on the panel. I only recommend this for people who really mess up and it is less trouble to do this than having to try to remember which applet goes where. Or those who upgraded.

---

### Post by Rubi1200 on 2010-06-26
Hi,
there is no such thing as a silly question here. Questions are how we learn and then help others when we see they have similar problems.

Regarding the applet, you might want to try this which will reset the panels to their original defaults:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by smratlif on 2010-06-26
Thanks, everyone!   I have tried the right-click and "Add to Panel" for adding the volume control; it's not listed as an option (though things I would consider pretty exotic, like "Dwell Click", are). I'll try some of the suggestions listed above.

---

### Post by smratlif on 2010-06-26
> **Rubi1200 said:**
> 
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```


That did it! Thanks!

---

### Post by da burger on 2010-06-26
Just so you know for the future volume control is in "indicator applet" which is one applet that holds a lot of others.

Also please mark this thread solved if it is.

---

