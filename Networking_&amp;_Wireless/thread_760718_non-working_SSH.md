---
title: "non-working SSH"
date: 2008-04-20
forum: Networking &amp; Wireless
---

### Post by ondatrik on 2008-04-20
hello!

since recently my ssh acts weird (=doesnt work), typing ordinary 'ssh user@computer', the thing asks for password and here all the communication ends, it doesnt open any distant prompt, it doesnt wirte anything, ctrl+c doesnt stop it neither does ctrl+d and i wonder what i am missing (while for example using putty works without any problems)...

thanks a lot for any suggestions

---

### Post by kevdog on 2008-04-20
Do a

ssh -vvv user@computer

(Those are 3 v's and not w's)
and post the output.  It may give a clue whats going on.

---

