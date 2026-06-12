---
title: "BCM4321 no 5ghz, broken WL driver"
date: 2014-09-16
forum: Networking &amp; Wireless
---

### Post by keithspg on 2014-09-16
First, this is a quite nonstandard setup. I am running a 3.17 kernel on 14.04 (b/c I have the crippled intel 965 video subsystem and this allows a suspend/resume). 

I figured out the linux-nonfree update removed the broadcom driver and was able to reinstall the B43 driver. All good. I have a 5ghz signal at home and wanted to connect to it and the B43 driver cannot see it. The card: 
```
0b:00.0 Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 03)
```

I went to the broadcom web page: [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php) and downloaded the amd64 6.30.223.248 package as it 'seems' that this iwll allow a 5ghz connection. Tried to build it. It needed a couple patches. one from here: [http://www.mindwerks.net/2013/10/wireless-bcm4312-with-the-3-10-and-3-11-kernels/](http://www.mindwerks.net/2013/10/wireless-bcm4312-with-the-3-10-and-3-11-kernels/) and another from here: [https://aur.archlinux.org/packages/broadcom-wl/](https://aur.archlinux.org/packages/broadcom-wl/)

I can build it, see my networks (still no 5ghz), but I cannot connect as all are WPA2. I put in a valid password and it just keeps retrying. It did this when I first installed 14.04 as well. What am I missing?

Keith

---

