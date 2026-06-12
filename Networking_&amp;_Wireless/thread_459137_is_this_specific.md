---
title: "is this specific"
date: 2007-05-30
forum: Networking &amp; Wireless
---

### Post by petercarter on 2007-05-30
peter@peter-desktop:~$ cd ndiswrapper-1.44
peter@peter-desktop:~/ndiswrapper-1.44$ sudo -l
Password:
User peter may run the following commands on this host:
    (ALL) ALL
peter@peter-desktop:~/ndiswrapper-1.44$ make uninstall
NOTE: Not all installed files are removed, as different distributions install ndiswrapper files at different places.
Run uninstall as many times as necessary until no "removing" messages appear below.
removing /lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/bin/rm: cannot remove `/lib/modules/2.6.20-16-generic/kernel/ubuntu/misc/ndiswrapper/ndiswrapper.ko': Permission denied
make: *** [uninstall] Error 1
this is what I get

---

### Post by khardbored on 2007-05-30
Maybe just try sudo make uninstall

---

### Post by petercarter on 2007-05-30
thank you it worked this time (but I tried it earlier and it did nothing. This time I can continue hoping there is no more idiot problems. I am new at linux so I will encounter many problems hopefully I can solve them by myself.
Thankx peter

---

