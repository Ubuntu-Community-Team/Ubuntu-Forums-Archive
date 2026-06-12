---
title: "&quot;Authentication required&quot;"
date: 2014-08-30
forum: Networking &amp; Wireless
---

### Post by Broghan on 2014-08-30
I've tried looking around for my problem but everyone else seems to be getting this message at startup. My problem is that my wifi will randomly drop.  My internet connection starts to get weak while I'm using it and then I'll get the message. I've never been asked at startup and the password is always in the field. Can anyone help me out?

---

### Post by ian-weisser on 2014-08-30
'Authentication' sounds like your system is trying to connect to a different, secured network.

---

### Post by Broghan on 2014-08-30
I don't see why it would. My computer is only 2 weeks old and has only been connected to my home network.

---

### Post by grahammechanical on 2014-08-30
But the machine might be in range of the transmissions of other wireless access points. And one of them might be giving a stronger wireless signal than your access point. In fact low signal strength could be a reason for your signal dropping out.

Run this command

```
nm-tool
```

That will show a list of all access points in range of your machine and the signal strengths. Check the frequencies. You may find that there are access points using the same frequency as your access point and if their signal strength is close to your signal strength and that could also be a reason why your wireless connection is dropping out.

Regards.

---

### Post by Broghan on 2014-08-31
Thanks. I didn't know Ubuntu would do that because I've never had Windows try to find a better connection.

---

