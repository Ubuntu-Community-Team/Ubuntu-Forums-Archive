---
title: "sendmail config problem..."
date: 2010-05-17
forum: New to Ubuntu
---

### Post by samuraiii on 2010-05-17
Hi to everybody,
i have problem with sendmail, 
I need it to relay some outgoing mails based on recipient domain through another smtp (TLS secured) and the rest to be just send by sendmail itself. sendmail should work only as sending server for localhost.

Thanks for future help
S

im running:
ubuntu lucid 64bit
sendmail 8.14.3-9.1
clamsmtp 1.10-6

---

### Post by samuraiii on 2010-05-23
bump... :)

---

### Post by samuraiii on 2010-05-28
another bump

---

### Post by fatality_uk on 2010-05-28
Not 100% sure what you want, but I think you have 2 options if I understand you correctly. 1 is say a script which analyses the recipient domain and then forwards to sendmail based on that or create forw2ard rules

[http://www.feep.net/sendmail/tutorial/intro/forward.html](http://www.feep.net/sendmail/tutorial/intro/forward.html)
[http://www.sendmail.org/tips/relaying](http://www.sendmail.org/tips/relaying)

---

### Post by samuraiii on 2010-06-06
hi,
I'm sorry to reply with such delay... relaying (as I understand it) isnt my "problem solver" because it analyzes sender domain not recipient...

and to be hones I didnt caught logic of that .forward file text (its shameful that I i cant catch meaning :confused:)
thanks for your reply

---

