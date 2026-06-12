---
title: "Unable to resolve hostname ?"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Julian David Pitt on 2008-06-21
Every time I run a terminal I receive the error "Unable to resolve hostname", can anyone tell me how to fix this please. Many thanks.

---

### Post by molotov00 on 2008-06-21
use google. this is a well documented error with an easy fix. i'm not going to tell you here because you're so bloody lazy.

---

### Post by superprash2003 on 2008-06-21
> use google. this is a well documented error with an easy fix. i'm not going to tell you here because you're so bloody lazy.
Thats not how you answer mate!!He has his question and if you are interested in giving the solution then please do, otherwise just ignore the thread!!
  @Julian David Pitt
   is that pc connected to the internet? are you trying to ping a website?

---

### Post by molotov00 on 2008-06-21
> **superprash2003 said:**
> Thats not how you answer mate!!He has his question and if you are interested in giving the solution then please do, otherwise just ignore the thread!!
  @Julian David Pitt
   is that pc connected to the internet? are you trying to ping a website?

Point taken. But here's why I'm irritated. It's a vague question. Plus, he clearly didn't try searching.

Solution (based on your vague question):

Check /etc/hosts

> Tested with todays hardy and found the same problem.

I added the DNS domain using Network Manager Applet and after that sudo won't work.

[in /etc/hosts]

Original:
127.0.1.1 ubuntu

After Network Manager:
127.0.1.1 ubuntu.test.com

sudo: unable to resolve host ubuntu

Source:
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/195308)

---

### Post by superprash2003 on 2008-06-22
There you go!!Good to see you answer..Your doing a good job..and yes Julian David Pitt was a bit vague with his question.But it would have better if you would have asked to be more clear in a better way!!cheers :D

---

