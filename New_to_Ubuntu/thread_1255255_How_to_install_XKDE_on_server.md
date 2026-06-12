---
title: "How to install X/KDE on server"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by bardov on 2009-09-01
I installed 9.04 server. Now I want to install/configure X/KDE.
What's the proper way to do it?

I installed kde using apt-get, it installed fine, and startx works, but my xorg.conf is empty,
the resolutions are wrong, and I don't want to manually create xorg.conf.

Thanks,
Dan

---

### Post by nikhilbhardwaj on 2009-09-01
you may want to install kdm
to autostart kde

to configure X
as root

```

Xorg -configure

X -config ~/xorg.conf.new

cp xorg.conf.new /etc/x11/xorg.conf
chmod 644 /etc/x11/xorg.conf


```

---

### Post by bardov on 2009-09-01
Thanks, that worked.

---

