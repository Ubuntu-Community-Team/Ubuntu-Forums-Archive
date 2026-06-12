---
title: "Standby &amp; Hibernate not working"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by mern1 on 2009-01-27
I recently installed 8.10 on my custom built desktop. Almost everything works great except for standby and hibernate. When I select either, the monitors and hard drives will turn off but everything else is powered on (including all fans) and the case power light remains on. Then it gets really weird. I am unable to restart the computer. Pressing the power button does nothing. The only thing I can do is hold the power button down in order to do a hard shutdown and then restart. Needless to say, this is a huge inconvenience. Any and all help is appreciated. Thanks

---

### Post by taurus on 2009-01-27
Open a terminal and post the output of this command to see how much swap space you have created.

Applications -> Accessories -> Terminal
```
free -m
```

---

### Post by mern1 on 2009-01-27
```
 total       used       free     shared    buffers     cached
Mem:          2024       1949         74          0        626        748
-/+ buffers/cache:        573       1450
Swap:         3812          1       3810

```

---

### Post by mern1 on 2009-01-27
It looks to me like the amount of swap space isn't an issue.  Any other thoughts?

---

