---
title: "task bar"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by godsmAsh on 2011-04-30
hi, 
 i've just upgraded to Ubuntu 11.04 and an having trouble about the task bar. actually, i can't see my task bar( the bar containing the option places, admin..) only my wall paper is being displayed. i've upload a print screen image. can someone please help me.

---

### Post by AndyM3 on 2011-04-30
Did you try restarting X? Hit Ctrl-Alt-F1, log in on the console and type:
```
sudo service gdm restart
```
If Unity still doesn't load, try picking "Ubuntu Classic" (or something to that effect) from the login screen's session list (it should be at the bottom of the screen).

---

### Post by godsmAsh on 2011-05-02
thanks for the reply but i've installed unity 2D

---

