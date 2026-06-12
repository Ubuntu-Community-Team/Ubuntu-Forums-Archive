---
title: "Postfix Weirdness"
date: 2008-03-22
forum: Networking &amp; Wireless
---

### Post by jknotzke on 2008-03-22
Hi,

  Testing my satellite configured postfix installation, I sent an email to myself.. Checking the logs, I was shocked to see:

Mar 22 16:51:32 shampoo postfix/smtp[3489]: 5D89A24293D: to=<jknotzke@yahoo.com>, orig_to=<jknotzke@shampoo.ca>, relay=relais.videotron.ca[24.201.245.36]:25, delay=0.15, delays=0.01/0.01/0.04/0.09, dsn=2.5.0, status=sent (250 2.5.0 Ok.)

  Nowhere in my mail did I enter [email]jknotzke@yahoo.com[/email]. Yet, it's sending it there.. Sure enough, checking my yahoo account, the mail is in fact there.

   Any ideas why ? Is this sent in the DNS somewhere ? How can I test for this using dig ?

   Thanks

   J

---

### Post by zazuge on 2008-04-30
i PRESUME the myorigin parameter in /etc/postfix/main.cf is set to @yahoo.fr
so all mail that is sent throught postfix have it FROM field rewriten
this kind of config is used when you have a dynamic IP ,all mail relays (maybe not all) will check the from to see from what domain the mail did come ,so if the domain is unkown the mail is considered spam ASAP
it's not the only thing but somtimes you have to relay your mail with authentication so that mail won't be considered spam

---

