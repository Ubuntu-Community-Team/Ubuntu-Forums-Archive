---
title: "Fully Purging Virtual Box 2.1 from my system"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-13
So VB is not working at all, it started when I updated my video drivers, but reverting the drivers has not worked. So I want to try removing all traces of VB and try a fresh install (figure maybe that will help) apt-get remove didn't work, is there a better way to fully remove it? (I am using the non-OSE version, 2.1)

Thanks,
~Jeff

---

### Post by cerealtx on 2009-02-14
sudo apt-get remove --purge <package>

---

