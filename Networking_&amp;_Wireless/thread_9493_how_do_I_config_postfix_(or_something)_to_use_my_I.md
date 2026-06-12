---
title: "how do I config postfix (or something) to use my ISP's smtp server?"
date: 2004-12-29
forum: Networking &amp; Wireless
---

### Post by negativ on 2004-12-29
I'm trying to set up my system so that I can have certain info emailed to my email account periodically.

My thought is to set up a cron job that will run something like 
```
(blah blah blah) | mail myemail@isp.com
```

The trouble is, I don't know how to configure it so that "mail [email]myemail@isp.com[/email]" actually gets out.

I need sort of a dummy's guide. :confused:

---

### Post by Sintara on 2005-01-05
Postfix is a "mail transfer agent," or MTA, and is responsible for tranferring/transporting e-mail for your system.  It *is* the SMTP server.  To configure Postfix, or another MTA (ie sendmail, qmail) to send e-mail to your ISP so that your ISP's mail server can send the mail to the desired e-mail account is pointless.  If your MTA and local network setup is configured properly, your mail command should work just fine.  Test it and see what happens.  If you need assistance with MTA configuration, look for your MTA documentation in /usr/share/doc, and check out the relevant manpages.

---

### Post by nocturn on 2005-01-05
[QUOTE=Sintara]Postfix is a "mail transfer agent," or MTA, and is responsible for tranferring/transporting e-mail for your system.  It *is* the SMTP server.  To configure Postfix, or another MTA (ie sendmail, qmail) to send e-mail to your ISP so that your ISP's mail server can send the mail to the desired e-mail account is pointless.  If your MTA and local network setup is configured properly, your mail command should work just fine.  Test it and see what happens.  If you need assistance with MTA configuration, look for your MTA documentation in /usr/share/doc, and check out the relevant manpages.[/QUOTE]

Actually not always pointless.
Many ISPs (including mine) block those outgoing connections, forcing you to go through their SMTP servers to track spam sent form their network.

For such an ISP you have to configure your MTA to relay to their SMTP server (using something like smarthost).  For some (again like mine) you even have to do adress rewriting to match their domain.  The latter has the unfortunate side effect that all mail appears to come from <your-local-user>@<ispdomain> or a single mail account with that ISP.

---

### Post by KupernikuZ on 2005-01-18
I have tried to write:
```
relayhost = *your.ISPs-smtp-host.com*
```
in my */etc/postfix/main.cf*  file once. As I remember, it worked.

---

