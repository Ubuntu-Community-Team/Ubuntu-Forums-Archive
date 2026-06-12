---
title: "&quot;New mail&quot; reported by finger"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by flylehe on 2009-09-05
Hi, 
I just learned to use finger command. Its output for mail confuses me:
> 
New mail received Mon Aug 31 00:00 2009 (EDT)
     Unread since Mon Jul  6 00:00 2009 (EDT)

I never use evolution or any software to check my emails. I only open webpages to access them. How to explain and check the "New mail" shown by finger?
Thanks and regards!

---

### Post by jpeddicord on 2009-09-05
> **flylehe said:**
> Hi, 
I just learned to use finger command. Its output for mail confuses me:

I never use evolution or any software to check my emails. I only open webpages to access them. How to explain and check the "New mail" shown by finger?
Thanks and regards!

Run `mail`. Does anything come up?

---

### Post by flylehe on 2009-09-05
Thanks! I see. I set up cron jobs, so everytime it does some job, it will mail me.
So this mail is not for emails, right? Only for system notification?

---

### Post by jpeddicord on 2009-09-05
> **flylehe said:**
> Thanks! I see. I set up cron jobs, so everytime it does some job, it will mail me.
So this mail is not for emails, right? Only for system notification?

Technically those notifications *are* email, but unless you have a SMTP daemon (eg, postfix) installed they won't be sent or received outside of your system.

---

