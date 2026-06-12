---
title: "System Stuck?"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by cat2005 on 2009-08-17
I was in synaptic downloading / installing KDE (needed it for k3b) and left.  When I came back, my screen saver was running.  I moved the mouse to make the screen saver disappear and the password prompt appear.  The moving screen saver moved just a little more, then froze.

I can't get into that computer.  If I physically restart it, could I cause damage / file loss / etc?

Other than physically restarting, do I have any options?

---

### Post by marshmallow1304 on 2009-08-17
Ctrl+Alt+F1

If this works, you should see a prompt on a black screen.  Login using your regular login/password, then type:
```
sudo /etc/init.d/gdm restart
```
Enter password again.

---

### Post by jakupl on 2009-08-17
first try to press ctrl + alt + f2, if it works than you can login on the command line and write ```
sudo shutdown -P now
```

If this does not work, try to hold Alt + Sys Rq and while holding these buttons, press R E I S U B with like 5 seconds between each. if the computer does not reboot, then do a hard reboot.

It can do bad stuff, but we will figure that out when your computer is back on.

---

### Post by colau on 2009-08-17
> **jakupl said:**
> first try to press ctrl + alt + f2, if it works than you can login on the command line and write ```
sudo shutdown -P now
```

If this does not work, try to hold Alt + Sys Rq and while holding these buttons, press R E I S U B with like 5 seconds between each. if the computer does not reboot, then do a hard reboot.

It can do bad stuff, but we will figure that out when your computer is back on.
R E I S U B are similar to r e i s u b ?

---

### Post by jakupl on 2009-08-17
> **colau said:**
> R E I S U B are similar to r e i s u b ?

yes.

---

### Post by cat2005 on 2009-08-18
I tried the following:

1)  ctl + alt + del   (no result)
2)  ctl + alt + bkspace  (no result)
3)  alt + sysrq (prtscrn) + k  (worked)

If anyone else runs into this problem, then give these a try.  I got them here (which lists more stuff):

[http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=19672](http://www.cdrinfo.com/Sections/Reviews/Specific.aspx?ArticleId=19672)

---

