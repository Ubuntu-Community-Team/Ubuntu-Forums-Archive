---
title: "IMAP Referral server issue"
date: 2007-10-08
forum: Networking &amp; Wireless
---

### Post by kwr2k on 2007-10-08
Hi,
 My IMAP server at work has switched to REFERRAL scheme where it redirects the IMAP request to another server. The trouble is, my standard login procedure does not work anymore.
 KMail/Evolution gives me the following error:
 
 Authorization failed, Unable to login. Probably the password is wrong.
 The server SERVER1 replied:
 [REFERRAL imap://DOMAIN%2FUSERNAME;AUTH=*@SERVER2/] The requested mailbox is not available on this server. authentication not supported
 
 Until sometime ago, SERVER1 was the mail server, now it seems its not and I cannot set SERVER2 directly in KMail as its not reachable directly across the network.
 
 Please reply if you need more info. I am trying to avoid booting into Windows if I can to access my mail. As of now, I can use web based email but that has a very short session timeout so pretty much useless for regular work.
 
 The mail server is Exchange V 8.0.
 
 Thanks.

---

