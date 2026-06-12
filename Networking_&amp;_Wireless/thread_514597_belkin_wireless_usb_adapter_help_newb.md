---
title: "belkin wireless usb adapter help *newb*"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by welfinator on 2007-07-31
hi guys, i just installed a copy of ubuntu using wubi, everything seemed to work flawlessly except i am not able to set up my wireless usb. when i start ubuntu i am able to see networks in the top right corner, however i am not able to connect to any of them. could you guys please help me with this. i am very new to linux and have only used suse before. what do i need to do to get this working and where can i get a driver for this

thank you very much

this is my usb adapter
[http://www.belkin.com/support/article/?lid=en&pid=F5D9050&aid=6019&scid=0](http://www.belkin.com/support/article/?lid=en&pid=F5D9050&aid=6019&scid=0)

---

### Post by noob12 on 2007-07-31
The following would help identify the hardware and the driver you are currently getting.  Type these in a terminal window and post the results.

```

lsusb

```

```

sudo lshw -C network

```

---

