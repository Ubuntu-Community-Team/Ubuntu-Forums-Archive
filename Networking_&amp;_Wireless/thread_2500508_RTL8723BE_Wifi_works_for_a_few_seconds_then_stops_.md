---
title: "RTL8723BE Wifi works for a few seconds then stops working [Ubuntu 24.04.1 LTS]"
date: 2024-09-04
forum: Networking &amp; Wireless
---

### Post by allen-gxm on 2024-09-04
First of all this : [wireless info script output]("https://termbin.com/lwfr")

When I boot into the OS, for about 10~30 seconds the WiFi shows me the available networks after that my WiFi stops working no internet. when I turn the WiFi off then on the visible networks category just spins forever without giving me any network to log into.

I am new to forums and stuff so, I don't know what all information to put in this post apart from the wireless info script output. Tell me and I will update it


lspci output:

```
09:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    DeviceName: Skyray
    Subsystem: Hewlett-Packard Company RTL8723BE PCIe Wireless Network Adapter [103c:2231]
    Kernel driver in use: rtl8723be
```

rfkill output:
```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```


ifconfig output:```


1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: enp8s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP group default qlen 1000
    link/ether <MAC 'enp8s0' [IF1]> brd <MAC address>
    inet 192.168.1.44/24 brd 192.168.1.255 scope global dynamic noprefixroute enp8s0
       valid_lft 85780sec preferred_lft 85780sec
    inet6 fe80::<IP6 'enp8s0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever
3: wlo1: <BROADCAST,MULTICAST> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether <MAC 'wlo1' [IF2]> brd <MAC address>
    altname wlp9s0
```

---

### Post by jeremy31 on 2024-09-04
Lets try disabling wifi power management and see if that fixes this
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo "options rtl8723be ips=N"|sudo tee /etc/modprobe.d/rtl8723be.conf
```
reboot

---

### Post by allen-gxm on 2024-09-04
Thanks for your reply,
That seems to work, atleast for now
I will update my reply after some more time about 1~2 hour later

---

### Post by allen-gxm on 2024-09-04
@jeremy31, It worked for about 3 minutes or so then suddenly disconnected and back to square one. stuck with WiFi searching for available network.

---

### Post by jeremy31 on 2024-09-04
Did this happen with other kernels?

---

### Post by allen-gxm on 2024-09-04
I didn't used WiFi till now, I used to have Ethernet connection so i didn't really used WiFi.
To answer your question, I don't know.

---

### Post by jeremy31 on 2024-09-04
I would like you to boot into an older kernel like 6.8.0-40 and see if the condition still exists

---

### Post by allen-gxm on 2024-09-05
Can you tell me how to do that? Is there any tutorial?
edit: nvm found it

---

### Post by allen-gxm on 2024-09-05
I tried 6.8.0 linux generic, 6.8.0-40 from ubuntu but anything below 6.8.0-41 is being wierd like half of the stuff on my menu goes even my ethernet so had to fall back to 6.8.0-41
i also tried 6.10.8 which worked just like 6.8.0-41 but no wifi still

---

### Post by allen-gxm on 2024-09-12
Fix : I reseated my network adapter inside my laptop and its working, tho i completely removed ubuntu and installed arch.

---

