---
title: "PHP Mail"
date: 2010-09-04
forum: New to Ubuntu
---

### Post by adamjkok on 2010-09-04
Okay, so I installed LAMP on my desktop using tasksel, and I was wondering if PHP will, by default, allow scripts (PHPBB, Concrete5, etc...) to send mail for password resets and stuff. If not, how do I fix this?

---

### Post by sandyd on 2010-09-04
> **adamjkok said:**
> Okay, so I installed LAMP on my desktop using tasksel, and I was wondering if PHP will, by default, allow scripts (PHPBB, Concrete5, etc...) to send mail for password resets and stuff. If not, how do I fix this?
you need to make sure sendmail (or postfix is installed)
if it is, it will work.

---

### Post by lisati on 2010-09-04
If I've understood the documentation at [http://help.ubuntu.com](http://help.ubuntu.com) properly, if you have postfix installed (comes as standard with a LAMP install), you'll have sendmail compatibility. 

I've got phpBB up and running on my server, which has Postfix on it, and it seems to be able to send email without any hassle.

---

### Post by adamjkok on 2010-09-05
> **lisati said:**
> If I've understood the documentation at [http://help.ubuntu.com](http://help.ubuntu.com) properly, if you have postfix installed (comes as standard with a LAMP install), you'll have sendmail compatibility. 

I've got phpBB up and running on my server, which has Postfix on it, and it seems to be able to send email without any hassle.
So let's say that you ISP blocks port 25 except for their own SMTP server... same story?

---

### Post by lisati on 2010-09-05
> **adamjkok said:**
> So let's say that you ISP blocks port 25 except for their own SMTP server... same story?

My ISP blocks port 25 in both directions (incoming and outgoing) by default. What wasn't obvious from their self-help page for unblocking it was that they expected me to pay extra each month for a static IP address before the unblocking would work, and to fill in a questionaire about what kind of software I'd be running on the server.

There are options if getting getting port 25 unblocked is a hassle. One would be to use your ISP's server as a relay for outgoing emails, and to use "fetchmail" to pull in email from an external email account. Personally, I'm not keen on the fetchmail option, because I like having the extra options available with a direct connection, e.g. using a DNSBL service such as Spamcop as a factor in deciding to reject spam during the SMTP dialog.

---

### Post by adamjkok on 2010-09-05
> **lisati said:**
> My ISP blocks port 25 in both directions (incoming and outgoing) by default. What wasn't obvious from their self-help page for unblocking it was that they expected me to pay extra each month for a static IP address before the unblocking would work, and to fill in a questionaire about what kind of software I'd be running on the server.

There are options if getting getting port 25 unblocked is a hassle. One would be to use your ISP's server as a relay for outgoing emails, and to use "fetchmail" to pull in email from an external email account. Personally, I'm not keen on the fetchmail option, because I like having the extra options available with a direct connection, e.g. using a DNSBL service such as Spamcop as a factor in deciding to reject spam during the SMTP dialog.
So, in other words, the PHP mail function *does* require port 25... correct?

And how would I use my ISP's SMTP server to relay messages? I have the settings and it doesn't require authentication.

---

### Post by sandyd on 2010-09-05
> **adamjkok said:**
> So, in other words, the PHP mail function *does* require port 25... correct?

And how would I use my ISP's SMTP server to relay messages? I have the settings and it doesn't require authentication.
just set the smtp server to your ISPS.
then use any email you like for the "from" thingy (board email from, it might be called"

---

