---
title: "Email Send Problems"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by tim042849 on 2007-05-30
I'm using kubuntu 7.04 (feisty fawn, amd 64)
I *am* able to send and receive email without problem using kmail.
However, I am *not* able to send mail from program scripts.
Example: Using python smtplib, I get a "Connection unexpectedly closed" error
              Using rebol sendmail function, I get Access Error: Cannot connect to <mailserver>

Using the same code, I can send mail without any problem from my slackware
machine, which is behind the same router and on the same network.

This suggests to me that there is some sort of firewall on this ubuntu machine,
which is being "avoided" by kmail, but not by the scripting languages.

Any ideas?
Thanks
Tim

---

