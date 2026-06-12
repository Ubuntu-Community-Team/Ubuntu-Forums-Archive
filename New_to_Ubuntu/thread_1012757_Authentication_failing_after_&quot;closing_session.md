---
title: "Authentication failing after &quot;closing session&quot;"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by thimad on 2008-12-16
I use intrepid and I selected an option to login automatically (without asking for a password).

It works.

But if I manually go to System > Close Session (my language is not english, so it may be something different), then I get the login screen with a popup saying:

Authentication Failed (again, my system is not in english, so it may be different).

If I click OK, it shows again, and I can't even write my username and password.

My only option is to CTRL-ALT-F1, sudo reboot.

Any help?

Thanks,
Thiago.

---

### Post by rlunger on 2008-12-17
> **thimad said:**
> I use intrepid and I selected an option to login automatically (without asking for a password).

It works.

But if I manually go to System > Close Session (my language is not english, so it may be something different), then I get the login screen with a popup saying:

Authentication Failed (again, my system is not in english, so it may be different).

If I click OK, it shows again, and I can't even write my username and password.

My only option is to CTRL-ALT-F1, sudo reboot.

Any help?

Thanks,
Thiago.

If you've set it to log you in automatically, when you close the session, it will log you out, and then immediately try to log you back in.  My guess is that your authentication info (username and password) don't make it back through the second time and the login screen is stuck in an error loop (trying to log you in automatically without the info).  If you want to log in automatically, you will have to do a shutdown or just stay logged on - I don't think the login manager will be able to tell when you want to be logged in automatically and when you don't.

---

