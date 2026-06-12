---
title: "Email server help"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by flyinggreg on 2008-01-02
Hi folks

I am a newbie to web admin and I am trying to setup an email server using Dapper.  I followed the Flurdy setup and had squirrelmail working and local email working, but no external email.

I have 2 issues going:
1)  I can't seem to get external email working.  When I try to email from GMail to my new server I get a 'connection refused' error.

2) SquirrelMail was letting me login and then quit!  I keep getting the incorrect login/password error - and I haven't touched my users database!

I am using EveryDNS for dynamic DNS service (I am behind a DSL modem/router).  I can see my website so I know the A & CNAME records are ok.  I setup another dynamic domain for my mail server as mail.wingandrotors.com.  I think my MX record might be incorrect and causing the problem.  I found almost everything I need to get this up and running on the Net - except setting up a proper internal/external email server.

Here is my record for my web site domain:
```
_HOST_                      _TYPE_           _VALUE_                     _MX _
wingandrotors.com         A             * dyn ip*                    -
wingandrotors.com         MX             mail.wingandrotors.com    1
[www.wingandrotors.com](www.wingandrotors.com)     CNAME          wingandrotors.com         -
mail.wingandrotors.com    A              *dyn ip*                    - 
```

I have Postfix setup looking for mail.wingandrotors.com and I can 'telnet wingandrotors.com' and get a '220-mail.wingandrotors.com', but when I send email - nothing shows up in the virtual mailbox - though I did manage to get a test message through once.  Aliases are setup for localhost and mail.wingandrotors.com to go to @wingandrotors.com & my users database is setup to _user_@wingandrotors.com

Thanks for your guys patience ahead of time!

---

