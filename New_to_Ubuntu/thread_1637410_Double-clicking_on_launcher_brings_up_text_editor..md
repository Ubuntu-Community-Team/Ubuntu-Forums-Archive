---
title: "Double-clicking on launcher brings up text editor...?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Defrector on 2010-12-04
I've been making application launchers on my Xfce desktop but they just bring up Mousepad to view the .desktop file. I tried chmod +x of the .desktop file (maybe it was a security thing?) but it doesn't appear to fix the issue.


How do I make the application launchers launch applications when double-clicked?

---

### Post by MooPi on 2010-12-04
Can you copy and paste the contents of one of the offending .desktop files for review ? We may be able to spot a reason for the failed launch.

---

### Post by Defrector on 2010-12-05
While trying to create a simplified test-case I think I may have found the problem. 

When using the dialog [right click on desktop]->Create Launcher->Command Textfield->[File Selection Dialog] and selecting an application whose path contains a space, the launch fails and launches Mousepad.

The obvious workaround would be to use a path without spaces...

I found a bug report regarding the matter. Perhaps it will be fixed soon.

[https://bugs.launchpad.net/libxfce4menu/+bug/388095](https://bugs.launchpad.net/libxfce4menu/+bug/388095)

---

