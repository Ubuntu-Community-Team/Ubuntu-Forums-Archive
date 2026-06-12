---
title: "implementing pptp server with one time auth using dynalogin or other mobile otp"
date: 2015-11-06
forum: Networking &amp; Wireless
---

### Post by nishir-ji on 2015-11-06
Hi Guys,

Want to implement a pptp server which will authenticate users using any mobile otp solution.. google authenticator or anything else..

please suggest...

---

### Post by Lars Noodén on 2015-11-06
It's probably good to [avoid PPTP](http://www.h-online.com/security/features/A-death-blow-for-PPTP-1716768.html).  It's been unsafe since the beginning.

Depending on your needs, OpenVPN might be an alternative.  It apparently works with OTP and 2FA solutions.

---

