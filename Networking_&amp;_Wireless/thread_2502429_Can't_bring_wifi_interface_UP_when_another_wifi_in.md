---
title: "Can't bring wifi interface UP when another wifi interface (exact same model) is UP"
date: 2024-11-14
forum: Networking &amp; Wireless
---

### Post by nicoeverquest on 2024-11-14
Hello,


I have added a new wifi Wifi adapter to my laptop, exactly the same model as the one I already have. (Yes, I need to have 2 wifi adapters running)


nicolas@localhost:~$ ip -br link show | grep wlx
wlx5811226b0e7d  UP             58:11:22:6b:0e:7d <BROADCAST,MULTICAST,UP,LOWER_UP> 
wlx5811226b0e7b  DOWN           58:11:22:6b:0e:7b <NO-CARRIER,BROADCAST,MULTICAST,UP> 



wlx5811226b0e7d is the first wifi card I have, working perfectly. Exactly the same model so same driver than the one wlx5811226b0e7b I just added.



But I can't set wlx5811226b0e7b UP


nicolas@localhost:~$ sudo ip link set wlx5811226b0e7d up
nicolas@localhost:~$ ip -br link show wlx5811226b0e7b
wlx5811226b0e7b  DOWN           58:11:22:6b:0e:7b <NO-CARRIER,BROADCAST,MULTICAST,UP> 
nicolas@localhost:~$ sudo dmesg | grep wlx5811226b0e7b
[    6.629653] mt76x0u 1-4:1.0 wlx5811226b0e7b: renamed from wlan1



I stopped / started the networking manage but it is same :
sudo systemctl stop NetworkManager

sudo systemctl start NetworkManager



nicolas@localhost:~$ sudo rfkill list
0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no



(The first asus-wlan is the built in wifi chip that is not used as there is no linux driver for it)


I don't have any error message to guide me.



Is there something to prevent Ubunntu from having 2 Wifi interfaces running at the same time?


Thanks

---

### Post by morrownr on 2024-11-17
> Is there something to prevent Ubuntu from having 2 Wifi interfaces running at the same time?

I often have up to 5 wireless interface going at the same time. To answer your question: It depends on the driver for the wireless devices. Please tell me the chipsets in the adapters that you have.

---

