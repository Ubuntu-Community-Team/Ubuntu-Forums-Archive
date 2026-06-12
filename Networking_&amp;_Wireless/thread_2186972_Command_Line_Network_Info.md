---
title: "Command Line Network Info"
date: 2013-11-10
forum: Networking &amp; Wireless
---

### Post by Geoff_Lane on 2013-11-10
Folks,

I run a small apache2 web server on a Raspberry Pi with no screen.

All administration is done on my Ubuntu laptop using ssh or webmin.

I share some largish media files with one friend and would like to be able to monitor the transfer, see how it is progressing.

Any suggestions as to terminal commands to do this?

The apache log files seem to give this info when FINISHED but not whilst in progress.

Geffers

---

### Post by sanderj on 2013-11-10
Hint: 

```
sudo tcpflow -i any -C -e port 119 |  pv -b > /dev/null
```

works for seeing the amount of traffic via port 119 ...

---

### Post by tompiedom on 2013-11-10
You could also install **apachetop**. 

```
apachetop -d 1
```

---

### Post by oldos2er on 2013-11-10
Moved to Networking & Wireless.

---

