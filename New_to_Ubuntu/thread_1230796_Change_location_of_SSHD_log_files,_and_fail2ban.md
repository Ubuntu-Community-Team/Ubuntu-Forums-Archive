---
title: "Change location of SSHD log files, and fail2ban"
date: 2009-08-03
forum: New to Ubuntu
---

### Post by harry71194 on 2009-08-03
Edit: Fixed it. Apparently I had to chmod 777 the non-existant auth.log file... :o



Hello, I have been using fail2ban with sshd for a while, and it has worked..... until I noticed that my sshd logs have been in /var/log/auth.log.1 instead of in /auth.log..... does fail2ban scan all auth.log*'s in that folder?

Anyways, to try to fix this, I stopped SSHD and Fail2ban, deleted the 2 files, and reran sshd, and status says it is running fine. BUT, it did not remake the auth.log file, nor any log file I can see. I even did a few denied logins to test this; fail2ban did not ban me, as nothing was logged into the (non existant) auth.log file.
So, I tried to make an auth.log file, chmod 777'd it, then reran sshd; STILL the same problem.


Please help me :)

---

