---
title: "Mailserver malfunction"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-01-22
I checked my KsystemLog application and found a lot of this:

2009-01-20 09:31:53 Inspiron nullmailer[4285] Starting delivery: protocol: smtp host: mail. file: 1231166253.11986
2009-01-20 09:31:53 Inspiron nullmailer[23956] smtp: Failed: Connect failed
2009-01-20 09:31:53 Inspiron nullmailer[4285] Sending failed: Host not found
2009-01-21 09:31:53 Inspiron nullmailer[4285] Delivery complete, 4 message(s) remain.
2009-01-20 09:32:53 Inspiron nullmailer[4285] Rescanning queue.

This set of instructions repeats endlessly 24/7 -- Wazzup with this? :o

---

### Post by Goodseeker on 2010-03-12
> **mayagrafix said:**
> I checked my KsystemLog application and found a lot of this:

2009-01-20 09:31:53 Inspiron nullmailer[4285] Starting delivery: protocol: smtp host: mail. file: 1231166253.11986
2009-01-20 09:31:53 Inspiron nullmailer[23956] smtp: Failed: Connect failed
2009-01-20 09:31:53 Inspiron nullmailer[4285] Sending failed: Host not found
2009-01-21 09:31:53 Inspiron nullmailer[4285] Delivery complete, 4 message(s) remain.
2009-01-20 09:32:53 Inspiron nullmailer[4285] Rescanning queue.

This set of instructions repeats endlessly 24/7 -- Wazzup with this? :o
I think I have the same problem:
Mar  8 03:27:59 pc1 nullmailer[2060]: Rescanning queue.
Mar  8 03:27:59 pc1 nullmailer[2060]: Starting delivery: protocol: smtp host: mail. file: 1267988814.23359
Mar  8 03:27:59 pc1 nullmailer[28693]: smtp: Failed: Connect failed
Mar  8 03:27:59 pc1 nullmailer[2060]: Sending failed:  Host not found
Mar  8 03:27:59 pc1 nullmailer[2060]: Delivery complete, 1 message(s) remain.

..and it goes on forever.
Any hints?
Thanks

---

