---
title: "Problem for particular user account."
date: 2011-06-07
forum: New to Ubuntu
---

### Post by pmohankumar on 2011-06-07
Hi,

iam using ubuntu 9.10 karamic.

i installed xvidcap1.1.7 screen recording software in my system.

iam having accounts:
1.) mohan
2.) dev
3.) root (default)

For dev & root account, xvidcap working but for mohan account, xvidcap not working.

EXP: i logined in mohan account & opened the xvidcap screen recording software. 
software  opened nicely. after that i clicked the recording button, suddenly it  disappears. i can't find it in system monitor also. but that same  xvidcap was working fine for other two accounts.
What is the problem?
Kindly reply the solution.........................

---

### Post by crispy_420 on 2011-06-11
Did you try launching from command line with xvidcap to see if any errors come up?

---

### Post by conradin on 2011-06-11
goto system > administration > Users and groups
then select the user mohan, then goto advance settings, password required
then, look at the user privileges. Does Mohan have privi to video devices? or any other possibly required resource? if not check those, close and reset the user session. tell us how it goes.

---

### Post by pmohankumar on 2011-07-19
Thanks for your answer

---

