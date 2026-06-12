---
title: "error message re. nautilus"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by Ruffed Grouse on 2009-03-01
Hi!

This is my first post on this forum.  

I have never used any Linux before.  I got ubuntu 8.10 installed yesterday and worked my way through getting it to recognize drivers etc.  Today I am getting a message on startup about:

Nautilus cannot be used now, due to an unexpected error.
show more details:
Nautilus cannot be used now, due to an unexpected error from Bonobo when attempting to locate the factory. Killing bonobo-activation-server and restarting Nautilus may help fix the problem.

I don't know how to kill bonobo, nor do I know what bonobo is, and so I don't know if I really want to kill it.  But I would like to have nautilus working properly.

All help much appreciated,

RG

<><

---

### Post by Ruffed Grouse on 2009-03-01
This problem first came up after I had edited my xorg.conf file in efforts to reduce the sensitivity of my computer's touch pad, and it persisted even when I restarted X.  But after a full reboot it seems to have gone away.  But as the error message may still indicate some problem, I would still like any advice on it that you can provide.

So on a related note - any advice on reducing my touchpad's sensitivity?  The computer is a compaq cq50-106 CA.

Thanks

RG

<><

---

### Post by chrisod on 2009-03-01
First restore your original xorg.conf. You did make a back up before you started mucking about, right?

Then go to system-->preferences-->mouse and disable "enable mouseclicks with touchpad." I found that feature to be the source of all my touchpad issues.

---

