---
title: "nullmailer"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-13
ay 13 21:33:05 pj-indulgence nullmailer[2647]: Starting delivery: protocol: smtp host: mail. file: 1242158287.22837
May 13 21:33:16 pj-indulgence nullmailer[11370]: smtp: Failed: Connect failed
May 13 21:33:16 pj-indulgence nullmailer[2647]: Sending failed:  Host not found
May 13 21:33:17 pj-indulgence nullmailer[2647]: Starting delivery: protocol: smtp host: mail. file: 1242070913.26777
May 13 21:33:27 pj-indulgence nullmailer[11374]: smtp: Failed: Connect failed
May 13 21:33:28 pj-indulgence nullmailer[2647]: Sending failed:  Host not found
May 13 21:33:28 pj-indulgence nullmailer[2647]: Delivery complete, 2 message(s) remain.
May 13 21:34:28 pj-indulgence nullmailer[2647]: Rescanning queue.
May 13 21:34:29 pj-indulgence nullmailer[2647]: Starting delivery: protocol: smtp host: mail. file: 1242158287.22837
May 13 21:34:46 pj-indulgence nullmailer[11398]: smtp: Failed: Connect failed
May 13 21:34:51 pj-indulgence nullmailer[2647]: Sending failed:  Host not found
May 13 21:34:55 pj-indulgence nullmailer[2647]: Starting delivery: protocol: smtp host: mail. file: 1242070913.26777
May 13 21:35:05 pj-indulgence nullmailer[11403]: smtp: Failed: Connect failed
May 13 21:35:09 pj-indulgence nullmailer[2647]: Sending failed:  Host not found
May 13 21:35:17 pj-indulgence nullmailer[2647]: Delivery complete, 2 message(s) remain.
May 13 21:36:07 pj-indulgence nullmailer[2647]: Rescanning queue.


I get screeds and screeds of these error messagages in my syslog.....what should I do please?

---

### Post by dunbrokin on 2009-05-14
bump

---

### Post by dunbrokin on 2009-05-16
bump

---

### Post by dunbrokin on 2009-05-17
bump

---

### Post by gleepwurp on 2009-05-21
Hi!

Had the same issue when I came in from work today... I just removed the nullmailer package (sudo apt-get remove nullmailer) and it fixed my issue... Looks like its a package for testing emailing capabilities when developing an application...?

Good luck!

Gleepwurp.

---

### Post by dunbrokin on 2009-05-22
> **gleepwurp said:**
> Hi!

Had the same issue when I came in from work today... I just removed the nullmailer package (sudo apt-get remove nullmailer) and it fixed my issue... Looks like its a package for testing emailing capabilities when developing an application...?

Good luck!

Gleepwurp.

Thanks, I will try that...

---

