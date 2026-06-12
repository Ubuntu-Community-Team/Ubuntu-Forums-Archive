---
title: "2 Speaker in Notifications Panel instead of 1"
date: 2010-04-23
forum: New to Ubuntu
---

### Post by OneLine on 2010-04-23
Hi, for some reason there appears to be 2 speakers in the panel instead of 1, nothing happens when I click on the first speaker, the second speaker is fine when I click on it. I've just noticed it. Have I done something wrong?

[IMG]http://j.imagehost.org/0596/Screenshot.png[/IMG]

Thank You.

---

### Post by OneLine on 2010-04-23
> **OneLine said:**
> Hi, for some reason there appears to be 2 speakers in the panel instead of 1, nothing happens when I click on the first speaker, the second speaker is fine when I click on it. I've just noticed it. Have I done something wrong?

[IMG]http://j.imagehost.org/0596/Screenshot.png[/IMG]

Thank You.

It's ok now, after a restart it appears to have fixed itself as only 1 speaker is in the notification bar now. Thank You.

---

### Post by lotharmat on 2010-04-23
I get similar behaviour occasionally.

Instead of re-booting, you can right click on the applet and remove it from the panel and then re-add it. It comes back fine!

---

### Post by mikodo on 2010-04-23
> **lotharmat said:**
> I get similar behaviour occasionally.

Instead of re-booting, you can right click on the applet and remove it from the panel and then re-add it. It comes back fine!
If I can chime in here...Strange; for me I can delete all other applets except the sound one by right clicking. Early in my Karmic install I deleted the panel mistakenly, and had to add all the applets manually, maybe that has something to do with it??

Right click just gives me the mute and preferences options.

No worries, as I just have the one applet though.

---

### Post by Grenage on 2010-04-23
There is a bug in there somewhere, but it's not a very serious one (for me).  Every time I open a new app with a bar applet, it initially loads with the image of whatever the last applet was (usually xchat or the volume control).  99 out of 100 times, it loads the correct image within 2 seconds.

This happens on all my Ubuntu installs.

---

### Post by mcduck on 2010-04-23
> **mikodo said:**
> If I can chime in here...Strange; for me I can delete all other applets except the sound one by right clicking. Early in my Karmic install I deleted the panel mistakenly, and had to add all the applets manually, maybe that has something to do with it??

Right click just gives me the mute and preferences options.

No worries, as I just have the one applet though.

That's because the sound is icon is not an applet, it's a notification icon.. So, to move/remove it you need to move the Notification Area-applet (notice the barely visible handle right to the left of the sound icon, that's what allows you to move the Notification Area-applet and access it's right-click menu.)

---

### Post by mikodo on 2010-04-23
> **mcduck said:**
> That's because the sound is icon is not an applet, it's a notification icon.. So, to move/remove it you need to move the Notification Area-applet (notice the barely visible handle right to the left of the sound icon, that's what allows you to move the Notification Area-applet and access it's right-click menu.)
Thanks!

Mike

---

### Post by mcduck on 2010-04-23
No problem. And, by the way, even quicker way that usually fixes buggy applets and notification icons is to simply reload the panel. Just hit Alt-F2 and run "killall gnome-panel" to kill the panel, and it will automatically spawn back again.

I had the same bug a couple of times in Ubuntu 9.10 and restarting the panel fixed it every time.

---

