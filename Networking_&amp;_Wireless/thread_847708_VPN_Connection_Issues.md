---
title: "VPN Connection Issues"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by shozzbott on 2008-07-02
I am brand new to Ubuntu, brand new to Linux, and a total non-technical user, so be gentle in any response. First, I love this OS and the apps that go with it...Ubuntu's newest big fan. Having said that I cannot get a VPN Connection to work with my place of employment.

The basics:
-Hardy Heron (8.04) installed and up-to-date.
-After reading some forum issues I located and installed the Network-Manager-pptp package.
-I configured a VPN connection with our company 'address.'
-I saw the selection in Network Manager (after I rebooted).
-When I crank the connection up the system spins for a couple of minutes then tells me that the connection failed. No reason or error code is provided.

Any ideas for the hopelessly lame?

---

### Post by enopepsoo on 2008-10-28
It's annoying that it doesn't give the reason why it failed, isn't it?

You can check /var/log/syslog for what is wrong:```
tail -f /var/log/syslog
```

This didn't particularly help me though.  I ended up having to enable encryption on the options form.  With encryption enabled it worked fine.:KS

---

