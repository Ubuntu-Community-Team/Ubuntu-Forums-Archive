---
title: "remote desktop connects but !"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by digitography on 2010-12-23
This is a strange problem.
I have setup a remote desktop connection, System, Preferences, Remote desktop.
I use Remote desktop viewer to connect.
Connects, however I only see a snapshot of the remote machine at the  moment I connect. I have control of the remote machine (I know this  because I setup the remote computer across the room so I could see it),  but the display in vinaigre  does not update. I do not have the "View only" box checked.
If I try to refresh the view, the session closes!
All computers I have tested this on are running 10.10, they are all bang up to date with updates.
I have tried this on several different computers all with the same result.

Anyone any idea why?
and how do I fix it?

---

### Post by Verbeck on 2010-12-23
could you try disabling the desktop effects

---

### Post by digitography on 2010-12-23
Verbeck: thank you so much, I thought I was losing my mind.
I'll mark the thread as solved so others can benefit from this.
Now all I need to do is figure out how to do this with PPTP.

---

### Post by digitography on 2011-08-23
OK so this was solved in 10.10 by turning off the visual effects.
Now I have one machine running 11.04, once more I can connect, but I never get to see what's happening on the remote machine. So I thought turn off the visual effects, and that is where the problem started. Where the heck has the visual effects tab gone? Has it been moved, or is it no longer available? 
help as always appreciated.

---

### Post by davidcampbell on 2011-08-31
I'm having the same problem. Remote desktop worked fine before i installed ati fglrx drivers. After that I have the exact same issue. Connecting works, i get a snapshot and I can control the computer but the snapshot never changes..

Any one got a solution for this?

---

### Post by davidcampbell on 2011-08-31
I'm gonna go ahead and answer my own question. Found the solution on another thread..

1) Open a gconf-editor from a terminal
2) and then go to /desktop/gnome/remote_access and enable "disable_xdamage"

ref: [http://ubuntuforums.org/showthread.php?t=1735979](http://ubuntuforums.org/showthread.php?t=1735979)

---

### Post by Legendary_Bibo on 2011-09-01
You'll have to use Unity 2D. It has compiz on by default on 11.04

---

