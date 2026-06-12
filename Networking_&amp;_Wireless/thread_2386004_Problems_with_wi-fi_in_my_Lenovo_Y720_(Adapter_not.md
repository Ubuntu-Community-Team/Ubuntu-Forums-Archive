---
title: "Problems with wi-fi in my Lenovo Y720 (Adapter not recognized)"
date: 2018-02-27
forum: Networking &amp; Wireless
---

### Post by santiago55397 on 2018-02-27
Hi guys, I am new in Ubuntu and I also bought a new computer, a Lenovo Y720. I was seeing that my wirless adapter is Intel Dual Band 8265/8275. But I am not sure about that. I can not connect to any wi-fi network, I saw that my wi-fi device is not being recognized.

I know that there are many threads about the topic but I have tried a lot of things but the wi-fi is not runing and I don't know what to do :( 

Please help. Thank you in advanced guys.

---

### Post by jeremy31 on 2018-02-27
Can you post results from terminal for ```
lspci -nnk | grep -iA3 net; rfkill list
```

---

### Post by santiago55397 on 2018-02-27
Sure, and thanks for answer.
```
02:00.0 Network controller [0280]: Intel Corporation Device [8086:24fd] (rev 78)
    Subsystem: Intel Corporation Device [8086:1010]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3880]
    Kernel driver in use: r8169
    Kernel modules: r8169
3d:00.0 Non-Volatile memory controller [0108]: Samsung Electronics Co Ltd Device [144d:a804]
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


```

---

### Post by jeremy31 on 2018-02-27
Ok do
```
echo "blacklist ideapad_laptop" | sudo tee /etc/modprobe.d/ideapad_laptop.conf
```
Reboot

What kernel are you using? ```
uname -r
```
This problem is fixed in upstream kernels with [https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/ideapad-laptop.c?id=b2f2fe205c3b9b595dc50ee431230a45d03f9c2c](https://git.kernel.org/pub/scm/linux/kernel/git/next/linux-next.git/commit/drivers/platform/x86/ideapad-laptop.c?id=b2f2fe205c3b9b595dc50ee431230a45d03f9c2c) unless your exact model is not Y720-15IKBN

---

### Post by santiago55397 on 2018-02-27
Hey thanks it worked with the first command you give me at first time !

I can not believe I was trying since Saturday and you make it works at first try haha. Thanks!

The kernel is 4.13.0-36-generic.

---

### Post by jeremy31 on 2018-02-27
Ubuntu 18.04 should work without using that command as it is has the kernel fix, please use the thread tools menu near the top right of the page to mark as solved

---

### Post by skope2 on 2018-11-05
I'm on lenovo y530 :
Ubuntu : 18.04
kernel : 4.15.0-38-generic

I blacklisted the lenovo-laptop module, now the wifi turns on but don't detect any network :/ it loads endlessly

---

