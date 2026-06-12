---
title: "Edimax EW-7811Un on BBB with Ubuntu 16.04"
date: 2017-03-17
forum: Networking &amp; Wireless
---

### Post by kaushalyas on 2017-03-17
Hi all,

I am trying to use the above USB network adapter with BBB on Ubuntu 16.04. Initially it was not working with the stock driver and after going through some excellent work by others like [https://github.com/pvaret/rtl8192cu-fixes](https://github.com/pvaret/rtl8192cu-fixes), I manage to get the driver up and running. The only issue I have is I am unable to auto start the wifi when the system boots up. I need to 
>connmanctl enable wifi
to start it and after that everything is good.

I have tried 
1. adding the above to /etc/rc.local
2. enabling wpa supplicant with /etc/wpa_supplicant/wpa_supplicant.conf and /etc/network/interfaces

but nothing worked.

Can someone shed some light to this?

Thanks in advance,
kaushalyas

---

### Post by praseodym on 2017-03-17
Did you blacklist the original drivers (there are two of them now!)?

```
echo -e "blacklist rtl8192cu\nblacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf   
```
There is a newer driver available:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms git
sudo git clone https://github.com/vincent-t/rt8192cu_dkms /usr/src/8192cu-4.0.2.9000.20130911
sudo dkms add -m 8192cu -v 4.0.2.9000.20130911
sudo dkms build -m 8192cu -v 4.0.2.9000.20130911
sudo dkms install -m 8192cu -v 4.0.2.9000.20130911
```
Uninstall the old one first

---

### Post by kaushalyas on 2017-03-19
Hi praseodym,

Many thanks for your reply. 

I had blacklisted the old driver in blacklist.conf as you suggest. Still have the same issue. 

The driver I am using at the moment is what I compiled from 'https://github.com/pvaret/rtl8192cu-fixes', which I think is same as what you suggested. When I run modinfo on my 8192cu that is loaded i get 

ubuntu@arm:~$ modinfo 8192cu
filename:       /lib/modules/4.4.43-ti-r84/updates/dkms/8192cu.ko
version:        v4.0.2_9000.20130911
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     7A1D00646D467D3956EC4A3
...

This driver works perfectly. The only issue is I have to manually execute 'connmanctl enable wifi' everytime I bootup!!

Do you know what's missing here?

Cheers,
kaushalyas
[COLOR=#000000]**praseodym**[/COLOR][COLOR=#000000]**praseodym**[/COLOR][COLOR=#000000]**praseodym**[/COLOR]

---

### Post by kaushalyas on 2017-03-27
Help anyone?

---

