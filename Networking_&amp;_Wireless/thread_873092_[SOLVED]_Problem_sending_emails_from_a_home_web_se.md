---
title: "[SOLVED] Problem sending emails from a home web server, I think I look like SPAM :("
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by loso on 2008-07-28
hey everyone,
Here's my situation and problem, and I hope you can help...

I'm hosting a drupal 6.3 website on my home computer (Ubuntu hardy desktop), and I'm connecting to the internet with a DSL residential ISP. My ISP isn't blocking port 25.

My website requires new users to create an account, and validate it via automated email. The problem I'm getting is that although Drupal is responding that an email has been sent, the email is not being received. When I look at my www-data email log, I find that the emails are being rejected by the receiver because:

```
<s_acker@alcor.concordia.ca>: host capone.concordia.ca[132.205.7.82] said: 554
    5.7.1 reject: Client host bypassing service provider's mail relay:
    ip-240.86.126.206.dsl-cust.ca.inter.net (in reply to end of DATA command)

```
Is there any way to get around this problem?  I'm not spam, really!

---

### Post by netztier on 2008-07-28
> **loso said:**
> Is there any way to get around this problem?  I'm not spam, really!

A lot of e-mail servers are refusing mail that is sent from IP addresses that are known to be of the "dialup or home user" kind, and rightly so.

A possible solution is  - while still running your own server - to forward all your outgoing mail to your ISP's SMTP smart host. If they're a good ISP, they'll be running such a service, most probably free for you to use. 

regards

Marc

---

