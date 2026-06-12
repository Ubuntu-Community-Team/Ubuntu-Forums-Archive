---
title: "[SOLVED] Tunnelling X11 apps to another box"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by Pro-reason on 2008-08-19
OK, I've finally decided to network mine and my wife's computer together (after being frustrated with Windows networking in the past).

I've used NFS to share files between the two.  It works perfectly.  By setting up appropriate user accounts on each other's machines, and making the appropriate home directories point to the appropriate home directory on the other machine, it is now possible for us to log on to either machine with either username/password combination, and have all the right user settings.

The next step is to truly log on to a remote computer (not just by sharing files).  To do this, I've set up SSH.  It works fine.  From my machine, I can SSH to my wife's machine and execute commands.  No need to explain what software she needs to install to do something: I can simply do the "sudo apt-get" for her myself.  I can type "eject" to open her CD drive.

[B]There is only one problem.  If I send a graphical command such as "linpopup" or "display", the X11 app opens up on *my* end, not hers.  That could be useful for some administrative purposes, but not for what I have in mind.

How can I make X11 applications send their output to the other box?[/B]

(Bonus question: how can I see what is happening on the screen of another computer?)

Edit: ah, putting "DISPLAY=:0.0" in front of the command seems to successfully send it to the remote computer.  I think that VNC is what I need for taking over a desktop completely.

---

