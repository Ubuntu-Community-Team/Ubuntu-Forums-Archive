---
title: "I have wireless WIFI issue.."
date: 2014-01-25
forum: Networking &amp; Wireless
---

### Post by kunduruswaroop on 2014-01-25
Hello All,

I am on Ubuntu 13.10 and my system will not connect to wifi on startup. I have to open terminal and give following command.

sudo modprobe rt2800pci nohwcrypt=1


It then ask for password. It connects to wireless on entering password

What should I do so that my system connect to wifi instently on startup?

Thanks in advance for your advice.

Thanks for viewing my post.

Regards,

Swaroop Kunduru.

---

### Post by chili555 on 2014-01-26
Please open a terminal and do:```
sudo -i
echo "options rt2800pci nohwcrypt=1"  >>  /etc/modprobe.d/rt2800.conf
echo rt2800pci  >>  /etc/modules
exit
```Is it working now?

---

### Post by kunduruswaroop on 2014-02-17
This works excellent. Thankyou for help.

Sorry for late reply.

Regards,

Swaroop Kunduru.

---

