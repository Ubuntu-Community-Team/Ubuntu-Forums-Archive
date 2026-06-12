---
title: "IMMEDIATE HELP NEEDED, PLEASE: Cannot pass loginscreen"
date: 2010-06-14
forum: New to Ubuntu
---

### Post by yc2 on 2010-06-14
I apologize for capitals, but this is a little bit of an emergency.

Using GUI I created one extra user (yyy).

I also went to "menu > loginscreen" and removed my previous "log in automatically as "xxx" which is my old and original username.

After that it is not possible to log in graphically at all. When I click either of the users at the loginscreen the box says:
(My translation fr. Swedish)
Error initiating the authentication system - general error.

I can log in to CLI by ctrl/alt/f3

I cannot start recovery-mode, the same problem occurs.

I have tried this
```

sudo userdel yyy

```
The command worked, now I only see my old xxx user, but cannot log in go GUI.

My friends expect my servers to be up this evening and if someone can help me solve this soon I sould be very grateful. (I really need the GUI to set up things.)

---

### Post by epicoder on 2010-06-14
I don't have any experience with something like this, so I probably won't help much.

Try adding a new user? 
```
sudo useradd zzz
sudo passwd zzz
```

---

### Post by Ryan Dwyer on 2010-06-14
Attempt to log in again. Then switch to a different TTY and log in there. Run:

tail -n 50 /var/log/auth.log
tail -n 50 /var/log/syslog

Hopefully it will reveal what's going wrong.

---

### Post by yc2 on 2010-06-14
Thanks for replies.

I think I have found a solution. It was in a thread in this excellent forum. Sorry I can't say which, I was there via a LiveCd.

I removed the line
@include common-pamkeyring

from the file

/etc/pam.d/gdm

I can now log in graphically.

Thanks for replies and to those who gave the problem consideration.

Already two replies, this forum rocks.

EDIT:
Of course I should have told that that I had been using the pam-keyreing. But that was along time ago (I was trying to unlock the Ubuntu keyring so that I could restart servers from remote.) It was no success (only works in Feisty). I completely forgot about it. Everything has worked fine ever since, but now that I enabled the loginscreen, the pam-keyring was in its way. I had no clue that the pam-keyring-command was the culprit.

---

