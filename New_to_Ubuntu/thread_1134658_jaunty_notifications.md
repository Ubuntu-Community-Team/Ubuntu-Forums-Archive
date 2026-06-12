---
title: "jaunty notifications"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-04-23
small problem...

jaunty notifications are appearing on the top-right corner of my second monitor. I want to move it to my main monitor...

any thoughts?

---

### Post by Didius Falco on 2009-04-23
A slashdot user, CrispBH, said:

> ...change their positioning via gconf-editor...  

I haven't tried it, I just remembered seeing it. It'd be nice to know if/how it works, though.

---

### Post by abhiroopb on 2009-04-23
How would i change it? I know how to use gconf-editor but there are a lot of options there!

---

### Post by duanedesign on 2009-04-23
you can R-click in the top Gnome panel and select Add to panel. Then select the Notification Area item to add to the panel. This creates a little divider looking icon in the panel that you can move around. Then delete the other one.

Just a suggestion, I have never messed around with dual monitors.

Good luck.

---

### Post by abhiroopb on 2009-04-23
This basically created a little notification icon on my panel, however, the new ubuntu notigications thing is still appearing on my second monitor.

---

### Post by duanedesign on 2009-04-23
ok did some more digging.

Check out this bug report. 

[https://bugs.launchpad.net/ubuntu/jaunty/+source/notify-osd/+bug/331369](https://bugs.launchpad.net/ubuntu/jaunty/+source/notify-osd/+bug/331369)

According to the bug it is marked fix released as of notify-osd 0.9.8 but as you can see some people still have issues. I didnt read all of it but one workaround seemed to be to remove the panel from the secondary monitor. I dont know if that is an option or not. Read all the comments on the bug report. If after reading them and trying any solutions that are provided you still have a problem add a comment to this bug.

Good Luck


Edit: There is mention of this smart mode that puts notifications on the monitor that contains the window that is active:

"Considering that multihead support is generally a setup for advanced users, we've also added a gconf key to enable a smarter mode. To enable it, you need to set "/apps/notify-osd/multihead_mode" to "focus-follow".

In this mode, the notifications will be displayed on the screen that contains the active window, and if none exists (if ever that can happen), then it will be displayed on the monitor that contains the mouse pointer."

---

### Post by abhiroopb on 2009-04-23
ok so I fixed it...thanks for the link...basically my panel is on the bottom and for some strange reason moving it to the top makes the notifications appear on the main screen.

THANKS!

---

