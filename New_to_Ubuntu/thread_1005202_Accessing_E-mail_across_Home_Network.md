---
title: "Accessing E-mail across Home Network"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by rlogan on 2008-12-08
Hi all

We currently use one PC with Ubuntu to download our email addresses from our ISP, there is 3 POP3 email accounts and also 2 Gmail accounts. 

Now what I would like to achieve is a setup so that each user can access their own emails from whatever PC they happen to login from.

I have thought about setting each pc to login into the current mail machine (for lack of a better term) or would it be better to setup a mail server ? I have been playing around with dovecot and postfix but I have never setup a mail server and to say the least I don't think I am winning !

Suggestions would be greatly appreciated !!!!

Many thanks

Richard

---

### Post by nhasian on 2008-12-08
any chance you can switch the pop3 accounts to IMAP?  then you can access the emails from any computer.

---

### Post by rlogan on 2008-12-08
Unfortunately I cannot change them to IMAP, the ISP only uses POP3 accts. These accounts are downloaded to one machine only.

Cheers

---

### Post by nhasian on 2008-12-09
no IMAP? no problem!  forward your emails to your gmail account.  use an alias to help filter your messages to the correct labels:

[http://mail.google.com/support/bin/answer.py?hl=en&answer=12096](http://mail.google.com/support/bin/answer.py?hl=en&answer=12096)

or manage multiple email accounts as described here:

[http://lifehacker.com/software/gmail/hack-attack-become-a-gmail-master-161399.php](http://lifehacker.com/software/gmail/hack-attack-become-a-gmail-master-161399.php)

---

### Post by rlogan on 2008-12-10
Your suggestion is certainly worth considering, it would certainly would work but it would be nice to link it into evolution with calender etc.

Many thanks

Richard

---

