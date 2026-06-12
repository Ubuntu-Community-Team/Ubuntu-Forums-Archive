---
title: "sendmail configuration"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by deepak.agrawal1101 on 2009-11-04
can u plz tell me how to configure mail server on ubuntu through commands

---

### Post by spikyjt on 2009-11-18
What do you need the email server to do? Will it be a full domain email server? Or does it just need to send mail from another service, via a relay host?

If the former, check out [https://help.ubuntu.com/9.10/serverguide/C/email-services.html](https://help.ubuntu.com/9.10/serverguide/C/email-services.html) which has comprehensive instructions. I have personal experience of the Postfix/Dovecot setup and could help if you get stuck.

If the latter, install ssmtp and then read the man page (man ssmtp) - it's really easy to setup.

If you want an all singing all dancing email server, you might try kolab - [http://kolab.org](http://kolab.org) , but don't try the ubuntu packages - they don't work.

---

### Post by moonport on 2009-11-19
> **spikyjt said:**
> What do you need the email server to do? Will it be a full domain email server? Or does it just need to send mail from another service, via a relay host?

If the former, check out [https://help.ubuntu.com/9.10/serverguide/C/email-services.html](https://help.ubuntu.com/9.10/serverguide/C/email-services.html) which has comprehensive instructions. I have personal experience of the Postfix/Dovecot setup and could help if you get stuck.

If the latter, install ssmtp and then read the man page (man ssmtp) - it's really easy to setup.

If you want an all singing all dancing email server, you might try kolab - [http://kolab.org](http://kolab.org) , but don't try the ubuntu packages - they don't work.

In my case, I just need to send an email when the backup script finish, just as an info issue.
I've been trying with sendmail 'cause it seems simple, and while it works on some machines, I could not configure it in others.

I guess the MTA config is the key, but I can't find the problem.
Any help would be appreciated.

TIA

---

