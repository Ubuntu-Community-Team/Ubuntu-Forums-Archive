---
title: "Connected but no internet"
date: 2015-07-20
forum: Networking &amp; Wireless
---

### Post by Dukenukemx on 2015-07-20
I installed Ubuntu 15.04 on my HP ZV6000 and can get the wired and wireless connected but no internet access.  I can ping other devices in my network but I can't go on the internet.  I connect for now using my cell phone through usb tethering.

---

### Post by Vladlenin5000 on 2015-07-20
Please check your router before anything else. It's kinda obvious...

---

### Post by patilamol-91 on 2015-07-22
Hi,
Are you able to connect to internet when using it over Windows 7. Then try to find the details of the interface & note the DNS.
While configuring IP address in Ubuntu make sure you also add DNS address to your Wired network interface. Without adding DNS you will only be able to ping IP addresses but not hosts.
To check,
just try to ping any public IP address for example 8.8.8.8 . If it works,then your router is working fine. 
Also,
you can add google DNS address i.e. 8.8.8.8 if you do not get DNS information from your ISP.
Hope it will work for you !

---

