---
title: "hardware modems"
date: 2005-09-16
forum: Networking &amp; Wireless
---

### Post by skaja on 2005-09-16
i'm trying to set up my modem i went to [my modem faq page](http://actiontec.com/support/modems/cwifaq.html#installlinux) 

If you are using the Debian distribution, go to the /etc/rcS.d directory. Edit the file called S30setserial and add the two setserial lines.

setserial /dev/ttyS3 port 0xa000 spd_vhi skip_test auto_irq autoconfig
setserial /dev/ttyS3 uart 16550A
but i cant find the file called s30setserial under /etc/rcS.d
 ](*,)

---

