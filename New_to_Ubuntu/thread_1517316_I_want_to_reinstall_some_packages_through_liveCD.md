---
title: "I want to reinstall some packages through liveCD"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-24
I did a big mistake when i installed new system tools to my ubuntu 10.4 and that cause some problems preventing me from log on in the system
so how to fix this with the liveCD or rescue mode or something else 
neeeed help

---

### Post by friv_livs on 2010-06-24
First try "fix broken packages" from the recovery menu.

If that doesn't work, and you know the package names, go to root shell in recovery menu and ```
apt-get remove --purge "package_name"
```

If that doesn't work, try chroot ing into your ubu drives from the liveCD, and run the root shell commands.

Hope this helps.

---

