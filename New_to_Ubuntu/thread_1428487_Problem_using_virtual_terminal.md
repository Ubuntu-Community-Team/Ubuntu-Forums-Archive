---
title: "Problem using virtual terminal"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by SteelCore on 2010-03-12
I'm using an LG S1 laptop. Whenever I switch to one of the 6 virtual terminals (ctrl+Alt+[F1-F6]) and switch back to the GuI (Alt+F7) I get the screen back for around a second and then the system sleeps (as if hybernating). It resumes after I press the power-on button of the laptop. I don't face this issue with my PC, (also 9.10).
What is the package name so I can report this with ubuntu-bug? or is there a better way to report this issue?
Thanks

---

### Post by spiderbatdad on 2010-03-12
great question. Wish I knew for sure.
I launched  tty1 then back and looked at daemon.log. It says acpid.

---

### Post by Rocket2DMn on 2010-03-12
SteelCore, I think you should file a bug against the *linux* package, which is for the kernel.  Using ubuntu-bug is the best way, since it automatically attaches relevant info to the bug report.  They will likely ask you to test with Lucid as well, which you should be able to do from a LiveCD.

---

### Post by SteelCore on 2010-03-12
> **Rocket2DMn said:**
> SteelCore, I think you should file a bug against the *linux* package, which is for the kernel.

I just ran
```
ubuntu-bug linux
```
then a window came up asking to send the report and I got the 'cannot connect' notice (attached). I am connected, using my laptop to send this reply.

---

### Post by Rocket2DMn on 2010-03-12
Weird, I just tested and got the same error.  It could be the Launchpad's database is down for the moment.  I would try again in awhile, seeing as the problem is not at your end.

---

### Post by SteelCore on 2010-03-15
I've tried it several times in the past 2 days and still can't connect.

---

### Post by Rocket2DMn on 2010-03-16
SteelCore, I was also able to reproduce the problem for a few days - see bug [lpbug]538097[/lpbug].  It should be working now, I'm able to connect.

---

