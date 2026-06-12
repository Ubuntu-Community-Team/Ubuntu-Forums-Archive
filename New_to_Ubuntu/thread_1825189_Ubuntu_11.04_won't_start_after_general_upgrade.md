---
title: "Ubuntu 11.04 won't start after general upgrade"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by ertoliart on 2011-08-14
I did a general update to my ubuntu 11.04 with the update manager. It worked well after I closed it (the manager), and I turned the computer off normally. The next time I tried to boot ubuntu, it went into the five dots screen (I don't know its name). After this, two things might happen. The first is that the dots continue changing color. As if it were still loading. But they never stop. The user screen never shows up. The second is that the dots stop changing color, but the screen doesn't move. It stays like that. I tried loading the other kernels, and they load well, but I can't enable wireless in them. I tried recovery mode (I had never tried that before), and I think it doesn't load completely. It shows some messages and it just stops after one that says something about skipping firewall. I believe it doesn't load completely because I can't write anything.

---

### Post by waynefoutz on 2011-08-14
> **ertoliart said:**
> I did a general update to my ubuntu 11.04 with the update manager. It worked well after I closed it (the manager), and I turned the computer off normally. The next time I tried to boot ubuntu, it went into the five dots screen (I don't know its name). After this, two things might happen. The first is that the dots continue changing color. As if it were still loading. But they never stop. The user screen never shows up. The second is that the dots stop changing color, but the screen doesn't move. It stays like that. I tried loading the other kernels, and they load well, but I can't enable wireless in them. I tried recovery mode (I had never tried that before), and I think it doesn't load completely. It shows some messages and it just stops after one that says something about skipping firewall. I believe it doesn't load completely because I can't write anything.

I would go back to the latest kernel that works, remove the updated kernel, then go into synaptic package manager and lock your kernel so that it doesn't update again. If you are using a proprietary driver for the wifi, remove it, and install it again.

---

### Post by ertoliart on 2011-08-15
That sounds like a logical solution, but what is a proprietary driver, and how do I remove it? Thanks, by the way.

---

