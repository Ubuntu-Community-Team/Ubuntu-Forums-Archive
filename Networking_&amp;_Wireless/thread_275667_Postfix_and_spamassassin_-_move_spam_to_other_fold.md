---
title: "Postfix and spamassassin - move spam to other folder"
date: 2006-10-11
forum: Networking &amp; Wireless
---

### Post by Muffe on 2006-10-11
I have just configured my own mailserver, running Ubuntu 6.06. I have used postfix and dovecot as the main applications in my mailserver, and have configured them according to [this](https://help.ubuntu.com/ubuntu/serverguide/C/email-services.html) guide. The mails are stored in the Maildir format, and accessed through IMAP.

The only problem is that I get a lot of spam (who doesn't?). Therefore, I installed spamassassin, and configured it using a very tiny [howto](http://hurring.com/howto/postfix_spamd/).

All the SPAM is no marked with "[SPAM]" in the email subject, but they still show up in my inbox. I have made a rule in Thunderbird that moved all mails maked as spam, into its own folder, called SPAM.

Is it possible to have all this spam-mails moved to the folder SPAM before it reaches the mail client? Can postfix handle this, or do I need yet another piece of software to do that? What's the best way to handle this problem?

Thanks in advance.

---

