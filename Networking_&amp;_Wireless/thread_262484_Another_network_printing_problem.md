---
title: "Another network printing problem"
date: 2006-09-21
forum: Networking &amp; Wireless
---

### Post by russellb on 2006-09-21
Hi all,

I hope all I need is someone to look at my cupsd.conf file and point out what I have not been able to see, but I have few enough hairs now, and the supply is rapidly diminishing.
I have Kubuntu Dapper 6.06  (AMD64) fully updated on my desktop, and Ubuntu server 6.0.6 on a Dell running as mail/web/print server (if I get the printing running)

I have attached to the Dell server a Samsung SXC4521 on USB, but am having a pain getting it to print. I managed briefly to get it printing, but after  trying to enable Samba from my wife's Win XP box,  I can't even print test pages any more.

Typical error in /var/log/cups/error.log is:
 Started filter /usr/lib/cups/filter/pstops (PID 19138) for job 108.
I [21/Sep/2006:23:00:43 +1000] Started filter /usr/lib/cups/filter/rastertosamsungspl (PID 19139) for job 108.
I [21/Sep/2006:23:00:43 +1000] Started backend /usr/lib/cups/backend/mfp (PID 19140) for job 108.
E [21/Sep/2006:23:00:44 +1000] PID 19140 (/usr/lib/cups/backend/mfp) stopped with status 2!
I [21/Sep/2006:23:00:44 +1000] [Job 108] Backend returned status 2 (authentication required)

Increasing log level was not informative.

Cups version is 1.2.2 on both machines.

It seems a problem with authenticating the user. I tried setting AuthType to None, but that dis not seem to help.


 I will attach a copy of cupsd.conf, if a fresh and more knowledgable pair of eyes could look over it and suggest what I am doing wrong.

Thanks for any and all help

Russell

---

