---
title: "howto update kernel ?"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by madsere on 2009-02-11
.

I've just installed Ubuntu 8.04 and find it only sees 3 GB of the 4 GB I have on this laptop.  On RHEL this usually means I'd need to install a kernel that can address more memory.  How would I go by doing that in Ubuntu?

Sorry probably a real beginner question. I know how to do this using the rpm system but I'm new to Ubuntu and not yet familiar with the apt system

---

### Post by binbash on 2009-02-11
There is a tutorial about this at tutorial section (@ forums)

---

### Post by LowSky on 2009-02-11
at least give him a link or tell him the steps

here are the steps

be careful and disab;e and propritary driver bofre trunning these commands (like graphics or wireless cards)

```
sudo apt-get update
```
```
sudo sudo apt-get install linux-headers-server linux-image-server linux-server
```
then reboot
check ram using 
```
free -m
```

---

### Post by madsere on 2009-02-11
Thanks much Lowsky, that took care of the problem!

---

