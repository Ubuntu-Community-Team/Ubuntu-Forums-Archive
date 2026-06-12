---
title: "cannot send email through Evolution..."
date: 2010-07-26
forum: New to Ubuntu
---

### Post by al.adab on 2010-07-26
hello,

in Evolution I have all my contacts stored under OnThisComputer/Personal. I've never been able to send emails to any of them since upgrading to Ubuntu 10.04. 

Here's the error message I get: 

*RCPT TO <xxx@xxx.com> failed. Recipient address rejected: you must be authenticated to use this service*

any idea?

---

### Post by Rubi1200 on 2010-07-27
From the Evolution website:
 
**> [B]Why do my emails not get sent?**[/B]
 
 
>  
There can be several reasons. Check all recipient addresses in all mails in your outbox - if the first message contains a wrong mail address, also all the other messages do not get send. Also check your SMTP settings (the settings where you define which server to use to send emails) and make sure to have entered the correct server address and a correct authentification method that is supported by the server. If the Send & Receive button is greyed out then you may be offline. To go online, click File - Work online and you should now be able to operate the Send & Receive button


---

### Post by al.adab on 2010-07-28
Thanks for the thought but the Evolution settings for my email address are as they were on Evolution as at the previous edition of Ubuntu. 

I've just checked my email provider how-to and everything is in place. I've also tried removing the encryption, to no avail. 

Most of the times, the email to be sent disappears from the outbox in Evolution, and I only get an error message at the bottom of the window. If I close and re-open Evolution + try to send the message, I get the error message described on my first post. 

Bug?

---

### Post by Merovius on 2010-07-28
Just out of curiosity, can you send an e-mail to yourself?

---

### Post by al.adab on 2010-07-28
No I can't send emails to myself. I remember that previously - on Ubuntu 9.04 - Evolution only let me send emails to people whose email address was stored in contacts. I tried both "unknown" and "known" email address, and I get the same error message...

---

### Post by Merovius on 2010-07-28
I use Evolution with gmail, hotmail, RoadRunner mail and my own domain. I can email myself or any other address with out issue. If I had to guess I would say the upgrade corrupted something for the email account you had set up previously. I think I would try setting the old account to not be checked automatically and try setting up a "new" account with the settings your account requires just to see if it works. If it does I would use the "new" account and abandon the old. Also verify the security settings for the sending mail (SMTP) section. Sounds like an authentication failure.

---

### Post by Whatrymes on 2010-07-28
Is Comcast your provider? Did you set smtp to "smtp.comcast.net:587"in the sending mail setting for the smtp server? Also check "Authentication is required."

---

### Post by al.adab on 2010-07-29
for some reason it sends emails only if I enable "server requires authentication" (Edit/preferences/edit account/sending emails) contrary to my email provider's directions...

works fine now :)
thanks everyone for your help

---

### Post by Merovius on 2010-07-29
Welcome!

---

### Post by Whatrymes on 2010-07-29
Mr too

---

