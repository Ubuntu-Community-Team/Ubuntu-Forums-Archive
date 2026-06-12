---
title: "evolution and outgoing mail"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by gordonsmall@bellsouth.net on 2010-04-21
I have been using Evolution for a couple of years now with no problems. At the time I started using it, I was getting my Internet from BellSouth and used their settings with no problem.  After AT&T took them over, and merged with Yahoo, the settings changed dramatically, but finally got it back running fine.  However, a couple of months ago it stopped sending messages. I have not been able to fix that.

I recently moved to a MiFi2200 and 3G for our Internet access and dropped the bellsouth address and started using gmail as our primary e-mail account (we live in a rural area, and our DSL was often not much better than dialup).  I tried some pop settings I found online for Gmail (and changed the gmail settings to allow pop) and now I can neither send or receive from Evolution. I can probably manage just fine without the onboard client, but I would like to know how to get it running with gmail - and my wife may eventually prefer the familiarity of the e-mail client. Any thoughts?

Gordon Small
[email]balsamgap@gmail.com[/email]

---

### Post by -humanaut- on 2010-04-21
Make sure in the SMTP settings mark the "use verification" and select SSL

---

### Post by drs305 on 2010-04-21
My Gmail settings:
pop.googlemail.com  [email]username@gmail.com[/email] SSL (will select port 995)   
smtp.gmail.com  port 465, [email]username@gmail.com[/email] & password, SSL

I see I have googlemail for POP and gmail for smtp. Don't know if it makes a difference or not, but that's what I have and send/receive both work.

---

### Post by drs305 on 2010-04-21
My Gmail settings:
pop.googlemail.com  [email]username@gmail.com[/email] SSL (will select port 995)   password
smtp.gmail.com  port 465, [email]username@gmail.com[/email] & password, SSL

I see I have googlemail for POP and gmail for smtp. Don't know if it makes a difference or not, but that's what I have and send/receive both work.

Edit: Computer froze up, sorry.

I have the ports listed but they do not appear in any of the settings so Evolution must take care of it based on the encryption.

---

### Post by gordonsmall@bellsouth.net on 2010-04-23
Thanks - will check.

Gordon

---

### Post by gordonsmall@bellsouth.net on 2010-04-23
That is what I initially tried - but glad to hear it works.

Gordon

---

