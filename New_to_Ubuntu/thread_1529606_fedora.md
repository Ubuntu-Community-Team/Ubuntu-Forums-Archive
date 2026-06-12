---
title: "fedora"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by pgolphin on 2010-07-12
how can i find my password inside the fedora terminal if i forgot it?

---

### Post by Simian Man on 2010-07-12
You can't do that with any Linux system, even root can't read passwords.  If you still remember the root password, you can reset your user password with:
```

su -
passwd [your user name]

```

---

### Post by Crunchy the Headcrab on 2010-07-12
Also, it might be worth setting up sudo in fedora.  I find that Ubuntu has made me very fond of using sudo instead of root simply for the timeout feature.

---

