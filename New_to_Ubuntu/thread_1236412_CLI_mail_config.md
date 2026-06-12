---
title: "CLI mail config"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by nevets_anderson on 2009-08-10
Hi

I've installed postfix and dovecot on my machine and it has a Fully qualifyed domain name.

I can send mail out no problem and I seem to be getting mail in (I'm watching the mail.log with a tail -f ) anyway 

The problem is that mail is not being read by the mail client on the cli.

For example if I type mail I get No mail for steve

If I cd into my home directory I can see new messages being sent to /home/steve/Maildir/new

 From what I can work out I seem to need to configure mail to look into the /home/steve/Maildir/new directory 

Any ideas on how I might go about this?

TIA

Nevets 

aka Steve

---

### Post by wizard10000 on 2009-08-10
Can't tell you exactly how, but I can tell you what you're looking to configure is called .procmailrc - it tells your MTA what to do with the mail when it comes in.

.procmailrc can be either system-level or user-level - or both.

Hope this helps -

---

