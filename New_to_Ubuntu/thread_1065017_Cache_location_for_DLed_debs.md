---
title: "Cache location for D/Led debs"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by mac9416 on 2009-02-09
Where does Synaptic/apt-get cache downloaded debs before installing? Thanks!

---

### Post by drs305 on 2009-02-09
/var/cache/apt/archives

---

### Post by mac9416 on 2009-02-09
Slow day in forum-world! That's OK, an IRC dude pointed me here: /var/cache/apt/archives
The debs stay there 30 days or until you 'apt-get clean' them.
Hope that helps someone else too!

---

