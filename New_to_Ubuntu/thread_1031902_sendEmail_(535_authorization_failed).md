---
title: "sendEmail (535 authorization failed)"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by Frank_F on 2009-01-05
Hello,

Wondering if anyone has any insight into this error

I am typing in the command line


 ./sendEmail -f [email]XXXX@rogers.com[/email] -t [email]XXXX@sprint.com[/email] -s smtp.broadband.rogers.com -xu XXXX -xp XXXXX -m "this is a test"


sendEmail[9113]: ERROR => Received: 	535 authorization failed (#5.7.0)

Thanks

---

### Post by blueridgedog on 2009-01-05
Sendmail is telling you in its own odd language that it tried to send your email, but when it presented the username and password, the remote end replied "authorization failed".  Double check the username and password.

---

### Post by Frank_F on 2009-01-05
thanks I will

---

