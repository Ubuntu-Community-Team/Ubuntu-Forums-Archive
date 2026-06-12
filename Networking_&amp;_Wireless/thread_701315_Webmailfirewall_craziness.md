---
title: "Webmail\firewall craziness"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by nusse on 2008-02-19
Running Ubuntu Server 7, postfix and squirrelmail.   For some reason I can't access the webmail from the outside world and am scratching my head on this one.

* webmail works internally
* the email server is getting email from the outside without a problem
* I have ports 80,25,110 and 143 set to forward to the internal server


There is something I missed in the firewall that I need to forward on but am at a loss.  I've searched this problem and so far has seen nothing that indicates that I have my set up done incorrectly.

Does anyone have any ideas for a poor frazzled soul?

---

### Post by jhetrick62 on 2008-02-19
Your isp may be blocking one of your required ports if you are not on a commercial account.  I could not use port 80 for my web server so I moved apache to port 88 and it worked like a champ.  You might consider that??

Jeff

---

### Post by nusse on 2008-02-19
Thanks ... I will give that a go .. that makes some sense actually.

And so simple!

---

### Post by nusse on 2008-02-19
Well still no joy .. I've got something messed up.

I have apache running on port 88 now

Changed the forwarding to point to 88 on my firewall ...

go to <address>:88/squirrelmail

No joy ...

I know I'm missing something simple ....

---

### Post by jhetrick62 on 2008-02-19
I don't know anything about squirrelmail as I don't use it, but there has to be a config file for it and I'm guessing you need to specify the port there??

Jeff

---

### Post by nusse on 2008-02-20
Thanks for you help. I'll check for something like that

---

### Post by nusse on 2008-02-21
I didn't see anything in squirrelmail for specifying the ports other than smtp and ssl. Anyone have any ideas?

---

