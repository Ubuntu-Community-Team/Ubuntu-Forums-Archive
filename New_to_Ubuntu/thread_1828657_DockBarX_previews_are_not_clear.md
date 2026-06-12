---
title: "DockBarX previews are not clear"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by ENigma885 on 2011-08-19
I have just upgraded from Maverick to Natty. After the upgrade I updated my PPA's to the Natty ones. DockBarX was one of these applications updated but after it has been updated the window previews looked pretty unclear as if the preview tooltip is covering the previewed window.

Is there any way to bring it up again?
[[IMG]http://img17.imageshack.us/img17/9491/dockbarx.png[/IMG]](http://imageshack.us/photo/my-images/17/dockbarx.png/)

Notes:
- DockBarX is installed using Webup8's PPA and it was working pretty well before the upgrade to Natty. Its version is 0.46 in both Maverick and Natty.
- I have tried many DBX themes but none corrected the preview issue.
- Also tried to run it as a standalone dock, through dockx, but the problems persisted.

---

### Post by M7S on 2011-08-19
It's a known bug in compiz 0.9.x. To fix it you have to downgrade compiz to 0.8.6 (google is your friend). A workround is to set dockbarx window list color to something more transparent.

---

### Post by ENigma885 on 2011-08-21
Thanks, M7S
I have actually purged 0.9.4 and compiled [COLOR="Red"]0.8.8[/COLOR] instead. Now, DockBarX is working pretty much as intended and I have to be honest, the overall Compiz performance has improved a lot.

---

