---
title: "Volume Control Slider Missing from Top Panel"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by lkraemer on 2010-09-30
Running 10.04 LTS, and this morning my Volume Control Slider is missing
from the Top Right Panel (usually is right beside the Wifi Icon) for
no reason.  It was present last night.

How can I add it back?  It isn't available when I edit the Panel to add
it back to the Top Menu.  WHY?

The Email (Letter) Icon for (setting up email, chat, broadcast account) is also missing.  

lk

---

### Post by bbqsandwich on 2010-09-30
Try right-clicking the panel and adding the Notification Area applet; see if that helps.

---

### Post by lkraemer on 2010-09-30
I removed the Notification Area applet, then added it back.  I just
have the Wifi Icon there.....nothing else, except when running on
battery, it is displayed.  Still no volume control slider.

lk

---

### Post by robbiemacg on 2010-09-30
Take a look at these two threads:
[http://georgia.ubuntuforums.org/showthread.php?t=1517390](http://georgia.ubuntuforums.org/showthread.php?t=1517390)
[http://newyork.ubuntuforums.org/showthread.php?t=1324510](http://newyork.ubuntuforums.org/showthread.php?t=1324510)

I think you'll find something useful.
Good luck, bud.

---

### Post by lkraemer on 2010-09-30
robbiemacg,
I tried those url's and commands, and still no Volume Slider for control.

lk

---

### Post by robbiemacg on 2010-09-30
Have you tried adding the Indicator Applet to your panel?
In more recent releases that's what allows you to access bluetooth, check battery/power settings, sound settings, connect to mail/chat from your Gnome Panel.

---

### Post by andrewthomas on 2010-10-01
Just restore to the default panel.  All you will lose is your customization
 
```
 
rm -r ~/.gconf/apps/panel

```
 
Then log-out and back in.

---

### Post by lkraemer on 2010-10-01
andrewthomas,
THANKS........that did it.  I have my Volume Slider back along with
the Letter Icon for setting up Mail, Chat & Broadcast Account.

I was just about ready to re-install.

I still have the problem with an error message when I boot:
ERROR CAN'T MOUNT STATIC.......I wish you could fix that one...

lk

---

### Post by andrewthomas on 2010-10-01
Post the full error message.

---

### Post by lkraemer on 2010-10-01
andrewthomas,
Here is the url to the posting:
[http://ubuntuforums.org/showthread.php?t=1577481](http://ubuntuforums.org/showthread.php?t=1577481)

After trying to get my Floppy to mount on Ubuntu 10.04, I have started getting the following Error Message:
"An Error Occured While Mounting Static"
"Press S to skip mounting, or M for Manual Recovery."

Maybe you will have an idea.

lk

---

