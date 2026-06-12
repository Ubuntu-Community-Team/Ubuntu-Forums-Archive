---
title: "Help, my wireless card RTL8191SEvA is not working."
date: 2016-04-19
forum: Networking &amp; Wireless
---

### Post by _sluimers_ on 2016-04-19
lspci

```

04:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

```

ip link
```

3: wlp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DORMANT group default qlen 1000
    link/ether 1c:65:9d:15:9f:fe brd ff:ff:ff:ff:ff:ff

```

ip addr
```

3: wlp4s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 1c:65:9d:15:9f:fe brd ff:ff:ff:ff:ff:ff

```

dmesg | grep wlp4s0
```

[   73.341285] rtl8192se 0000:04:00.0 wlp4s0: renamed from wlan0
[   74.403692] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   74.558762] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready
[   74.755532] IPv6: ADDRCONF(NETDEV_UP): wlp4s0: link is not ready

```

---

### Post by Hadaka on 2016-04-19
Hi, please open a terminal ctrl/alt/t then Copy and paste the following commandand press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
Next.
From your directory please copy,paste and post the wireless-info.txt
thanks.

---

### Post by _sluimers_ on 2016-04-19
[http://paste.ubuntu.com/15933947/](http://paste.ubuntu.com/15933947/)

---

### Post by Hadaka on 2016-04-19
Hi please open a terminal and do..
```
sudo iw reg set NL
sudo sed -i 's/^REG.*=$/&NL/' /etc/default/crda
```
then do..
```
sudo apt-get updates
sudo apt-get dist-upgrade

```
boot...then do
```
sudo modprobe -rf rtl8192se
sudo modprobe rtl8192se
```
Please post the output of..
```
modinfo rtl8192se | grep 8171
dmesg  | grep rtl
```
thanks.

---

### Post by _sluimers_ on 2016-04-19
```

alias:          pci:v000010ECd00008171sv*sd*bc*sc*i*

```

```

[   23.608261] rtl8192se: FW Power Save off (module option)
[   23.614982] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
               Loading firmware rtlwifi/rtl8192sefw.bin
[   23.643254] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   23.729898] rtl8192se 0000:04:00.0 wlp4s0: renamed from wlan0
[  217.992820] rtl8192se: FW Power Save off (module option)
[  217.992968] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
               Loading firmware rtlwifi/rtl8192sefw.bin
[  217.994589] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[  218.000143] rtl8192se 0000:04:00.0 wlp4s0: renamed from wlan0

```

---

### Post by Hadaka on 2016-04-20
Hi, Let's see if we can get the card to tell us why it doesnt want to connect.
Please disconnect the wired connection and do,..
```
sudo modprobe -rf rtl8192se
sudo modprobe -vv rtl9192se
```
then do and post..
```
dmesg | grep rtl
```
thanks.

---

### Post by _sluimers_ on 2016-04-20
```

modprobe: INFO: ../libkmod/libkmod.c:356 kmod_set_log_fn() custom logging function 0x558b3cc9e480 registered
modprobe: FATAL: Module rtl9192se not found.

```

```

[   24.613747] rtl8192se: FW Power Save off (module option)
[   24.620930] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
               Loading firmware rtlwifi/rtl8192sefw.bin
[   24.659119] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[   24.777156] rtl8192se 0000:04:00.0 wlp4s0: renamed from wlan0

```

---

### Post by Hadaka on 2016-04-20
Ok, let's give this a try  and load the dirver rtlwifi_new: 

    ```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
    sudo apt-get update
    sudo apt-get install rtlwifi-new-dkms linux-firmware
```

If it still doesn't connect, Please post  at a new wireless script with the ethernet detached.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
thanks.

---

### Post by _sluimers_ on 2016-04-21
[http://paste.ubuntu.com/15960345/](http://paste.ubuntu.com/15960345/)

---

### Post by Hadaka on 2016-04-21
Hi, everything appears to be in line with the  driver and hopefully your
configuration. Unfortunately I have no knowledge of " the use of docker0"
or how it functions,My hope was that by loading an updated driver that it
would resolve your problem. I apologize that it was not the solution needed.
I will have to research Fritz box and docker usage and configuration. Sorry
I have nothing further to contribute.
thanks.

---

### Post by _sluimers_ on 2016-04-22
Docker is unrelated. Fritz box is the name of my router.

---

