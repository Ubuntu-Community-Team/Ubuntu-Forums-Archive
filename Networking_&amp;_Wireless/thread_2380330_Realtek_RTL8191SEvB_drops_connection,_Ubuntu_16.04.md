---
title: "Realtek RTL8191SEvB drops connection, Ubuntu 16.04.3"
date: 2017-12-15
forum: Networking &amp; Wireless
---

### Post by Hodor on 2017-12-15
Clean install plus updates / upgrades, wifi has started dropping connection after last update or upgrade, hard to re-establish the connection. No other devices have problems connecting to this router. Thanks for any help.

---

### Post by chili555 on 2017-12-16
I would try two things. First, turn off power saving for the driver:```
sudo -i
echo "options rtl8192se ips=0 swlps=0"  >  /etc/modprobe.d/rtl8192se.conf
exit
```Next, I'd turn off power saving in Network Manager:```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```Reboot and let us hear your report.

---

### Post by Hodor on 2017-12-16
Done.  No problems yet.  
The problem seemed to develop after an update or upgrade.  If the problem comes back, is there an easy way to wind back wfi related changes due to the update / upgrade, to go back to 16.04.3 original?
Thank you.

---

### Post by chili555 on 2017-12-17
>  If the problem comes back, is there an easy way to wind back wfi related changes due to the update / upgrade, to go back to 16.04.3 original?Fairly easy, but let's hope that these easy steps have corrected it.

---

