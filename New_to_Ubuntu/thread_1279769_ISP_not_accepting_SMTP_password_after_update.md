---
title: "ISP not accepting SMTP password after update"
date: 2009-10-01
forum: New to Ubuntu
---

### Post by dbuehler on 2009-10-01
Hi All,

My e-mail was working fine yesterday but today I get an error message "unable to authenticate to SMTP server.  Bad authentication response from server."

The only thing I know that has changed is that I ran update manager this morning.  I have two different accounts, one uses evolution and one uses thunderbird.  Neither will accept my password.  I logged in via web mail and verified that the passwords work there.

I also have an XP box and verified that it connects correctly so I do not believe the ISP is at fault.  My ISP is roadrunner and I am running Ubuntu 9.04.

Does anyone have any suggestions?

Thanks.

Dan

---

### Post by LewRockwell on 2009-10-01
you'll need to resolve any discrepencies with your advanced settings in both email programs and you might check your network settings also

seems there are many strange things happening on the interwebs these days

.

---

### Post by jonobr on 2009-10-01
maybe you could try command line debugging

If you open a terminal
and try to telnet to the ISPs smtp server.

it would me something like
telnet smtp.roadrunner.com 25

(im assuming here that port 25 is the smtp port being used and smtp.roadrunner.com is the isp smtp server address.)

See if you get a response.
WEbmail would work as its using an interim application to work between you and the server.

Im also guessing receiving email works ok also?

---

### Post by wrobin1 on 2009-10-01
I had this same problem, also connecting to smtp.roadrunner.com.  Incoming mail worked fine, but outgoing gave the "unable to authenticate" error.  I hadn't changed anything, and it had previously worked just fine.  I installed the latest-and-greatest updates from Ubuntu, rebooted, and the error resolved itself.

Good luck!

---

### Post by dbuehler on 2009-10-01
Thanks for all the responses but it looks like it may have been an ISP problem after all.  I don't understand why but it works OK now.  Sorry for the bother.  You are correct, some strange things are happening.

Thanks again.

---

