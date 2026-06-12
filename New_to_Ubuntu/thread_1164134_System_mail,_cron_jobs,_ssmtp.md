---
title: "System mail, cron jobs, ssmtp"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by tnek on 2009-05-19
Hi,

I've heard of system mail, but never actually read any. I'm wondering how to, as root and my normal user account tnek:

[LIST]
[*]Check if the account has any system mail?
[*]And how I'm able to read them?
[/LIST]
I've also heard that the output of cron jobs is sent to the account under which the job is run as a system mail. I'm wondering:

[LIST]
[*]Is that true in all cases? What about the no output case? Is it dependent on exit status of my job?
[*]Is it also true for anacron which Ubuntu uses?
[*]Are there any other situations when a system mail is sent?
[/LIST]
I've installed [ssmtp]("http://packages.ubuntu.com/hardy/ssmtp") and I'm able to send mail using it. It would be convenient if I could use it to:

[LIST]
[*]Send system mail addressed to root or tnek to [email]firstmail@gmail.com[/email].
[*]Send mail sent to an account foo to some address specified within foo's home directory (or at another location).
[/LIST]
If it is possible I'm wondering how to set it up? And if it isn't possible I'm wondering what alternatives I have to deliver system mail to my users?

Thanks for reading! :)

---

### Post by Celauran on 2009-05-19
Mail is typically stored in /var/spool/mail/$username and can be read using the mail command (not installed by default in Ubuntu). None of the cron jobs I have running generate any system mail, though you can add MAILTO=Whatever to any entry in /etc/cron.* Once you have mail in /var/spool/mail/tnek, you will receive a command line notice whenever you open a terminal.

---

### Post by chrisod on 2009-05-19
you can also install [webmin]("http://webmin.com/"). It's a web interface to accomplish a lot of those sys admin type tasks - user mail, setting up cron jobs, etc. It's very handy. I use it on my Ubuntu server when I'm not in the mood to struggle with the command line.

---

