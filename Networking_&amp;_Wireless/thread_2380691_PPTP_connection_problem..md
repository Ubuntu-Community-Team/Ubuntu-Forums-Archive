---
title: "PPTP connection problem."
date: 2017-12-20
forum: Networking &amp; Wireless
---

### Post by g0td0pe on 2017-12-20
I registered an account with PureVPN and setup the PPTP connection on my Ubuntu 16.04.03 LTS following the instructions in this page:

[https://support.purevpn.com/pptp-configuration-guide-for-ubuntu](https://support.purevpn.com/pptp-configuration-guide-for-ubuntu)


Whenever I am try to connect I end up not being able to do so. Here is a screenshot:

[https://imgur.com/a/IJPIU](https://imgur.com/a/IJPIU)


Here is a screenshot too for the connection's details:

[https://imgur.com/a/NwdgX](https://imgur.com/a/NwdgX)


I tried to set the security to "All Available (Default)", but still couldn't connect.



My firewall is turned off too:

[https://imgur.com/a/i4hjr](https://imgur.com/a/i4hjr)



What do you think is the problem?

---

### Post by TheFu on 2017-12-21
Cannot help with pptp. Did you check the logs?

PPTP is a broken protocol and has been for over a decade.  In 2012, hacking it became REALLY easy. Best to use almost anything else - IPSec being the best for today.  [https://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html](https://www.computerworld.com/article/2505117/cyberwarfare/tools-released-at-defcon-can-crack-widely-used-pptp-encryption-in-under-a-day.html)

---

### Post by g0td0pe on 2017-12-21
Even when used with a VPN service like PureVPN?

---

### Post by TheFu on 2017-12-21
> **g0td0pe said:**
> Even when used with a VPN service like PureVPN?

Yes.  If you want an unencrypted tunnel, pptp is fine.  If you want encryption that isn't possible to break in 3 minutes, don't use PPTP.

---

