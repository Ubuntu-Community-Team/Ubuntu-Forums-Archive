---
title: "Wireless quit working on Dell e1405 (Hardy)"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by jkwon19 on 2008-10-14
Hello,

I have been using the wireless connection (Intel 3945 a/b/g) on my Dell e1405 running Hardy 8.04 for months now without problem.  In my house, I either connect to my router through wireless, or where the connection is weaker, I use a direct wired connection to use the network.

Sometime in the past few weeks, the my laptop has become unable to connect to the network through wireless.  I can't pinpoint the exact date and time, because I often switch between wireless and wired, and I also sometimes boot to the Windows XP partition on my laptop (and on that partition, wireless networking continues to work).

Based on other forum posts here, I observed that my network adapter was not being enabled:

> $ dmesg | grep -i wlan
[   54.654498] ADDRCONF(NETDEV_UP): wlan0: link is not ready

I confirmed that the kill switch was not disabling the wireless.  I attempted installing a new driver:

> sudo apt-get install linux-backports-modules-hardy-generic

... and that succeeded in lighting the WiFi LED, but still Network Manager refused to show or connect to any wireless networks.

I did:

> sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
sudo iwlist wlan0 scan

sudo su
echo -e 'alias wlan0 iwl3945 \noptions iwl3945 disable_hw_scan=1' > /etc/modprobe.d/iwl3945
reboot

And scanning works, showing me my access point, but still no wireless networks appear in Network Manager, and I am still unable to connect to any wireless networks.

Finally, I uninstalled and reinstalled Network Manager:

> sudo apt-get purge network-manager-gnome
sudo apt-get autoremove
sudo apt-get install network-manager-gnome

Still no luck.

Was there a recent software update that affected wireless operation?  Anyone else experience the same scenario, where wireless worked and then ceased to work?

Thanks.

---

