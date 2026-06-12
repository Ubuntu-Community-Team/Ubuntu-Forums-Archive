---
title: "how to remove bcmwl5 (fwcutter)"
date: 2007-04-24
forum: Networking &amp; Wireless
---

### Post by stevieb on 2007-04-24
hello,

i used bcm43xx-fwcutter to install bcmwl5, but what i need is to do it with wl_apsta.o.  how can i remove bcmwl5?

thanks,

-steve

---

### Post by spd106 on 2007-04-26
The fwcutter just extracts the firmware and puts it in the /lib/firmware directory. If you delete these files and replace them with those from wl_apsta.o then you should be good to go.

---

