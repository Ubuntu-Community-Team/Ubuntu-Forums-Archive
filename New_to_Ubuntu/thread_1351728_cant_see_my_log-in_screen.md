---
title: "cant see my log-in screen"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by mis-understood on 2009-12-10
I recently upgraded from 8.04 to 9.10 after which i restarted my system,it re-booted and the screen went blank i cant see the log-in menu and my numbers,caps & scroll lock keeps blinking 
can anyone help:(
i tried recovery mode it doesnt help,i cant get on my computer help somebody

---

### Post by radiocognition on 2009-12-11
Can you see any text or expecially error messages during boot up.  Providing instances of specific errors would be helpful in diagnosing your problem.  If you can get to a black command prompt screen that asks for your login username, try to get access with your username and password. Then issue the command

```

sudo /etc/init.d/gdm restart

```

---

### Post by Geoff918 on 2009-12-11
Do you have a LiveCD? That might be the best first step.

Also, how did you do the upgrade? The upgrade path from 8.04 to 9.10 is not a one-shot move. It would force you through another upgrade path, I believe (at least from my experience)-->8.04 -> 8.10 -> 9.04 -> 9.10?

Did you put in the repos and try a direct upgrade?

---

### Post by mis-understood on 2009-12-11
I upgraded from 8.04 >8.10>9.10.
i upgraded from the regular posted upgrade notification.
and no i cant see my log-in screen

---

