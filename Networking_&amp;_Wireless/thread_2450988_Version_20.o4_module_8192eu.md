---
title: "Version 20.o4 module 8192eu"
date: 2020-09-24
forum: Networking &amp; Wireless
---

### Post by ionmich1 on 2020-09-24
Where might I find the 8192eu module for 20.04?

Thanks in advance.

---

### Post by Frogs Hair on 2020-09-24
I have not used these instructions, but they may be helpful.

[https://easylinuxtipsproject.blogspot.com/p/realtek.html](https://easylinuxtipsproject.blogspot.com/p/realtek.html)

---

### Post by ionmich1 on 2020-09-24
> **Frogs Hair said:**
> I have not used these instructions, but they may be helpful.

[https://easylinuxtipsproject.blogspot.com/p/realtek.html](https://easylinuxtipsproject.blogspot.com/p/realtek.html)

Many thanks. Problem solved.

---

### Post by jeremy31 on 2020-09-24
For rtl8192eu devices I usually recommend
```
sudo apt-get install git linux-headers-generic build-essential dkms
git clone https://github.com/Mange/rtl8192eu-linux-driver
sudo dkms add ./rtl8192eu-linux-driver
sudo dkms install rtl8192eu/1.0
echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf
```

---

