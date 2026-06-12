---
title: "lshw?"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by DarinB on 2009-12-12
darin@darin-desktop:~$ lshw > WARNING: you should run this program as super-user  
I understand the warning but why is it bad to run it with out sudo

---

### Post by halitech on 2009-12-12
I'm not sure why the warning as I've run it with and without sudo and the output was identical

---

### Post by falconindy on 2009-12-12
lshw probes parts of the OS that are normally off limits to a normal user. Without elevated permissions, you might not get an accurate representation of the hardware available, or specific device information may be missing.

---

### Post by halitech on 2009-12-12
scratch what I just said. Just did it again now and there are alot of items missing in lshw that do show up in sudo lshw. Guess when I've used it before I wasn't looking as close

---

### Post by DarinB on 2009-12-12
thanks

---

