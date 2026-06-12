---
title: "Having issues with graphics - artifacts in panels"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by sw4383 on 2010-06-30
I'm using Ubuntu 10.04 on an Acer Aspire x1300 - I'm running the 32-bit version of the OS for what it is worth.  

The problem that I'm having, after I enable the nVidia drivers, is that I will have artifacts on the Gnome panels upon login.  Sometimes the username in the upper right-hand corner will be super-imposed over itself which restricts functionality of the buttons - even to the point I cannot use GUI to shut down the PC.  Sometimes in the lower left-hand corner I will have a white rectangle running parallel to the "show desktop" button on the bottom panel.  If I terminate the panels and restore them the issues are gone.  I can also log out and log back in and this will at times fix the issue.  I have tried taking desktop effects from none to normal to high.  Eventually the problem comes back.  

I am running the suggested driver for my device, and this phenomena happens whether I'm running a clean install or after having updated the system with the latest packages.  Is there a fix for this?  I would much rather learn how to diagnose and trouble-shoot this than just be directed to a site that says copy this code and paste it into terminal.  

Perhaps I'm phrasing my question differently than most and this has been discussed a thousand times over. (The search for related posts tool didn't come up with an exact match)  For that I am sorry.  As I am writing this I am away from my machine so I won't be able to provide you with immediate feedback on anything I try.  If this has been discussed and solved, I would appreciate a link to the article.  Then for that point if the thread needs to be moved / locked / deleted the moderators can do so.

---

### Post by Rybandt on 2010-06-30
I thinkI have the same problem. After upgrading i rebooted and my computer didn't work. It just flashed something that looked like my login over and over and I have to REIUB it. Is this what you are experiencing? I have bookmarked tons of articles on this to see if any help. I'm through half of them with no such luck yet. Including over 10 different installs from 8.04 to 10.04... :confused:
 
Let me know if this is the same problem you are having!

---

### Post by eriktheblu on 2010-06-30
Sounds similar to issues I was having with my Intel card on my laptop.

I have no reason to believe this will work with an Nvidia chip, but my solution was to add ```
Option "MigrationHeuristic" "greedy"
``` to /etc/X11/xorg.conf

---

### Post by cloyd on 2010-06-30
Does your pointer ever turn into a white rectangle, maybe changing back to normal, maybe not? Do parts of the screen scramble with lines showing up? This was my problem:
[http://ubuntuforums.org/showthread.php?t=1518658](http://ubuntuforums.org/showthread.php?t=1518658)

The solution was here:
[http://news.softpedia.com/news/How-t...4-140810.shtml](http://news.softpedia.com/news/How-t...4-140810.shtml)

The first offered solution is longer. It is the one that worked. Don't know that this is your problem, but mine would work fine for a while, and then graphics would get screwy.

---

