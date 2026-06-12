---
title: "Setting up mail server"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by phillipdbaker on 2009-03-15
i have followed the online guide in setting up a mail server and can send messages internally. But if i try to send emails to it from outside it get a 550 user doesnt exist have i configured something wrong. I have made DNS changes so mail from my domain points towards my server.

phill

---

### Post by Titan8990 on 2009-03-15
I notice that this is in the absolute beginners talk forum.... Email servers are not for beginners, period. Its fine to learn and etc, but it may be best that your not trying to establish a production email server here. A misconfiguration can easily result in spammers relaying mail through your MTA.


Now, moving along....


A) What type of smtp server is it?

B) What type of POP/IMAP server are you using?

C) Separate delivery agent such as procmail?

D) What type of authentication are you using and have you checked for the existence of the user, as well as created a mailbox in their homedir?

---

### Post by khelben1979 on 2009-03-15
Have you checked how your firewall is configured?

---

