---
title: "configure network from terminal"
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by npodges on 2006-09-14
The kernel update broke my nvidia drivers. I can't get into gnome anymore.. it also broke my ndiswrapper, I think. Since my wireless is set as the default network device, S cant update via eth0. 

How can i change network settings to default eth0 from the command line?

---

### Post by tbonius on 2006-09-14
Just ifup eth0 (if you are DHCP).  Then you can apt-get install the nvidia stuff again.  Am I missing something else?

T

---

### Post by npodges on 2006-09-14
nope, that's it. thanks :-D

---

