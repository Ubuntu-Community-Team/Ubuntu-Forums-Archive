---
title: "Intel 1000 Lan driver install"
date: 2008-06-25
forum: Networking &amp; Wireless
---

### Post by ragraham on 2008-06-25
The network card on my Intel D865GLC Motherboard (Intel 1000 pro Lan) has not been detected/installed by UBUNTU during the installation. How can it be installed as the only driver that seems to come close provided by Intel fails when I try and install it.

---

### Post by chili555 on 2008-06-25
I believe the Intel drivers, built circa 2004, have not been updated since the needed module, *e1000*, is now built in to your kernel. Please try:```
sudo modprobe e1000
```Does your card now spring to life? If not, take a look at:```
dmesg | grep e1000
```Let's see if it's trying but failing to load, for some reason.

---

### Post by ragraham on 2008-06-25
Thanks for your speedy reply Chili

Maybe it has detected it after all as it shows the IP address details I entered manually for it with "ifconfig eth0"
but I can't ping anything on the local network or beyond, only pinging 127.0.0.1 is successful.

I tried the commands you suggested and it doesn't seem to have made any difference.....yet

---

### Post by chili555 on 2008-06-25
Please take out the manual details, IP number, netmask, etc. and select DHCP. Will it now connect?

---

### Post by ragraham on 2008-06-25
Thanks Chili, the hardware connection was not seated properly into the router. That was all! Not very clever of me not to have found it sooner.
Looking good now, thanks so much for your response.

---

