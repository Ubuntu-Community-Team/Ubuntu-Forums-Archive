---
title: "Postfix &amp; Dovecot installation &amp; configuration"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by bbx1003 on 2009-04-06
Dear Friend,



I have installed Postfix & Dovecot. I followed the instruction from the Ubuntu Server Guide.


I can telnet port 25 & 110. ( using CLI command to test send mail  & OutLook Express ) 

I can send, but receive no mail, telnet myserver 110, no mail also.


I really don't understand the Postfix mbox & dovecot mail_location explanation.



Can some one provide me the step-by-step on how to make the whole e-mail system work.......? 




TQ.

---

### Post by LiQuidAiR on 2009-04-08
A step by step is difficult to do in a short amount of time.  At least one that is fully functional and understandable.

Please post your Postfix and Dovecot versions and how you installed them.  If you installed Postfix by the CLI sudo apt-get command than please state that, or if you downloaded a .tar file.  This way I can at least provide links to websites that should give you a really good start to understand the basic configurations.  I would love to help you thru the install.

The number one rule you have to understand, which I don't :), is start very simple and make sure each change works as expected than move forward.  This way you can spot errors quickly.

I'm known for gather all the functionality I want in an install and doing it all at once.  Then, I spend weeks figuring it all out.  Sometimes months.  :)

---

