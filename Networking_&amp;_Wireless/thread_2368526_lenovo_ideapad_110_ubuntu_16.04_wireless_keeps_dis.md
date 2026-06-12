---
title: "lenovo ideapad 110 ubuntu 16.04 wireless keeps disconnecting"
date: 2017-08-11
forum: Networking &amp; Wireless
---

### Post by jerarmstrong on 2017-08-11
my wireless keeps disconnecting every 5-10 minutes.  wireless card is RTL8821AE 802.11ac PCIe Wireless network adapter.  any help is appreciated.  relatively new to ubuntu, thanks

---

### Post by jerarmstrong on 2017-08-11
It is a windows 10 ubuntu 16.04 dual boot

---

### Post by vocx on 2017-08-12
> **jerarmstrong said:**
> my wireless keeps disconnecting every 5-10 minutes.  wireless card is **RTL8821AE** 802.11ac PCIe Wireless network adapter.  any help is appreciated.  relatively new to ubuntu, thanks

See this thread [https://ubuntuforums.org/showthread.php?t=2368005&p=13673251#post13673251](https://ubuntuforums.org/showthread.php?t=2368005&p=13673251#post13673251)
[https://ubuntuforums.org/showthread.php?t=2367093](https://ubuntuforums.org/showthread.php?t=2367093)

It seems many Lenovo users experience problems with the default Realtek wireless drivers included in the stock kernel when they first install the system. The solution is to download the newest drivers, compile them, and install them.

All these threads use the solution here
[https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa](https://medium.com/@elmaxx/rtl8821ae-wifi-drivers-in-ubuntu-16-04-4c1286524afa)

```

sudo apt-get install linux-headers-generic build-essential git
git clone http://github.com/lwfinger/rtlwifi_new.git
cd rtlwifi_new
make
sudo make install

```

"These commands build and install the drivers for rtl8192ce, rtl8192se, rtl8192de, rtl8188ee, rtl8192ee, rtl8723ae, rtl8723be, and rtl8821ae, all in one go. Just in case the system doesn’t load the appropriate kernel module, you can execute the following command from within your rtlwifi_new directory
Code:
```

sudo modprobe rtl8821ae

```

I hope these problems go away by 2018 as probably the new drivers will be included in the new kernel versions released by then. Of course, if new wireless chipsets are released, even newer drivers will be necessary and the catching up cycle will continue.

---

