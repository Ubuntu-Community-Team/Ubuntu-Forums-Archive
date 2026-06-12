---
title: "I Want To Make This Terminal Command a Startup Script"
date: 2007-09-12
forum: Networking &amp; Wireless
---

### Post by R-Dot-Yung on 2007-09-12
When i boot up my Laptop, i have to enter this command into the terminal in order to have wireless internet...

sudo modprobe bcm43xx

how can i make this start up on every new session...aka how do i make this an executable...aka, please help you know what i mean, hahaha

---

### Post by Bachstelze on 2007-09-12
```
echo "bcm43xx" | sudo tee -a /etc/modules
```

---

