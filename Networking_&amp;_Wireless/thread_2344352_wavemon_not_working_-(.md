---
title: "wavemon not working :-("
date: 2016-11-24
forum: Networking &amp; Wireless
---

### Post by john163 on 2016-11-24
I just installed wavemon 0.7.6 on Ububtu 14.04  Every resource I can find says to start it and it goes.  When I start it, I get NO INTERFACE DATA.  Going to F3 "scan" tells me, "This screen requires CAP_NET_ADMIN permissions".  If I start it with sudo, F3 says "Scan failed on wlan0mon: Operation not supported"  And if I press F1 to try to get back to Info, I get the GNOME Terminal Manual open in another window :-/  I can 'sudo iw dev wlan0 scan' and 'iwlist wlan0 scan' and get results.  Googling cap_net_admin didn't help:

```
joliver@ubuntu2:~$ getcap /usr/bin/wavemon
joliver@ubuntu2:~$ sudo setcap cap_net_admin /usr/bin/wavemon
fatal error: Invalid argument
usage: setcap [-q] [-v] (-r|-|<caps>) <filename> [ ... (-r|-|<capsN>) <filenameN> ]

 Note <filename> must be a regular (non-symlink) file.
joliver@ubuntu2:~$ ls -l /usr/bin/wavemon
-rwxr-xr-x 1 root root 81208 Mar 27  2014 /usr/bin/wavemon
```

What gives? :-)

---

