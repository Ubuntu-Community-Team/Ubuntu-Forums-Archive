---
title: "What is the &quot;adm&quot; group?"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by cat2005 on 2009-11-07
What is the "adm" group?  

I see an "admin" group to which my admin user (1st created user) belongs, but I also see an "adm" group.

My non-admin users have only "adm".  They do not have "admin."

What is the difference between "adm" and "admin"?  They sound like the same thing but with different names.  Is that true?

Thank you.

---

### Post by amingv on 2009-11-07
Didn't know what it was, but looked it up.
Here it is:
> adm: Group adm is used for system monitoring tasks. Members of this group can read many log files in /var/log, and can use xconsole. Historically, /var/log was /usr/adm (and later /var/adm), thus the name of the group.

I guess google is good after all :).

---

### Post by cat2005 on 2009-11-07
> **amingv said:**
> Didn't know what it was, but looked it up.
Here it is:


I guess google is good after all :).


Yes, but is it the same as "admin"?  That is what I wish to know.

---

### Post by diesch on 2009-11-07
> **cat2005 said:**
> What is the "adm" group?  

I see an "admin" group to which my admin user (1st created user) belongs, but I also see an "adm" group.

My non-admin users have only "adm".  They do not have "admin."

What is the difference between "adm" and "admin"?  They sound like the same thing but with different names.  Is that true?

Thank you.

In Ubuntu members of the group *admin* can run programs with root privileges, members of *adm* are allowed to view some logfiles

---

### Post by cat2005 on 2009-11-08
> **diesch said:**
> In Ubuntu members of the group *admin* can run programs with root privileges, members of *adm* are allowed to view some logfiles


Thank you.

---

