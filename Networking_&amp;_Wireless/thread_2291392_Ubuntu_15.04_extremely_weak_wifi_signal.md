---
title: "Ubuntu 15.04 extremely weak wifi signal"
date: 2015-08-19
forum: Networking &amp; Wireless
---

### Post by biraj2 on 2015-08-19
[COLOR=#111111][FONT=Ubuntu]New to Linux Systems, so help would be much appreciated.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Wireless Test Script Code: [http://paste.ubuntu.com/12131270/](http://paste.ubuntu.com/12131270/)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Thank you![/FONT][/COLOR]

---

### Post by Hadaka on 2015-08-19
Hi, please change your router settings from tkip to wpa2
then please do
```
sudo modprobe -rf rt2800pci
 sudo modprobe *rt2800pci nohwcrypt*=1
```
this is good to the first boot..so try it...if it improves then
do..
```
echo options rt2800pci nohwcrypt=1 | sudo tee -a /etc/modprobe.d/rt2800pci.conf
```

---

### Post by biraj2 on 2015-08-20
Does this matter if I will be connected to my college's network? As I will not have access to change the router setting.

Thank you.

---

### Post by biraj2 on 2015-08-28
I'm connected to my College's wifi connection. The signal strength on Ubuntu is terrible. My other devices connected to the network receives full strength.

My wireless information is pasted in the following link : [http://paste.ubuntu.com/12215647/](http://paste.ubuntu.com/12215647/)

Thank you for the support!

---

### Post by howefield on 2015-08-28
Duplicate threads merged.

---

### Post by brad-bogar on 2015-08-28
I would try disabling IPv6 first.

Deactivate IPv6 support:
```
$ sudo su
# echo "#disable ipv6" >> /etc/sysctl.conf
# echo "net.ipv6.conf.all.disable_ipv6 = 1" >> /etc/sysctl.conf
# echo "net.ipv6.conf.default.disable_ipv6 = 1" >> /etc/sysctl.conf
# echo "net.ipv6.conf.lo.disable_ipv6 = 1" >> /etc/sysctl.conf

```

---

### Post by biraj2 on 2015-08-31
Disabling IPv6 had no improvements in network connection strength. Any other suggestions to to fix the change? Thank you!

---

