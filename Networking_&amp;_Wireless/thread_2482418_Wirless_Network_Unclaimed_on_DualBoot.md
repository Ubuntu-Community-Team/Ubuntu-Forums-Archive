---
title: "Wirless Network Unclaimed on DualBoot"
date: 2022-12-30
forum: Networking &amp; Wireless
---

### Post by difable on 2022-12-30
Hello I have installed Ubuntu 22.04.1 on my msi laptop (specs are attached) together with windows and I cant seem to access any Wifi connection.
USB tethering and wired connections seem to work fine.

When  I use the "lshw -C network" command (results attached) it says network Unclaimed and i any information i have found regarding this problem seems outdated or hardware specific and I wasn't able to solve this problem on my own.

I cant even see any Wireless settings in the settings tab, can anyone help me ?

thanks in advance and I'll of course provide additional information if required!

---

### Post by chili555 on 2022-12-30
Please run the terminal commands:```
lspci -nnk | grep 0280 -A3
sudo modprobe iwlwifi && sudo dmesg | grep iwl
```Next, please post the results.

---

### Post by difable on 2022-12-30
These are my results

---

### Post by chili555 on 2022-12-30
This is the probable answer: [https://askubuntu.com/questions/1399951/wifi-adapter-not-working-ubuntu-21-10-fresh-install-in-asus-laptop/1400013#1400013](https://askubuntu.com/questions/1399951/wifi-adapter-not-working-ubuntu-21-10-fresh-install-in-asus-laptop/1400013#1400013) Today, I'd suggest kernel version 5.17.15.

Or, even easier, install Ubuntu 22.10 which uses kernel version 5.19 by default.

---

### Post by difable on 2022-12-30
I just installed Ubuntu 22.10 and Wifi is working!

Thank you so much :D

---

### Post by chili555 on 2022-12-30
Awesome! Please use thread tools at the top to mark Solved. The searchers will appreciate it.

---

