---
title: "Can't Connect to Internet"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Allyhibs on 2010-06-19
Hi, I'm in the process of trying to configure my Atheros AR5007EG to work with Ubuntu but I can't even get my ethernet connection working in order to download the necessary bits. This is in 32bit 8.0.4. What do I need to enter into the terminal to check to see what's wrong?

Thanks

---

### Post by cariboo on 2010-06-19
In a terminal type:

```
lshw -C network
```

This will tell you if the driver for your network device is loaded and if the device is enabled.

---

### Post by gandaran on 2010-06-19
> **Allyhibs said:**
> Hi, I'm in the process of trying to configure my Atheros AR5007EG to work with Ubuntu but I can't even get my ethernet connection working in order to download the necessary bits. This is in 32bit 8.0.4. What do I need to enter into the terminal to check to see what's wrong?

Thanks
upgrade to Ubuntu 10.04, the Atheros card will work out of the box!

---

