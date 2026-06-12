---
title: "Network Manager Dosent show Wi-Fi"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-02-20
I was trying to crack my AP's WEP, but I did a bunch of crap with my wifi driver and I coundent get it in moniter mode. Anyway, after I resarted, Network manager dident show wifi. I ran this:

```
nm-applet --sm-disable
```

and it fixed it. Then I added it to sessions and it didnt work after a restart, I had to type it out in the terminal. Any ideas?

---

### Post by tarps87 on 2009-03-12
Have you added it as a program or a command, you might what to try adding the full path.
This will show you the full path
```
which nm-applet
```

---

