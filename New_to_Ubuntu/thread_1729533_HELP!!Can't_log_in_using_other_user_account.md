---
title: "HELP!!Can't log in using other user account"
date: 2011-04-15
forum: New to Ubuntu
---

### Post by juanbisente on 2011-04-15
Hi!

I'm using Ubuntu 10.04. I can't log in using my other user account except for m administrator account. Every time I try to use my other account my system crashes. Please help

Thank you

---

### Post by WanderingAlbatross on 2011-04-15
How did you create the other account?

---

### Post by juanbisente on 2011-04-16
the usual way of creating a user account, system - administration - users and group. there I added the new user.

---

### Post by MrEgg on 2011-04-16
What privileges did you give the new user? It could be a permissions issue. Also, check that /home/newuser was properly created with the right ownership, and that its shell is /bin/bash.

---

### Post by juanbisente on 2011-04-16
the new user's privilege is desktop user. the right home ownership and shell was properly created. it just the system hangs everytime I'm trying to log in using my created account. but if I switch user from  my administrator account there is no problem,

---

### Post by MrEgg on 2011-04-16
> **juanbisente said:**
> the new user's privilege is desktop user. the right home ownership and shell was properly created. it just the system hangs everytime I'm trying to log in using my created account. but if I switch user from  my administrator account there is no problem,

Go [ALT] + [CTRL] + [F1], try and login using the user account and see what happens.

Return to the GUI using the combo [ALT] + [CTRL] + [F7].

Please post :
```
ls -l /home
ls -l /home/user
```

---

### Post by juanbisente on 2011-04-16
I can log in using tty1 but when I tried to return to the GUI it didn't display the GUI. it just says "checking Battery state"

when i posted "ls -l /home" it displayed the the home folders the permision
then when i posted the "ls -l /home/username it displayed the home folders content.
what should i expect from that post?

---

### Post by MrEgg on 2011-04-16
It's kind of hard to help if you don't actually want to show the results of what we ask to be posted.

Anyway, within /home/user :
- check permissions for .ICEauthority
- check .xsession-errors

---

### Post by juanbisente on 2011-04-18
Here is the permissions of the .ICEauthority and .xsessions-error
```
-rw------- 1 robansilan robansilan 1050 2011-04-16 15:08 /home/robansilan/.ICEauthority
-rw------- 1 robansilan robansilan 1870 2011-04-16 15:09 /home/robansilan/.xsession-errors

```

---

### Post by juanbisente on 2011-04-18
Think I've found the reason of the problem. Think it's my video card.
Thanks for the help

---

