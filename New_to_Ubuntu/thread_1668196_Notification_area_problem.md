---
title: "Notification area problem"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by rs87424 on 2011-01-16
I turned off the notification for rhythmbox and now I want to turn off the notification for internet network discovery/disconnect. I can't find a menu or any place to turn it off. I found a box that said "turn off notification" and I unchecked it...but that didn't work

---

### Post by Perfect Storm on 2011-01-16
Try with logout and then login and see if it takes affect.

---

### Post by rs87424 on 2011-01-16
doesn't work for some reason

---

### Post by Perfect Storm on 2011-01-16
hmm....I think the enable/Disable option in the network applet is for the pop-up that comes if there's some changes taking place. Not for removing network from the Notification area.

---

### Post by rs87424 on 2011-01-16
well yeah... but for some reason when I uncheck the box the pop up still shows up. I am trying to remove the pop up

---

### Post by Perfect Storm on 2011-01-16
Ah, I thought you want to remove the network applet from the notification area, my bad.


Try this:

```
gconf-editor
```

apps ---> nm-applet

and disable the desired notifications. (may need a logout).

---

### Post by rs87424 on 2011-01-16
oh ok thanks that works

---

### Post by rs87424 on 2011-01-16
you know... actually... unchecked everything I didn't want in the boxed for the gconf editor and it *still* seems to be popping up anyways. very strange

---

### Post by rs87424 on 2011-01-16
it seems everytime I uncheck the boxes in gconf editor the "enable notifications" box is checked. I like the application but I just don't like the pop ups

---

### Post by Perfect Storm on 2011-01-16
I found this: [http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/](http://www.killertechtips.com/2009/04/26/disable-notifications-in-ubuntu-904-jaunty-jackalope/)

(use it at your own risk)

---

