---
title: "how to change a admin privilege to costum"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by aab001 on 2011-04-27
hi 
I have only one user, i changed the privilege from the default (costum) to admin, know i want to go back to costum privelege but every time i got the message "Can't revoke administration rights"
any idea?

---

### Post by user1397 on 2011-04-27
> **aab001 said:**
> hi 
I have only one user, i changed the privilege from the default (costum) to admin, know i want to go back to costum privelege but every time i got the message "Can't revoke administration rights"
any idea?

what did you exactly do when you changed privilege from default to admin?  I mean, how did you do that?

---

### Post by _0R10N on 2011-04-27
> **aab001 said:**
> hi 
I have only one user, i changed the privilege from the default (costum) to admin, know i want to go back to costum privelege but every time i got the message "Can't revoke administration rights"
any idea?


If you've changed de permissions for some file to admin, then you're no longer allowed to change them back. What you should do is to execute a chmod with sudo.

Kind regards!

---

