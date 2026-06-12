---
title: "[Kubuntu 12.04] Wireless connection dropping out"
date: 2013-12-15
forum: Networking &amp; Wireless
---

### Post by mscava on 2013-12-15
Hi,

I am using Kubuntu 12.04.3 and my wireless keeps dropping out. Restarting it via NetworkManager works.

```

$ uname -r
3.2.0-57-generic

```

```

$ lspci | grep -i 'network'
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)

```

Looking at /var/log/syslog I can see following messages printed out frequently 

```

Dec 15 19:40:02 eggplant kernel: [ 3885.547225] net_ratelimit: 14 callbacks suppressed
Dec 15 19:40:02 eggplant kernel: [ 3885.547231] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Dec 15 19:40:02 eggplant kernel: [ 3885.547239] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Dec 15 19:40:02 eggplant kernel: [ 3885.547313] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Dec 15 19:40:02 eggplant kernel: [ 3885.547319] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Dec 15 19:40:03 eggplant kernel: [ 3886.545539] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Dec 15 19:40:03 eggplant kernel: [ 3886.545549] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Dec 15 19:40:03 eggplant kernel: [ 3886.545597] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Dec 15 19:40:03 eggplant kernel: [ 3886.545604] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
Dec 15 19:40:04 eggplant kernel: [ 3887.543265] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
Dec 15 19:40:04 eggplant kernel: [ 3887.543274] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)

```

I have seen couple of people reporting this but I am not sure on what is the correct workaround. Any recommendations?

Thanks.

---

### Post by praseodym on 2013-12-31
Use the updated native driver:```


sudo apt-get remove--purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
sudo sed -i "s/blacklist b43/#blacklist b43/g" $(egrep -lo 'blacklist b43' /etc/modprobe.d/*)
sudo sed -i "s/blacklist ssb/#blacklist ssb/g" $(egrep -lo 'blacklist ssb' /etc/modprobe.d/*)
sudo sed -i "s/blacklist bcma/#blacklist bcma/g" $(egrep -lo 'blacklist bcma' /etc/modprobe.d/*) 
sudo apt-get install linux-backports-modules-cw-3.6-$(grep CODE /etc/lsb-release | cut -c18-28)-$(uname -r | cut -c10-23) 
sudo apt-get install linux-headers-generic linux-headers-$(uname -r) build-essential dkms linux-firmware-nonfree
```
Reboot.

---

