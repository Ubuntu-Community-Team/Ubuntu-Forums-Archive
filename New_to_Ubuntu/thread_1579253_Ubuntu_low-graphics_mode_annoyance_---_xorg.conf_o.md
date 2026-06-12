---
title: "Ubuntu low-graphics mode annoyance --- xorg.conf outdated"
date: 2010-09-21
forum: New to Ubuntu
---

### Post by Gameboyman99 on 2010-09-21
Hi guys,
I recently messed up my xorg.conf file, now whenever I start up Ubuntu it says something like this:
```
WARNING: Ubuntu is running in low-graphics mode
Some-junk blahblah i cant remember
Error: No (ee)devices found(I think...)
(OK button)
``` Then:
```
(Radio buttons)
icantremember
icantremember
Troubleshoot the error
icantremember sorry
Restart X
```And I choose **Restart X** and it restarts something, but not my whole computer, my screen says **Out of scan range: somedimension and icantrememberagain**
Then it goes away and Ubuntu runs fine... Something to do with xorg.conf not updated and/or driver problems.(I also have a 2nd monitor plugged in, but I haven't taken it out yet, I'll try that)
[B]But the error is incredibly annoying!
[/B]Thx,
[HTML]<hr />[/HTML]
Hey...??^^^^^^^^ HTML stupidity or wut is wrong thr??
 [FONT=Comic Sans MS][SIZE=2][COLOR=DarkOrange]Gameboyman99[/COLOR][/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-09-21
Delete or move the file and try again.

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.broken
```

---

### Post by Gameboyman99 on 2010-09-21
Oh, Wow, thanks bodhi.zazen!! Gr8 :)
Thank you again,
  [FONT=Comic Sans MS][SIZE=2][COLOR=DarkOrange]Gameboyman99[/COLOR][/SIZE][/FONT]

---

### Post by bodhi.zazen on 2010-09-21
> **Gameboyman99 said:**
> Oh, Wow, thanks bodhi.zazen!! Gr8 :)
Thank you again,
  [FONT=Comic Sans MS][SIZE=2][COLOR=DarkOrange]Gameboyman99[/COLOR][/SIZE][/FONT]

No problem, it is easy to over look that "fix" in the middle of a crisis.

---

