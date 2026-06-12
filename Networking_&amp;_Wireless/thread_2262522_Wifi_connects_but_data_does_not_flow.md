---
title: "Wifi connects but data does not flow"
date: 2015-01-25
forum: Networking &amp; Wireless
---

### Post by vivek22 on 2015-01-25
I just setup a new wireless router in AP mode that every other device (tablets,phones etc., 8 other devices) connect to fine but my Ubuntu 12.04 connects to the Wifi fine but a ping to the router does not work.  I ran the script posted in another topic ([http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222](http://ubuntuforums.org/showthread.php?t=2224209&p=13024222#post13024222)) to   get details of my configuration - I am attaching the script output from both the old and the new routers.  Can someone tell me what is wrong here.

Thanks

---

### Post by praseodym on 2015-01-25
Deactivate the N-mode and the queue of the driver:

```
echo "options iwlwifi 11n_disable=1 wd_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```

---

### Post by vivek22 on 2015-01-26
Amazing - thank you.  That worked well.  Can you please explain / point me to what those settings are for my education and others as well.

---

### Post by praseodym on 2015-01-26
Please check:
```

modinfo iwlwifi
```
;)

---

