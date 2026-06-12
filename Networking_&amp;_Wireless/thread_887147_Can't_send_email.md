---
title: "Can't send email"
date: 2008-08-11
forum: Networking &amp; Wireless
---

### Post by michaelwerner on 2008-08-11
Hi,

I recently bought a new laptop and installed Ubuntu on it. Some days later I bought a new Router, a Belkin G MIMO.
I'm pretty sure that sending emails worked with the old router but it doesn't do so with the new one. I don't know why. Disabling the firewall did not solve the problem. The logfile shows:
```
* Doing POP before SMTP...
* Connecting to POP3 server: 213.165.64.22...
[20:59:09] POP3< +OK GMX POP3 StreamProxy ready <21731.1218502749@mp066>
[20:59:09] POP3> USER 112233
[20:59:09] POP3< +OK May I have your password, please?
[20:59:09] POP3> PASS ********
[20:59:09] POP3< +OK Mailbox locked and ready
[20:59:09] POP3> QUIT
[20:59:09] POP3< +OK GMX POP3 server signing off
* Connecting to SMTP server: 213.165.64.20 ...
*** Session timed out.
```

Any help or hint is appreciated.

Regards,
Michael

---

### Post by RedPandaFox on 2008-08-12
So you have the correct SMTP server entered?

---

### Post by michaelwerner on 2008-08-13
Yes, I have. And I have checked this very often....

---

