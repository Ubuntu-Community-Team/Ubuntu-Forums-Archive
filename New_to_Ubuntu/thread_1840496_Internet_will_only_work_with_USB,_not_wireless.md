---
title: "Internet will only work with USB, not wireless"
date: 2011-09-07
forum: New to Ubuntu
---

### Post by avisvolat on 2011-09-07
Hello,
I just put 11.04 on my computer, and the internet connection will only work when I connect my computer to the modem with the USB cord.  It will not work wirelessly, like it did with the other OS.  How do I correct this?
Thanks!

---

### Post by aura7 on 2011-09-07
Wireless drivers are proprietary drivers and you have to install them manually in some distros. In case you have a broadcom wireless modem install the drivers by downloading them from the link below

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by ajgreeny on 2011-09-07
But first let's find out the wireless adapter you have.  Open a terminal and run command ```
lspci
``` and then ```
sudo lshw -C network
```

---

### Post by avisvolat on 2011-09-12
OK, I did that and it shows a whole bunch of info.  Not sure what you need to know...

---

### Post by gandaran on 2011-09-12
> **avisvolat said:**
> OK, I did that and it shows a whole bunch of info.  Not sure what you need to know...
post all the info

---

### Post by anewguy on 2011-09-12
Broadcom drivers and other wireless drivers also sometimes be activated just by doing:

sudo apt-get update

Let if finish, then look under Additional or Restricted Drivers and see if there is a driver showing for the wireless, enabled it.


And, if this is a laptop or the wireless adapter is USB, please also include the output of:

lsusb


Thanks!
Dave ;)

---

