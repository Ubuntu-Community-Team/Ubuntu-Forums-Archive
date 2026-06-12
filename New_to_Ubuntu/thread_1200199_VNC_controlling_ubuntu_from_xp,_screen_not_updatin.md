---
title: "VNC controlling ubuntu from xp, screen not updating?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by spacesearcher on 2009-06-29
Hello,

I am trying to be able to remote connect to my Ubuntu laptop from a machine with Windows XP.

I installed ssh on the Ubuntu laptop (sudo apt-get install ssh)
then on the xp machine I used putty and was able to get a ssh window open and I could run commands from that window. then i started tightvnc on my xp machine put in my ip and password and it loaded the initial screen but nothing else after that. When I type or move the mouse on the xp machine it types and moves the mouse on the Ubuntu box. It just won't update the screen on the vnc viewer. When I click refresh screen in tightvnc the Ubuntu machine sends a couple megabytes of stuff through the network but the screen still won't update in the vnc viewer.  The same thing is happening in ultravnc. I am just using the default settings for everything.

Is there something I am not doing correctly? Does anyone know how to fix it?

---

### Post by XCan on 2009-06-30
Unfortunately, vnc is totally broken in Jaunty when used with compiz. There are no good fixes for this. The workaround that sucks the least is to turn off visual effects. Another workaround that sucks more relates to run vnc server with the noxdamage flag, which makes it really slow since the whole screen is updated. See [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126) .

---

### Post by spacesearcher on 2009-07-01
That's really aggravating oh well at least it has a really active bug report hopefully it will be fixed soon. Thanks for the reply and the link to the bug.

---

### Post by XCan on 2009-07-01
No problems. However, it seems like the chances of this being fixed for Karmic is slim. The devs are not really prioritizing this, and so far people say the same issue arises in Karmic. I too hope this would be fixed soon, no matter whether one likes vnc or not, having such important feature as remote desktop broken by default just doesn't scream user friendliness. :p

---

### Post by QIII on 2009-07-01
You can temporarily switch to Metacity to use VNC, which is what I have to do in both Jaunty and Karmic.

See post #9 here:

[http://ubuntuforums.org/showthread.php?t=1199020](http://ubuntuforums.org/showthread.php?t=1199020)

---

### Post by XCan on 2009-07-01
> **QIII said:**
> You can temporarily switch to Metacity to use VNC, which is what I have to do in both Jaunty and Karmic.

See post #9 here:

[http://ubuntuforums.org/showthread.php?t=1199020](http://ubuntuforums.org/showthread.php?t=1199020)

Which of course is the workaround that sucks the least. If you use workspaces extensively, be prepared that it will put all windows into one single workspace.

---

