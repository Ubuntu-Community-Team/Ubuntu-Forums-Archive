---
title: "problem with floola 9.10"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by pendulum101 on 2009-12-04
for some reason floola will not open. the only change that has been made to the system that could in my opinion have caused this problem is upgrading to karmic koala distribution 9.10. Does anyone have any input on this topic or are there any other people that are having this problem?

---

### Post by tgalati4 on 2009-12-04
I know it doesn't work on 64-bit Intrepid, but 32-bit Jaunty it works fine.  It's possible that there is a regression.  What is the output of the following:

dmesg | tail -50

Right after trying to open floola.

Also, open floola in the terminal by changing directory to the root of the ipod then type:

floola --debug

---

### Post by pendulum101 on 2009-12-09
> **tgalati4 said:**
> I know it doesn't work on 64-bit Intrepid, but 32-bit Jaunty it works fine.  It's possible that there is a regression.  What is the output of the following:

dmesg | tail -50

Right after trying to open floola.

Also, open floola in the terminal by changing directory to the root of the ipod then type:

floola --debug

one more point I forgot to make is that when i double click on the floola icon i don't get anything and im sure the dmesg | tail -50 doesn't give me anything that could be considered useful

---

### Post by tgalati4 on 2009-12-09
Run floola --debug in a terminal.  That told me that it couldn't execute in a 64-bit environment.  Perhaps floola is trying to load but fails.  It might show an error in the terminal.

---

### Post by pendulum101 on 2009-12-09
> **tgalati4 said:**
> Run floola --debug in a terminal.  That told me that it couldn't execute in a 64-bit environment.  Perhaps floola is trying to load but fails.  It might show an error in the terminal.

Nothing floola --debug just comes up command not found? I'm really stumped i cant make sense of why this happened although i feel as if its something to do with the new distribution. are you still running jaunty ?

---

### Post by tgalati4 on 2009-12-10
I've installed Karmic on a few client's machines, but I haven't put it on any of mine yet.  No regressions are possible on a new clients's machine.  Everything is both new and broken at the same time!

I've decided to wait for a more thoroughly-baked version--Lucid.

Floola was not found because you were probably not in the ipod directory.

cd /media
ls
cd ipod  (or whatever your ipod mount point is called)
ls  (verify that floola exists in root directory of the ipod)
floola --debug

Post the output of any useful messages.

---

### Post by neu5eeCh on 2010-01-02
I'm having the same problem with Floola. Double clicking does nothing.

Can it be executed (started up) without a mounted IPOD?

---

