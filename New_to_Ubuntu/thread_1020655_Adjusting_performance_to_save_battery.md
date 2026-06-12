---
title: "Adjusting performance to save battery"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by libihero on 2008-12-24
is there any way i can decrease the performance of the computer when it is not plugged in so that i may save battery?

---

### Post by Kosimo on 2008-12-24
> **libihero said:**
> is there any way i can decrease the performance of the computer when it is not plugged in so that i may save battery?

You should give it a try to powertop. (is amazing)

open a terminal: then intall powertop 

```
sudo apt-get install powertop
```

then run it:  ```
sudo powertop
```

It tells you a lot of information regarding the current consumption and all devices that are currently using more resources. It allows you to enable extra saving tricks (you have to hit the letter that powertop suggest)

---

### Post by teh_yodeler on 2008-12-24
System > Preferences > Power Management has a few options, but not too many.:)

---

