---
title: "Ubuntu 17.4-Wireless is not working"
date: 2017-10-07
forum: Networking &amp; Wireless
---

### Post by fedehon on 2017-10-07
i guys, 
I recently bought an old Dell laptop (Dell D630 intel Core Duo 2 Gb ram) and I installed ubuntu 17.04 on it. 
The wireless is not working, I followed the instruction listed on the thread at the top of this section, so I am pasting my wireless info:

[http://paste.ubuntu.com/25692462/](http://paste.ubuntu.com/25692462/)

---

### Post by wildmanne39 on 2017-10-07
Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo apt install firmware-b43-installer
```
Reboot, your wireless should now work, if it does not run the wireless script again and post the new file created.

Thanks

---

### Post by fedehon on 2017-10-07
Hi,
still not working,
new script:
[http://paste.ubuntu.com/25693591/](http://paste.ubuntu.com/25693591/)

---

### Post by jeremy31 on 2017-10-07
```
sudo -H gedit /etc/modprobe.d/blacklist.conf
```
Delete the lines blacklist ssb and blacklist b43, save and reboot

---

### Post by wildmanne39 on 2017-10-07
Just saw jeremy31's post, do what he recommends, when you ran the purge command I gave you in my previous post it should have removed those modules from the blacklist file but for some strange reason it did not. Did you reboot after running the commands?

---

### Post by fedehon on 2017-10-09
Thank you guys,
Now it's working fine

---

### Post by wildmanne39 on 2017-10-09
Glad it is working!
Enjoy!

---

