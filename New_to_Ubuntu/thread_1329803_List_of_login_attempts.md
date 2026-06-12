---
title: "List of login attempts"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-11-17
I know I have seen this info before, but I cannot find it now.

Where is the file that contains the log of login attempts?

Thanks.

---

### Post by MonoDeem on 2009-11-17
[COLOR=Blue]/var/log/auth.log
[/COLOR]

---

### Post by ozzyprv on 2009-11-17
> **MonoDeem said:**
> [COLOR=Blue]/var/log/auth.log
[/COLOR]

Thank you!

Is there a log of the users that logged in the last "x" days?

---

### Post by XCan on 2009-11-18
I believe you can use the the command "last", or look into the /var/log/wtmp files manually. It will just list all logins but at a chronological order so sorting through it should be very easy.

---

