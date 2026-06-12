---
title: "110 Can't open SMTP stream"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by chrisdee on 2010-04-01
Hi.

I'v had postfix + dovecot + squirrelmail working just fine on my Ubuntu 9.10 for months untill about 2 weeks ago. Suddenly I get a error message when I try to send mail via squirrelmail.

ERROR
Message not sent. Server replied:
Connection timed out 110 Can't open SMTP stream.

I can recive mail but not send. Any idea what's going wrong and how this can be fixed ?

---

### Post by chrisdee on 2010-04-22
I found out the problem.:P

The firestarter firewall service was the problem. Rather than troubleshooting I uninstalled it, and now everyting works fine:P

---

