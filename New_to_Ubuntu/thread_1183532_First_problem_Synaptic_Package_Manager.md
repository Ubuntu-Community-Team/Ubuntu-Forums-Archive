---
title: "First problem Synaptic Package Manager"
date: 2009-06-10
forum: New to Ubuntu
---

### Post by Anybloodyid on 2009-06-10
Hi
When I try to load the SPM I get this alert

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
```

I can see what it wants me to do but how do I do it?

Thanks

---

### Post by Troll_the_Great on 2009-06-10
Hy! Just open a terminal from Applications - Accessories - Terminal and run that command:```
sudo dpkg --configure -a
```
Post back if you have other problems.
Cheers!

---

### Post by taseedorf on 2009-06-10
I have found that sometimes the problem needs to be rectified other ways sometimes, such as running that command will not fix your problem, and if that is the case, please post again!

---

### Post by Anybloodyid on 2009-06-10
Thanks
Run the command and rebooted 
SPM is now back to normal.

---

### Post by billgoldberg on 2009-06-10
> **Anybloodyid said:**
> Thanks
Run the command and rebooted 
SPM is now back to normal.

The reboot wasn't neccesary.

---

### Post by Anybloodyid on 2009-06-10
The reboot was neccesary.
After I run the command SPM still did not work so I rebooted and it did.

---

