---
title: "I made a BIG ut-oh, closed installer script"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by designateduser on 2009-08-12
So I was trying to install some webcam software package, and after the "terminal" view and the loading bar had not changed in a while, I decided, like the idiot I sometimes am, to try and re-start it and so I closed the installation #-o. After trying to re-start the package installer I found that the original installer was still running somewhere! I logged out and logged back in and it was STILL RUNNING. I turned off my computer and re-started Ubuntu Jaunty and I am still not able to run any installers or software management. How can I close that origninal script! any insight is much appreciated.

---

### Post by alexlafreniere on 2009-08-12
Usually if you just let whatever process is running just sit for a while it will crash itself out. If you haven't gotten the crash reporter applet showing up in your panel, try issuing the ```
top
``` command in the terminal and see if there is a process named similar to what you are looking for. If you find it, issue ```
killall <processName>
``` then reboot for good measure. You should be fine after that. If the installer left some stray files around your drive, find and delete them and start from the beginning.

---

