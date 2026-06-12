---
title: "No network/internet wired/wireless"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by manuel.zass on 2013-11-18
Hello.
I installed lubuntu 13.10 on my Lenovo Ideapad S10-3. At installationsprogress i connected with my wi-fi. It worked fine for 2 hours. Now it's disconnected and can't connect anymore. Other devices are connected without problems.
I tried to connect it with a cable, but no success.

Someone a reason and a solution?

Greets

---

### Post by chili555 on 2013-11-18
First, let's see what wired and wireless devices you have. Please open a terminal and run and post:```
lspci -nn | grep -e 0200 -e 0280
rfkill list all
```Thanks.

---

### Post by manuel.zass on 2013-11-18
I rebootet my device. And now it works with cable.
But wi-fi would be better.

***lspci -nn | grep -e 0200 -e 0280***:
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
09:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)



[B][I]
rfkill list all[/I][/B]
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2013-11-18
Does the wireless come to life if you do:```
sudo modprobe ath9k
```If so, let's get it to load automagically:```
sudo -i
echo ath9k >> /etc/modules
exit
```If not, look for clues here:```
dmesg | grep ath
```

---

