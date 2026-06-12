---
title: "Your session only lasted less than 10 seconds."
date: 2008-12-06
forum: New to Ubuntu
---

### Post by phanleson on 2008-12-06
Twice, in the past week, I've been unable to log-in and get the message
Your session only lasted less than 10 seconds. If you have not logged yourself out, this could mean that there is some installation problem or that you may be out of disk space. Try logging in with one of the fail-safe sessions to see if you can fix this problem

Detail :

> 
/etc/gdm/Xsession:Beginning session setup……
/etc/profile: 26: id: not found
[:26:Illegal number
/etc/gdm/Xsession:178:grep:not found
/etc/gdm/Xsession:192 ls: not found
/etc/gdm/Xsession Executing default failed,will try exec:205 x-termial-emulator:not found 

If you had a solution with this problem , please send to me with email address : [email]phanleson@gmail.com[/email]
thank you very much !
:popcorn:

---

### Post by cmnorton on 2008-12-09
This usually happens the next time you log in, after you have just logged in and then back out this time.

---

### Post by Infinite Indefinite on 2009-02-19
I had this problem as well when I updated from Gutsy to Hardy.

It evaporated once I removed xgl.

---

