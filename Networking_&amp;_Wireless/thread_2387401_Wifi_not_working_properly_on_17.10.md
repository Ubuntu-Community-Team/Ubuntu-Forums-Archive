---
title: "Wifi not working properly on 17.10"
date: 2018-03-18
forum: Networking &amp; Wireless
---

### Post by klubinus on 2018-03-18
Hi all!

thanks for taking the time to read this thread, I've been having issues with my wifi adapter, it sometimes connects to Internet but when it does  its too slow and the connection drops after a couple minutes. as for the time being I'm connected via usb theter through my phone.

this is my wifi info [http://paste.ubuntu.com/p/CcTG7kqY3f/](http://paste.ubuntu.com/p/CcTG7kqY3f/) 

on a side note the wifi symbol always shows with an ? sing on top of it and as I said, it sometimes connects and drops.
haven't tried wired connection.


thanks for your help.

---

### Post by chili555 on 2018-03-18
Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110) The correct driver for your device is not bcmwl-kernel-source. Let's fix it. From the terminal:```
sudo -i
apt purge bcmwl-kernel source
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```Reboot with the ethernet detached and tell us if the wireless is working.> haven't tried wired connection.This suggests otherwise:> enp0s29u1u3: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.42.51  netmask 255.255.255.0  broadcast 192.168.42.255
        inet6 fe80::1fe2:69c0:308e:5d58  prefixlen 64  scopeid 0x20<link>
        ether <MAC address>  txqueuelen 1000  (Ethernet)
        RX packets 1577  bytes 1058792 (1.0 MB)
        RX errors 1  dropped 0  overruns 0  frame 1
        TX packets 1786  bytes 330234 (330.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


---

### Post by klubinus on 2018-03-18
I ran the code you posted, and rebooted with the phone disconnected from the laptop, it appears as if if was properly connected to the wifi but there is no internet connection, I still get server not found when trying url

---

### Post by chili555 on 2018-03-19
Please run and post:```
ping -c3 8.8.8.8
ping -c3 www.ubuntu.com
sudo resolvconf -u
```Thanks.

---

