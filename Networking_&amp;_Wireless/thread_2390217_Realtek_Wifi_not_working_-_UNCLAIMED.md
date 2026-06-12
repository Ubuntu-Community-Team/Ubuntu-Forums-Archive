---
title: "Realtek Wifi not working - UNCLAIMED"
date: 2018-04-26
forum: Networking &amp; Wireless
---

### Post by Kognit on 2018-04-26
Hello,

i just bought new HP laptop and wifi is not working, though on Windows there is no problem. Even more, doing lshw Network is unclaimed:

```
-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d1300000-d130ffff


```

```
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device d723

```

I found a lot of GIT pages offering REaltek drivers but the problem is i do not know what is the correct driver.

I use Kubuntu 18.04, the same problem was also presen on Kubuntu 16.04.

Thanks for help.

---

### Post by jeremy31 on 2018-04-26
I would actually try Larry Fingers version
```
sudo apt-get install git dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Reboot

---

### Post by stefanomazzobel on 2018-08-01
> **jeremy31 said:**
> I would actually try Larry Fingers version
```
sudo apt-get install git dkms
git clone -b extended https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms install rtlwifi-new/0.6
```

Reboot

Still UNCLAIMED, mine is a realtek usb wifi adapter, 8188eus

---

