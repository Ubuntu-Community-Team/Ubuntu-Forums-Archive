---
title: "Need to install some packages"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by AgentXSmith on 2009-01-21
Hi,  I've just upgraded to 8.10 and need to download some packages but I get this error message:

[B]E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/B]

What does this mean and what do I do?

Thanks

---

### Post by toddward on 2009-01-21
Run the following as root.  Then try to get your packages downloaded again:

```
dpkg --configure -a
```

---

### Post by adult swim on 2009-01-21
you need to go to a terminal, applications>accessories>terminal and enter in ```
sudo dpkg --configure -a
``` then hit enter, type in your password and hit enter.  then run ```
sudo apt-get update

sudo apt-get upgrade
``` and  you should be all set

---

### Post by AgentXSmith on 2009-01-21
Ok, I did that and now some more errors have come up.  It suggested that I run apt-get -f install.  I did and I get these error messages:

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


What sort of minefield have I walked into?:p

---

### Post by emarkd on 2009-01-21
Did you put 'sudo' in front of each of the commands?  You're getting a permissions error because you're not running the command as root.  Adding 'sudo' before the command forces it to run as the superuser (root).

---

### Post by AgentXSmith on 2009-01-21
ok, I used sudo and then all kinds of things started to happen, too quick for me to see, but the final thing to come up was a "configuring sun java 6 bin" screen with a long legal disclaimer.  There is an <ok> at the bottom of the disclaimer but nothing happens when I click it.  It appears to be frozen.

---

### Post by adult swim on 2009-01-22
this gets alot of people :)  whenever that screen pops up, you need to hit tab.  it will make the OK highlighted and then you need to hit enter.

---

### Post by AgentXSmith on 2009-01-22
Alrighty, it's all good now.  Thanks for all your  help emarkd and adult swim.  This forum is the best for us newbies.

Speaking of adult swim, any idea when season 4 of the venture bros starts?

---

### Post by adult swim on 2009-01-22
this kind of thing usually occurs when an update is interrupted and then it creates a nice little mess for you to clean up.  its not that hard once youve had to do it a couple of times.  as far as venture brothers goes, i dont know.  im waiting for new aqua teen hunger force myself!

---

