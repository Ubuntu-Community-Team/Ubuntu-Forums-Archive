---
title: "SOLVED install usb wireless adapter tp-link tl-wn8200nd in Ubuntu"
date: 2020-02-25
forum: Networking &amp; Wireless
---

### Post by ecuentas on 2020-02-25
This adapter sports the chipset Reañltek rtl8192eu. Best results and easiest to install for me has been the official driver located at [https://github.com/clnhub/rtl8192eu-linux](https://github.com/clnhub/rtl8192eu-linux) To install:

sudo apt -y install linux-headers-generic build-essential dkms git

git clone [https://github.com/clnhub/rtl8192eu-linux](https://github.com/clnhub/rtl8192eu-linux)

cd rtl8192eu-linux

./install_wifi.sh

---

### Post by him610 on 2020-02-25
I have the same chip on one of my devices. I initially had some issues with it. The correct drivers have been in the repositories at least since 19.10. You can read my observations here, [https://ubuntuforums.org/showthread.php?t=2420042&highlight=rtl8192eu]("https://ubuntuforums.org/showthread.php?t=2420042&highlight=rtl8192eu")

---

