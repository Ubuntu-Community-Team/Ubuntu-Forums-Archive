---
title: "Wired Connection lost"
date: 2014-04-12
forum: Networking &amp; Wireless
---

### Post by mehraks9 on 2014-04-12
Hi!
   I have just configured the LTSP on ubuntu 12.04 on IBM Server X with two NIC.After reboot the system is not showing any wired connection. Under Setting> Network option its showing The System network services are not compatible with this version.Earlier it was showing both the NICs.
Kindly help:confused::confused::confused::confused:

---

### Post by varunendra on 2014-04-12
Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
sudo lshw -C network
cat /etc/network/interfaces
```
If it is a Desktop installation (or a server with GUI), also post back the outputs of -
```
nm-tool
cat /etc/NetworkManager/NetworkManager.conf
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

