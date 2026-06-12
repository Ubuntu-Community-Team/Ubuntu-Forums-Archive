---
title: "Broken Package System"
date: 2011-02-23
forum: New to Ubuntu
---

### Post by whofacke on 2011-02-23
Every time I try to install software or software updates, I get a message that the 'package system' is broken, and nothing can change software-wise until repairs take place. This is my second day of Linux, so of course I have no idea what's wrong or how to fix it. 

I'm running Xubuntu 10.10 on an HP Compaq nx6110, if that matters. 

Any help is appreciated, but layman's terms would be the most helpful

---

### Post by whofacke on 2011-02-23
One more thing:

the error message that tells me of the broken package systems recommended running "apt-get install -f" in Terminal, so I did, and this is what came out:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Maybe this is a clue. The 'broken package system' error message also told me that I should check for 'third party repositories'...whatever those are........

---

### Post by sidprak on 2011-02-23
> **whofacke said:**
> One more thing:

the error message that tells me of the broken package systems recommended running "apt-get install -f" in Terminal, so I did, and this is what came out:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Maybe this is a clue. The 'broken package system' error message also told me that I should check for 'third party repositories'...whatever those are........

Try 

```
sudo apt-get install -f
```

You need to be root to use apt.

---

