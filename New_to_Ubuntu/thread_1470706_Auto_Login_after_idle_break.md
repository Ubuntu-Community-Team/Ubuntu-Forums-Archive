---
title: "Auto Login after idle break"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by FredVanH on 2010-05-03
Hi.  I just upgraded Ubuntu 9.10 to 10.04.  I got asked for my password all the time and so, after consulting this forum, did System | Administration | LoginScreen | Unlock | Login as ___ automatically (a checkoff) | Close;  and Restarted.  Now I am automatically logged in after a Shutdown or a restart;  however I am still required to log in with my admin password every time I try to "get back in" by pushing a key after the screensaver timeout (which is often).  Any suggestions would be appreciated.
Thanks,
Fred

---

### Post by Elfy on 2010-05-03
I found the only way was to not let the screensaver actually lock the screen - that is fine for me as I use this at home and am not worried about anyone using this box. I'd not do that if there was a possibility of someone else getting on here.

Unless someone else comes along I would either stop screensaver locking screen or increase the timeout for it.

---

### Post by FredVanH on 2010-05-03
Thanks, Forest.  That worked!  I appreciate your timely and helpful reply.
Regards,
fred:KS

---

### Post by modsbyus on 2010-05-26
This helped me too. Thanks again guys!

---

### Post by 7kreed on 2010-11-21
folks i am a total newvie,i am having this problem also. now i follow i need to change the time out of the screen saver.i have been looking at the manuel on how to do that i guess ididn't get it yet.can someone please HELP to give it to me step by step..

---

### Post by FredVanH on 2010-11-23
Hi, 7kreed.  To summarize, there were 2 steps to solve my particular problem.  You may have already done the first and, if so, need only do the second:

1)  System | Administration | LoginScreen | Unlock | Login as ___ automatically (a checkoff) | Close.

2)  System | Preferences | Screensaver:  In the resulting "ScreenSaver Preferences" dialog box, pick a screensaver, set a time length for it, check the box for "Activate Screensaver when computer is idle", and, most importantly, UNCHECK the box for "Lock screen when screensaver is active".

This is written from incomplete notes made at the time;  but it does reflect my settings at this time and I no longer have the problem.  Hope this helps.
Regards,
Fred

---

### Post by 7kreed on 2010-12-02
Thanks so much, that did the trick!!!

---

