---
title: "how to configure command line mail for reading new emails ?"
date: 2014-09-10
forum: Networking &amp; Wireless
---

### Post by vincentberenz on 2014-09-10
Hi,

I am trying to read/send emails via command line.
I am a gmail user.

The sending part is working fine. I followed the instructions here:
[https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/](https://rtcamp.com/tutorials/linux/ubuntu-postfix-gmail-smtp/)

I can not manage to get the receiving part working.
From searching online, I understood that simply typing "mail" should do it.
But this return "No mail for <myname>", while I know I have new mail on my gmail box.
This is not so surprising, because I did not perform any configuration for receiving mails.

I could not find online any help on how to configure mail to get the mails.

Many thanks

---

### Post by TheFu on 2014-09-11
mail/Mail will only read from /var/spool/mail/userid - it cannot connect to POP or IMAP servers.  For that you need a POP3 or IMAP client.  Sorry, I haven't done this in years and vaguely recall only a few clients - elm, pine, alpine, mutt.  Don't know which handles what protocols.

Or you can setup **fetchmail** to pull gmail local every 30 minutes and use mail or Mail to read and reply.

---

### Post by SeijiSensei on 2014-09-11
**Alpine**, the program formerly known as pine, is an excellent text-mode mail client, but it runs in full-screen mode.  You can install it from the repositories.

---

