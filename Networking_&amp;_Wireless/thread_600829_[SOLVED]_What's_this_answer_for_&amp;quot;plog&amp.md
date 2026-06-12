---
title: "[SOLVED] What's this answer for &amp;quot;plog&amp;quot;?"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by Friccy on 2007-11-02
Dear all!
I can not make my Ubuntu 7.10 connect to the internet.
After I have done everything at pppoeconf, for the "plog" command I have this:
csalad@NagyGep:~$ plog
Nov  2 22:13:35 NagyGep pppd[5366]: Remote message: ^M^JAccess denied (external check failed).^J
Nov  2 22:13:35 NagyGep pppd[5366]: PAP authentication failed
Nov  2 22:13:35 NagyGep pppd[5366]: Connection terminated.
Nov  2 22:13:37 NagyGep pppd[3954]: PPP session is 1912
Nov  2 22:13:37 NagyGep pppd[3954]: Using interface ppp0
Nov  2 22:13:37 NagyGep pppd[3954]: Connect: ppp0 <--> eth0
Nov  2 22:13:37 NagyGep pppd[3954]: Remote message: ^M^JAccess denied (external check failed).^J
Nov  2 22:13:37 NagyGep pppd[3954]: PAP authentication failed
Nov  2 22:13:37 NagyGep pppd[3954]: Connection terminated.
Nov  2 22:13:37 NagyGep pppd[3954]: Exit.

What's this?
Why is that I can't connect to the net and the Xp on the same machine can?!
 Thanks!

---

### Post by Stemp on 2007-11-02
I guess it's only a username/password error.
Check them again, or add the complete username [email]username@provider.com[/email]

---

### Post by Friccy on 2007-11-02
Thanks!
But I have a broadband connection with a username like MS1234567 and a password like 9876543.
I am using this for the XP also.
And intersting part is that it worked this way on an older Ubuntu (6.06 I think).
But now, no!
What can I do to connect to the internet?

---

### Post by Friccy on 2007-11-02
> **Stemp said:**
> I guess it's only a username/password error.
Check them again, or add the complete username [email]username@provider.com[/email]

Thanks!
But I have a broadband connection with a username like MS1234567 and a password like 9876543.
I am using this for the XP also.
And intersting part is that it worked this way on an older Ubuntu (6.06 I think).
But now, no!
What can I do to connect to the internet?
__________________

---

