---
title: "How to restore /etc/init.d/shutdown script?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by lemuriens on 2011-01-24
Hello all,

I was copying a script to /etc/init.d/ and I accidentally overwrote the shutdown script. Is there a package I can reinstall through apt to correct this error?

Thanks!

---

### Post by Claus7 on 2011-01-24
Hello,

I would start reinstalling initscripts package from synaptic.

Hope it helps,
Regards!

---

### Post by lemuriens on 2011-01-25
I tried this but still no /etc/init.d/shutdown file. Is there another copy elsewhere, or one I could download?

---

### Post by Claus7 on 2011-01-26
Hello,

searching my ubu box about shutdown this is what I got:
> /usr/share/gnome/shutdown
/sbin/shutdown

I should go to synaptic and choose the upstart package to be reinstalled. 

Inside /etc/init.d files I was not able to find one with that name...

Regards!

---

