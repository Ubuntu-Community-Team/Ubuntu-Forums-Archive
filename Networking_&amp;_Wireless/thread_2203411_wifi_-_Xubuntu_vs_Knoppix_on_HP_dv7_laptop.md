---
title: "wifi - Xubuntu vs Knoppix on HP dv7 laptop"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by aspergerian on 2014-02-03
Wifi works easily via Knoppix 7.2.0 CD but I can't get wifi to work via Xubuntu 12.04.3 CD. I think I have entered correct info into edit network connections (BSSID, MAC address, etc), but just can't get wifi to connect during Xubuntu trial using CD (on HP dv7 laptop). 

I've been trying for days, have read many webpages, can't solve the problem, thus this post. I would prefer Xubuntu if wifi can be tested and made to work on the dv7.

---

### Post by sudodus on 2014-02-03
Knoppix is known to be good at recognizing hardware.

We need to know more to help you with Xubuntu.

1. We need to know which wifi chip there is in the computer.

- Please run ```
sudo lshw
``` save the output to a file and post it to show the wifi hardware

- or run ***hardinfo*** (which you might have to install).

2. We need to know which version of Xubuntu you are running:

- 12.04 LTS or 13.10?

- 32-bit or 64-bit?

---

### Post by aspergerian on 2014-02-03
Thank you for responding. The HP dv7 has a Broadcom 802.11 b/g WLAN, and I'm using Xubuntu 12.04.3 install CD for the test. Knoppix CD is 7.2.0.

---

### Post by aspergerian on 2014-02-03
> **aspergerian said:**
> Thank you for responding. The HP dv7 has a Broadcom 802.11 b/g WLAN, and I'm using Xubuntu 12.04.3 install CD for the test. Knoppix CD is 7.2.0.

64 bit Xubuntu

---

### Post by PotatoHead007 on 2014-02-03
I think you should go for Xubuntu, as it does support the 802.11 b/g WLAN, and knoppix(i find) is more of a OS to use with a LiveUSB, for repair etc, and its not as user-friendly as Xubuntu. My thoughts.

---

### Post by sudodus on 2014-02-03
There are proprietary drivers for Broadcom. Try according to the following link

[http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx](http://askubuntu.com/questions/55868/how-to-install-broadcom-wireless-drivers-bcm43xx)

---

### Post by wildmanne39 on 2014-02-03
*Thread moved to **Networking & Wireless**.*

---

