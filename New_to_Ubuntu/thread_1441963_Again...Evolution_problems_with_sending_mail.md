---
title: "Again...Evolution problems with sending mail"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Jeffster999 on 2010-03-29
I have read the threads concerning Evol not sending email andI tried the solutions but it didn't work. I am able to ping the server via terminal

ping smtpout.secureserver.net

Just like other issues posted I can retrieve mail but not send.
BTW this is a web-based email account through GoDaddy the servers are:
pop.secureserver.net
smtpout.secureserver.net

I am stumped

---

### Post by derekeverett on 2010-03-29
Perhaps you need to change the outgoing mail port?

I have to do that with one of my .com email accounts.

The default is port 25 I believe and I have to change it. The faq section of your mail providers web site may have the answer if that is indeed the problem.

---

### Post by lisati on 2010-03-29
> **derekeverett said:**
> Perhaps you need to change the outgoing mail port?

I have to do that with one of my .com email accounts.

The default is port 25 I believe and I have to change it. The faq section of your mail providers web site may have the answer if that is indeed the problem.

+1. 

Some ISPs block traffic on port 25. 

A couple of links:
[http://www.postcastserver.com/help/Port_25_Blocking.aspx](http://www.postcastserver.com/help/Port_25_Blocking.aspx)
[http://help.godaddy.com/article/122](http://help.godaddy.com/article/122)

---

### Post by Nisal on 2010-03-29
well i guess thunderbird will be optional nd better tool than evolution

---

### Post by RTrev on 2010-03-29
I played with Evolution briefly before dumping it, and found that the only way to specify the alternate smtp port was by appending it to the smtp server name:

Ex: smtp.somebody.com:587

587 is the port I see used most often, so you might try that.

---

### Post by derekeverett on 2010-03-29
> **Nisal said:**
> well i guess thunderbird will be optional nd better tool than evolution

I have to admit I use Thunderbird now...

But my solution posted earlier has worked for me with Evolution.

---

### Post by Nisal on 2010-03-29
> **derekeverett said:**
> I have to admit I use Thunderbird now...

But my solution posted earlier has worked for me with Evolution.

yeah it workes for me too i just give a optional idea bcz i got several issues with evolution but i never got a problem with thunderbird

---

