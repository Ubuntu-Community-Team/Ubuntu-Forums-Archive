---
title: "After installed LAMP, i cannot connect localhost"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by jsun87 on 2011-05-09
Hi Good day, all expert. I'm suffering a problem right now. I cannot connect my localhost after installed LAMP. Here is the screenshot after i press enter into localhost.

---

### Post by lmarmisa on 2011-05-09
Welcome to the forums.

According to your screenshot you are unable to connet to phpmyadmin. Do you get the same problem connecting to [http://localhost](http://localhost) ?

---

### Post by satanselbow on 2011-05-09
have you restarted apache?

```
/etc/**init**.**d**/**apache2 restart**
```

Could/can you connect to localhost or 127.0.0.1 at all? Are you running virtualhosts? 

Rather need to know more about your setup before any useful help can be offered ;)

---

### Post by falko on 2011-05-09
Is your LAMP stack installed on the same system? (Otherwise localhost won't work.)

What's the output of ```
netstat -tap
``` on your LAMP system? Also make sure that port 80 is open in your firewall (if your firewall is on).

---

