---
title: "[SOLVED] Has anyone tried Madwifi Release 0.9.4 yet"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by tad1073 on 2008-02-13
Has anyone tried Madwifi Release 0.9.4 yet?  I couldn't get past :
```
cd scripts
./madwifi-unload.bash
```
I got an error saying that wlan0 or something or other was still active. Then I tried:
```
ifconfig wlan0 down
```
it tells me no such device. then i try:
```
ifconfig wlan down
```
and  get the same answer.

Any suggestions?

---

### Post by tad1073 on 2008-02-15
bump...

---

### Post by kevdog on 2008-02-15
Try sudo with the command.  Just use svn sources of madwifi.

---

