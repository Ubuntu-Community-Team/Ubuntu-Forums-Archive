---
title: "Problems with ndiswrapper"
date: 2007-07-14
forum: Networking &amp; Wireless
---

### Post by ittiam on 2007-07-14
My ndiswrapper module does not get loaded on boot up. I have to do a modprobe manually on boot up it to see my wireless interface. I downloaded and did a make on it and did ndiswrapper -m and installed the driver et al. I did not have this problem with edgy.

Also another problem is after it boots i do the modprobe, set the essid using wpa_supplicant and when i try to do a dhclient, i get no offers for DHCPDISCOVER. But this problem gets resolved when I pkill wpa_supplicant and repeat the whole process again starting from modprobe ndiswrapper then it works fine. Weird but It would be great if i can get some explanation and fix for this.

thanks

---

### Post by ittiam on 2007-07-14
my bad! Simple it was. Update /etc/modules.

---

