---
title: "ISPConfig killed mail"
date: 2010-06-17
forum: New to Ubuntu
---

### Post by conryf on 2010-06-17
Hello,

  I have had some serious trouble setting up email on my webserver.

I was able to send mails, but not with a return addresss. So I decided to follow this guide:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p5](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-3-p5)

and now even the command line mail doesn't work. The mail log has this as the tail:


Jun 17 11:51:45 loft4657 postfix/cleanup[2348]: D3ADD130C21E: message-id=<20100617115145.D3ADD130C21E@iwriteit.com>
Jun 17 11:51:46 loft4657 postfix/qmgr[1611]: D3ADD130C21E: from=<conryf>, size=287, nrcpt=1 (queue active)
Jun 17 11:51:46 loft4657 postfix/smtpd[2354]: connect from localhost.localdomain[127.0.0.1]
Jun 17 11:51:46 loft4657 postfix/smtpd[2354]: warning: SASL: Connect to private/auth failed: No such file or directory
Jun 17 11:51:46 loft4657 postfix/smtpd[2354]: fatal: no SASL authentication mechanisms
Jun 17 11:51:47 loft4657 postfix/master[1606]: warning: process /usr/lib/postfix/smtpd pid 2354 exit status 1
Jun 17 11:51:47 loft4657 postfix/master[1606]: warning: /usr/lib/postfix/smtpd: bad command startup -- throttling
Jun 17 11:51:47 loft4657 amavis[1086]: (01086-04) (!)FWD via SMTP: <conryf> -> <conryf@gmail.com>, 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting:  at (eval 113) line 596, <GEN35> line 82.): id=01086-04
Jun 17 11:51:47 loft4657 amavis[1086]: (01086-04) Blocked MTA-BLOCKED, <conryf> -> <conryf@gmail.com>, Message-ID: <20100617115145.D3ADD130C21E@iwriteit.com>, mail_id: XcQC03DMnWER, Hits: 0.179, size: 287, 1117 ms
Jun 17 11:51:47 loft4657 postfix/smtp[2351]: D3ADD130C21E: to=<conryf@gmail.com>, relay=127.0.0.1[127.0.0.1]:10024, delay=1.5, delays=0.39/0.01/0/1.1, dsn=4.5.0, status=deferred (host 127.0.0.1[127.0.0.1] said: 451 4.5.0 From MTA([127.0.0.1]:10025) during fwd-connect (Negative greeting:  at (eval 113) line 596, <GEN35> line 82.): id=01086-04 (in reply to end of DATA command))


Please help I need this to be working!

---

