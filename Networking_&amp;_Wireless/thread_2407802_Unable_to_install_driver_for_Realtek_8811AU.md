---
title: "Unable to install driver for Realtek 8811AU"
date: 2018-12-09
forum: Networking &amp; Wireless
---

### Post by Pavel_Razgovorov on 2018-12-09
So I bought this: [https://es.aliexpress.com/item/USB3-0-AC-1200-Mbps-inal-mbrica-de-banda-Dual-USB-adaptador-de-red-inal-mbrica/32842909137.html?spm=a2g0s.9042311.0.0.7c3b63c04zpFIq](https://es.aliexpress.com/item/USB3-0-AC-1200-Mbps-inal-mbrica-de-banda-Dual-USB-adaptador-de-red-inal-mbrica/32842909137.html?spm=a2g0s.9042311.0.0.7c3b63c04zpFIq) and now I'm trying to make it work for my Ubuntu distro (it's working fine in Windows and in Mac as well after I installed a driver for the later).

I tried to install these drivers:
[https://github.com/diederikdehaas/rtl8812AU](https://github.com/diederikdehaas/rtl8812AU)
[https://github.com/gordboy/rtl8812au](https://github.com/gordboy/rtl8812au)

But none of them is working (they appear as installed in DKMS, but no WLAN interface is shown on `ip a`)

Any idea?

PS: I attach a wireless-info.txt in case it gives you some info (at this moment, I uninstalled the previous DKMS drivers).

---

### Post by chili555 on 2018-12-10
> ID 0bda:b812 Realtek Semiconductor Corp. Yours is not an rtl8812au device. That is why you installed drivers and the device is not claimed by the (improper) driver and driven.

It is, instead, the rare and elusive 88x2bu device. With a temporary working internet connection, do:

```
git clone https://github.com/cilynx/rtl88x2BU_WiFi_linux_v5.2.4.4_26334.20180126_COEX20171012-5044
cd rtl88x2BU_WiFi_linux_v5.2.4.4_26334.20180126_COEX20171012-5044
VER=$(cat ./version)
sudo rsync -rvhP ./ /usr/src/rtl88x2bu-${VER}
sudo dkms add -m rtl88x2bu -v ${VER}
sudo dkms build -m rtl88x2bu -v ${VER}
sudo dkms install -m rtl88x2bu -v ${VER}
sudo modprobe 88x2bu
```Your wireless should now be working.

---

