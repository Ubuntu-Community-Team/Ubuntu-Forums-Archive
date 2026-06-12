---
title: "WI-FI keeps dropping for BROADCOM BCM43142 wireless card on Ubuntu 16.04 LTS"
date: 2018-06-09
forum: Networking &amp; Wireless
---

### Post by aliole4731 on 2018-06-09
My WI-FI keeps dropping every 2minutes and I have to reconnect manually each time.I tried the solution given at [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) .I went through the thread and it looks like I already have the correct driver :grin:(bcmwl-kernel-source) for my pci.id.Someone then suggested I use another driver which I installed using the code```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://ubuntu-master.mirror.tudos.de/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-5_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-5_all.deb 
sudo apt-get remove --purge bcmwl-kernel-source
echo "blacklist b43" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

and the problem still persist.Someone also suggested I set my ipv6 to ignored.It made the network manager to always remain in connected state although the WI-FI had dropped and I still have to reconnect manually every 2 minutes or so.I also added a script to /etc/NetworkManager/dispatcher.d so that I don't have to reconnect manually everytime but it also doesn't work:```
#!/bin/bash

if [ "$CONNECTION_UUID" = " *********" ]; then
    if [ "$2" = "down" ]; then
        sleep 10
        nmcli con up uuid $CONNECTION_UUID
    fi
fi
```.
My wireless info script output:
[https://paste.ubuntu.com/p/TzvF8r2vDF/](https://paste.ubuntu.com/p/TzvF8r2vDF/)

---

### Post by jeremy31 on 2018-06-09
Disable UFW as it appears to be blocking multicast

---

### Post by aliole4731 on 2018-06-10
I did that 
sudo ufw disable
but the problem is still there wifi disconnects every 2 minutes

---

### Post by aliole4731 on 2018-06-16
Hi,disabling ufw did not help any help would be appreciated

---

### Post by jeremy31 on 2018-06-19
The signal strength is fairly low, you may want to get a USB wifi adapter with external antenna

---

### Post by aliole4731 on 2018-06-21
but it was not low when i was using windows 10 on the same laptop

---

### Post by jeremy31 on 2018-06-21
Try Ubuntu 16.04.1 and see if the signal strength is good using the 4.4 kernel as I have heard complaint about signal strength on the newer kernels

---

