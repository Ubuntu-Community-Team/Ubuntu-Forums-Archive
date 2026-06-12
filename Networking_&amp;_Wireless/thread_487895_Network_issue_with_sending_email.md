---
title: "Network issue with sending email"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by DaveAK on 2007-06-29
Here's the scenario :

Two computers connected to a Linksys router and to a Road Runner ISP.  One's a Windows desktop (wired), the other an Ubuntu laptop (wireless).  Both receive email just fine, but the Ubuntu one won't send.  We get the following error message : "An error occurred while sending mail. The mail server responded 5.7.1 (recipient email addy here) ... Relaying denied. Please verify that your email address is correct in your Mail preferences and try again."

To rule out email client settings we opened a telnet session to the SMTP server and tried to send email that way.  It worked fine on the Windows machine, but we had the same error after the RCPT TO: command on the Ubuntu laptop.  So what gives?  I'm thinking an underlying difference in how the network is handling things, but I have no clue as to what to look for.

Any suggestions as to what we can try next?

ETA:  Is the SMTP protocol implementation a separate "module", (for want of a better term), in Ubuntu, and could this by itself be causing the problem?  If so is it updatable in some way?  I also don't know which version of Ubuntu it is as it's a friends machine, they're in Hawaii and I'm not. :(  I'll see if I can get that info though.  I do know it's a new Dell laptop with Ubuntu preinstalled.

---

### Post by SingerChick on 2007-06-29
Hi I'm the one DaveAK's writing about (thanks!) with the Dell laptop with Ubuntu pre- installed.  To answer your question, it's the brand new Dell E1505 Inspiron with Ubuntu 7.04, Feisty Fawn, on it.  

Thanks again Dave for your help so far and thanks to anyone who can offer some insights.:)

Amy

---

