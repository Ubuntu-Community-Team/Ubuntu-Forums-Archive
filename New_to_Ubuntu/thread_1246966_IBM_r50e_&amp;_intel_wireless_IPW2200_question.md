---
title: "IBM r50e &amp; intel wireless IPW2200 question"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by daimonas on 2009-08-22
hello. Im using jaunty on this laptop and it works great.
the wireless adapter was automatically installed by ubuntu and thank god this driver improved the range at least 50% but i found that there are more drivers available on the internet to compile. My question is how can i know what driver ubuntu us using right now for this adapter? is there a command?

---

### Post by AClark on 2009-08-22
This command will list all your network interfaces with lots of info including the driver:

```
lshw -C network
```

---

### Post by daimonas on 2009-08-22
Ok that helped a lot! thanks Aclark! linux rocks!

---

