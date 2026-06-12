---
title: "List of Wifi Networks not showing up"
date: 2019-06-18
forum: Networking &amp; Wireless
---

### Post by docdoc2 on 2019-06-18
My network applet doesnt show any wifis in the drop down menu, the list is just empty. Since i have this problem the applet also doenst show the wifi symbol anymore but two arrows. I am connected though. Also, wenn i use *nmcli dev wifi list* i can see other networks that i am not connected to.

wpa_supplicant and network manager are installed.

```

Network controller [0280]: Intel Corporation Centrino Wireless-N 2230 [8086:0887] (rev c4)
    DeviceName: Intel Jackson Peak 1 802.11bgn 2x2 + BT combo
    Subsystem: Intel Corporation Centrino Wireless-N 2230 BGN [8086:4062]
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

```

---

### Post by chili555 on 2019-06-18
Please run and post:```
ip addr show
iwconfig
rfkill list all
dmesg | grep iwl
```

---

### Post by docdoc2 on 2019-06-20
I found the problem, the problem lies within the nm-applet and i have this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1576747)

---

