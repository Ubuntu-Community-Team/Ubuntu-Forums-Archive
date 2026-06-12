---
title: "/etc/init.d/network restart - file not found"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by zeezam on 2008-07-28
Hmm trying to restart my network but I don't have any network in init.d.
Any ideas why?

---

### Post by brujoand on 2008-07-28
well that should be 
/etc/init.d/networking
But, i would rather do a :

"sudo killall -9 NetworkManager "
and then to start it again
"sudo NetworkManager"

---

### Post by brujoand on 2008-07-28
well that should be 
/etc/init.d/networking
But, i would rather do a :

"sudo killall -9 NetworkManager "
and then to start it again
"sudo NetworkManager"

---

### Post by dmizer on 2008-07-28
> **GrimmVarg said:**
> But, i would rather do a :

"sudo killall -9 NetworkManager "
and then to start it again
"sudo NetworkManager"

That only works if you're using NetworkManager.
```
sudo /etc/init.d/networking restart
```
is preferred because it's gui independent.  Doesn't matter if you're using WICD, NetworkManager, or any other of the multitude of GUI network management programs available, the above command will still work. The "killall" command shouldn't be used unless absolutely necessary as it can cause problems due to an unexpected shutdown in the middle of a process.

---

### Post by zeezam on 2008-07-28
Thanks alot m8s!

---

### Post by dmizer on 2008-07-28
For future information, <tab> is an auto complete.

So, if you type /etc/init.d/netw and then hit the <tab> key, the rest of the command will auto fill, so you never make the mistake between "network" and "networking".

---

