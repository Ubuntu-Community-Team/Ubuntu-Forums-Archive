---
title: "Locked in safe graphics mode"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Drawstop on 2009-12-07
I have Ubuntu on my old Toshiba Satellite laptop.  I seem to have booted in safe graphics mode and cannot get to any other resulution. Nothing will install from the disc drive and I desperately need some advice.  I am a senior citizen (77) and do not understand technical terms so please could any advice be simple?
Many thanks in advance.
Regards. Richard.

---

### Post by cariboo on 2009-12-11
We need to know what graphics adapter your laptop has. Could you open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C display
```

enter your password when asked. The above command will display the details of your graphics adapter. Could you please paste the output into your next post.

---

