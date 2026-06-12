---
title: "usb_modeswitch 64"
date: 2010-01-16
forum: New to Ubuntu
---

### Post by betterthanjordan79 on 2010-01-16
could anyone help me find usb_modeswitch for 64 bit architecture.

its the deb file im looking for or if someone could give me step by step instructions on how to install it.

also i found this but im not sure which is 64bit.

> [http://packages.debian.org/squeeze/usb-modeswitch](http://packages.debian.org/squeeze/usb-modeswitch)

thanks in advanced
Daniel

---

### Post by marshmallow1304 on 2010-01-16
It's in the universe repository.  Go to System->Administration->Software sources and on the Ubuntu Software tab, make sure universe is checked.  Close and reload then install the package via Synaptic or
```
sudo apt-get update && sudo apt-get install usb-modeswitch
```

---

### Post by betterthanjordan79 on 2010-01-16
thanks for the reply but my problem is that i dont have the internet so i want to download it onto this windows machine and then transfer it across. then i can use my o2 modem.

---

### Post by marshmallow1304 on 2010-01-16
[http://packages.ubuntu.com/karmic/usb-modeswitch](http://packages.ubuntu.com/karmic/usb-modeswitch)

Download link at the bottom.  Once you get the deb, double click it to install.  If it asks for dependencies, those are listed on the page as well.

---

### Post by betterthanjordan79 on 2010-01-16
perfect!!!thanks!!!

---

