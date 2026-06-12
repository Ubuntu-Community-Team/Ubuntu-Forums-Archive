---
title: "Problem with likewise open and cached credentials"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by ducheus on 2008-11-18
Hi,
i have the following problem with likewise open. I installed Intrepid with ADS integration using likewise open (ubuntu delivered version). The configuration runs fine, the machined is joined to the domain and when a user log in when the DC is available, the things run smoothly.
The problem began when I try to log in when the computer can not reach the DC. The behavior is:

1. The machine displays the message indicating that cached credentials are in use, accept the password (if correct) and proceed to log in.
2. After login, the home directory should be /home/domain/user, However, the home directory is in all cases /home/domain/admin_user where admin_user is the user created when the OS was installed.

Due this condition, all the configuration in the /home/domain/user is not loaded and the functioning is partial.

Any help to correct this issue will be vry helpful.

Regards, Duche:)

---

