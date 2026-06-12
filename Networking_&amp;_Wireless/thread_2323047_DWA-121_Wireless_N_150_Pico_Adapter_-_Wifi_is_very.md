---
title: "DWA-121 Wireless N 150 Pico Adapter - Wifi is very slow"
date: 2016-05-02
forum: Networking &amp; Wireless
---

### Post by said-el on 2016-05-02
Dear All,

I'm using DWA-121 Pico adapter , It was working just fine in xubuntu 14.04 , when I upgraded to xubuntu 16.04 the wifi speed became very slow,
Here is the output of the wireless info script : [http://paste.ubuntu.com/16193670/](http://paste.ubuntu.com/16193670/)
Would you please provide some suggestions

Regards

---

### Post by praseodym on 2016-05-02
Yes, change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo "blacklist rtl8xxxcu" | sudo tee -a /etc/modprobe.d/blacklist-rtl8xxxcu.conf  
``` 
Reboot

---

### Post by said-el on 2016-06-16
> **praseodym said:**
> Yes, change the driver:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911 
echo "blacklist rtl8xxxcu" | sudo tee -a /etc/modprobe.d/blacklist-rtl8xxxcu.conf  
``` 
Reboot

Thank you , that solved the issue.

---

