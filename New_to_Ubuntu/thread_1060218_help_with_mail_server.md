---
title: "help with mail server"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by fugaki on 2009-02-04
I followed this tutorial to set up a mail server:

[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

and now i am getting the following mail undeliverable message:

The following reciepients cannot be reached:
[email]myemail@domain.com[/email] on date/time
554 5.7.1 [email]myemail@domain.com[/email]: Relay access denied.

Any ideas?

Log section:

```
Feb  4 14:44:52 hostname postfix/smtpd[3434]: connect from unknown[IP]
Feb  4 14:44:52 hostname postfix/smtpd[3434]: setting up TLS connection from unknown[IP]
Feb  4 14:44:52 hostname postfix/smtpd[3434]: Anonymous TLS connection established from unknown[IP]: TLSv1 with cipher AES128-SHA (128/128 bits)
Feb  4 14:44:52 hostname postfix/smtpd[3434]: NOQUEUE: reject: RCPT from unknown[IP]: 554 5.7.1 <email@domain.com>: Relay access denied; from=<thisserveremail@thisdomain.com> to=<email@otherdomain.com>$
Feb  4 14:44:56 hostname postfix/smtpd[3434]: disconnect from unknown[IP]
Feb  4 14:45:40 hostname dovecot: IMAP(dan): Disconnected: Logged out bytes=3345/6367

```

---

