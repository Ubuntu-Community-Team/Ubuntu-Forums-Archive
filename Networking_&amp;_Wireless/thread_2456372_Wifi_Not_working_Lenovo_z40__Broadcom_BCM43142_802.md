---
title: "Wifi Not working: Lenovo z40 / Broadcom BCM43142 802.11b/g/n"
date: 2021-01-10
forum: Networking &amp; Wireless
---

### Post by juanmonsalve88 on 2021-01-10
I im using Ubuntu "20.04.1 LTS (Focal Fossa)" in my Lenovo z40 and my wifi is not working. I am copying below the hardware I am using and the output of the command ***iwconfig***. I am a new user so please forgive me if i am not giving enough information.

Thanks in advance. 

-----------------------------------
$ lspci -k

01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
    Kernel driver in use: r8169
    Kernel modules: r8169
[B][I]02:00.0 Network controller: Broadcom Inc. and subsidiaries BCM43142 802.11b/g/n (rev 01)
    Subsystem: Lenovo BCM43142 802.11b/g/n[/I][/B]
03:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)
    Subsystem: Lenovo GeForce 820M
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

-----------------------------------

-----------------------------------

$ iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.
-----------------------------------

---

### Post by jeremy31 on 2021-01-10
Please post result from terminal for ```
uname -a
```

---

