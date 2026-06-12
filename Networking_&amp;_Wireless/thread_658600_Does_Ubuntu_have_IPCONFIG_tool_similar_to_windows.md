---
title: "Does Ubuntu have IPCONFIG tool similar to windows ?"
date: 2008-01-04
forum: Networking &amp; Wireless
---

### Post by picard12 on 2008-01-04
[SIZE="4"]  Does Ubuntu have IPCONFIG tool similar to windows ?[/SIZE]

I checked the add/remove tool in Ubuntu for this feature but I couldn't find it. 

where can I get this tool to refresh my network connection ?

---

### Post by whittler on 2008-01-04
The equivalent Linux command is ifconfig

There would be other better equipped than me to explain it, I don't know much about networking.

Try the command:```
 ifconfig eth0 up
```

---

### Post by kevdog on 2008-01-04
Yes commands that are similar are

ifconfig
iwconfig (for wireless connections)

Although they appear similar on the surface, they are much more powerful than windows. Hate to tell you to do this, but the man pages on ifconfig and iwconfig will tell you a lot.

---

### Post by picard12 on 2008-01-05
> **kevdog said:**
> Yes commands that are similar are

ifconfig
iwconfig (for wireless connections)

Although they appear similar on the surface, they are much more powerful than windows. Hate to tell you to do this, but the man pages on ifconfig and iwconfig will tell you a lot.

Where do I type in the command in Ubuntu?
 Is there a DOS prompt screen?

---

### Post by slolerner on 2008-01-05
still new to linux, but your "cmd" window is under applications>accessories>terminal

best of luck

---

