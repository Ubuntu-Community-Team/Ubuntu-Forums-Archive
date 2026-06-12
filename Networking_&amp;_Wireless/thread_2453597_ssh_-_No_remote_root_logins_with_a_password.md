---
title: "ssh - No remote root logins with a password"
date: 2020-11-13
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2020-11-13
I feel a bit silly asking this but the more I read the more confused I get.   If I uncheck line 34 in /etc/shh/sshd_config so it now reads:

#LoginGraceTime 2m
PermitRootLogin prohibit-password
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

have I achieved the situation that root access cannot log on by using a password - I assume if root wanted to log it would have to use ssh keys if they were set up for said connection.  Also - should the grace time of 2m be lowered to say, 1m?

---

