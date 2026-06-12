---
title: "Does the netboot iso include a root console?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by Starks on 2009-02-28
Topic.

---

### Post by thtrgremlin on 2009-02-28
Not sure what you mean by netboot iso. The ubuntu live CD's all have consoles (ctl-alt-F1 to F6) and if you want root, just use ```
sudo su
```

Another slightly hidden option on any live CD is to edit the kernel options at the boot menu. For example on any live CD using ubiquity, just hit F6, and change the part at the end > silent splash -- to > single Really convenient! Just a few times I have used that along with 'chroot' to quickly fix some pretty fubar'd systems.

Best luck!

---

### Post by Starks on 2009-02-28
Netboot iso = [http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/jaunty/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by thtrgremlin on 2009-02-28
AH, wow, haven't seen that installer since I used Debian. Anyway, took me a sec to remember, but there is an Ash shell. Anyway...

1. Type install
2. once it gets to the language selection page, press escape
3. from the new menu that comes up, select 'Execute a shell'
4. read the little dialog about what the shell features, and press enter
5. VIOLA! Root Shell.

Included screen shots for fun.

---

