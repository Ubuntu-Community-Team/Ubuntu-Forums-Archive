---
title: "[SOLVED] Track who logs in. How?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by TJCIB on 2008-12-08
How would I go about keeping track of login information?  I would need to know who logs in and how long they stayed on.  To make it easier, I need a login and logout time.

I searched around the system logs and things and could find traces, but not every log in. I think I am using the wrong search terms in google because the results are not helpful.

I am using NIS for login, but I don't have a problem setting it up on each individual computer if NIS makes it too complicated.

Thanks for your help!

---

### Post by TJCIB on 2008-12-08
Sorry, I'm an idiot.  I JUST found the answer.

stupid "last" command.

---

### Post by Peter09 on 2008-12-08
in var/logs the file auth.log will show all logins and sudo activities.

---

