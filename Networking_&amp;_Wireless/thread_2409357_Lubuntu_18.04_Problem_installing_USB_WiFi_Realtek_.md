---
title: "Lubuntu 18.04 Problem installing USB WiFi Realtek rtl8812au"
date: 2019-01-01
forum: Networking &amp; Wireless
---

### Post by bengtingo on 2019-01-01
The build in WiFi adapter in my HP PC (Broadcom Limited BCM4313 802.11bgn Wireless Network Adapter) is not working so good in Lubuntu 18.04. It worked ok in W10. So I bought an USB WiFi adapter with Realtek rtl8812au. Downloaded the suppliers install files for Linux but I got several error message during installation. Googled the error message but it didn&#8217;t help me.

After I while I found this youtube clip [https://www.youtube.com/watch?v=XJ0gcA778Ms](https://www.youtube.com/watch?v=XJ0gcA778Ms). Tested it and it worked. Here is the commands. It was easy.

```
sudo apt-get install linux-headers-$(uname -r) build-essential git
git clone [https://github.com/scrivy/rtl8812AU_8821AU_linux.git](https://github.com/scrivy/rtl8812AU_8821AU_linux.git)
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe rtl8812au
```
reboot

---

### Post by jeremy31 on 2019-01-01
When you have a kernel update you should ```
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
Then dkms will automatically compile the module for the new kernel before you reboot

---

