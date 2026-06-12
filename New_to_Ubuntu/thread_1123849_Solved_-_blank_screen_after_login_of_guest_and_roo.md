---
title: "Solved - blank screen after login of guest and root accounts"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by stevemu on 2009-04-12
I can login fine to my normal account.  When I try to login to either guest or root accounts I get a blank, light brown screen after the password and then nothing happens.  I've left it for 30 mins or more and still nothing.

---

### Post by stevemu on 2009-04-12
Well I looked around and found the advice to run the following commands in another thread with a similar problem.  I did so and the problem is now fixed.  Thinking about it I changed my graphics card a while back and this was the first time I tried logging into any other account since then.  So I guess it had something to do with that.

sudo apt-get remove compiz
sudo apt-get remove compiz-core

---

### Post by Sef on 2009-04-12
Thank you for posting the solution which worked for you.

---

