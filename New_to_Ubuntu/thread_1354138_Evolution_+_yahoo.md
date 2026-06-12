---
title: "Evolution + yahoo"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by mayagrafix on 2009-12-13
can Evolution be configured to check Yahoo mail and or Hotmail clients?

Thanks for any input here. ;)

---

### Post by Matt__ on 2009-12-13
They both use POP and smtp so there is no reason why they wouldn't work.
Get the settings from your provider/google it 

Yahoo should be this...
**Incoming mail server settings**
 
[LIST]
[*]POP server: **plus.pop.mail.yahoo.com**
[*]Use **SSL**
[*]Port: **995**
[/LIST]
 **Outgoing mail server (SMTP) settings**
 
[LIST]
[*]SMTP server: **plus.smtp.mail.yahoo.com**
[*]Use **SSL**
[*]Port: **465**
[*]Use authentication
[*]Account Name/Login Name: Your  Yahoo! Mail ID (your email address without the "@yahoo.com", for example, &#8220;testing80&#8221;)
[*]Email Address: Your  Yahoo! Mail address (for example, [EMAIL="testing80@yahoo.com"]testing80@yahoo.com[/EMAIL])
[*]Password: Your  Yahoo! Mail password
[/LIST]

---

### Post by dmp2010 on 2010-10-10
Tried everything but still doesn't work.

---

### Post by jimrz on 2010-10-10
Probably a silly question, but have you setup your Yahoo mail for POP access? Which used to mean paying for [COLOR="Red"][COLOR="Red"]**_[Yahoo Mail Plus]("http://overview.mail.yahoo.com/enhancements/mailplus")_**[/COLOR][/COLOR].

---

### Post by DougieFresh4U on 2010-10-10
Don't know if Evolution has same requirements,or some way to make web mail work but I installed WebMail for Thunderbird and my Yahoo mail is there for me.It's not the 'pay' Yahoo email :)

---

