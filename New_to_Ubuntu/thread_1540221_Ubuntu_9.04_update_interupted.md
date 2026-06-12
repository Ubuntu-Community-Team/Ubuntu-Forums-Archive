---
title: "Ubuntu 9.04 update interupted"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by Kurt_daddy on 2010-07-27
last night I was doing the update for ubunt 9.04 jaunty jackalope and I lost power at my house before it was completed. when I turned the modem back on after power was restored the monitor stayed black but the modem was running. how do I fix this problem? please advise.

---

### Post by candtalan on 2010-07-27
One thought:
When booting up, do you see the grub choices which include the 'Recovery Mode'? If you see this, then choose the recovery mode nearest the top. You may see an option to repair broken packages, which might be worth trying (use the tab key to navigate)

Another thought:
If you press keys 
CTRL and ALT and F1
at the same time, do you see a command prompt on the monitor screen?
If you do, then this is a form of terminal and can be used to run commands which could do a repair. Other responses here might help with that.

hth

---

### Post by linux18 on 2010-07-27
THE FIX ALL SYNAPTIC PROBLEMS COMMANDS:
```

 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"
 sudo apt-get -f || echo "ERROR 8"

```it includes error codes as well for debugging problems
just run ```
 sudo apt-get dist-upgrade 
``` afterwards to finish your 9.10 to 10.04 upgrade

---

