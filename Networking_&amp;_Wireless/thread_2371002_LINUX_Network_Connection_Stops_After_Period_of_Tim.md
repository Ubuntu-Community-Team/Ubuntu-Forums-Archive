---
title: "LINUX Network Connection Stops After Period of Time"
date: 2017-09-09
forum: Networking &amp; Wireless
---

### Post by foxes45 on 2017-09-09
Hi everyone, I am ubuntu 17.04 user. My PC always automaticly stops the network connection (e.g wifi, android usb tether). The problem is the network indicator is still active, even the connection information  still shows the network is running. In first 1 minute, when I start browser, or try "ping google.com" command in terminal, the network is normal, but after that the browser cannot opens any website, and the "ping google.com" command shows nothing :(

I also have a laptop with ubuntu 17.04 installed, but does not have any problem. Because I also use same router for my PC also my laptop. I don't have idea for fixing this problem



note : It also happens when I boot the PC with kali live usb or if I boot steam os

---

### Post by praseodym on 2017-09-09
There is a bug in 17.04, please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```

---

### Post by foxes45 on 2017-09-10
Then I tried to use android usb tethering for my PC

Also i tried to check with "dmesg | grep usb0"
it shows this

```
[5435.502604] rndis_host 1-4:1.0 usb0: kevent 1 may have been dropped
```

---

### Post by codefu2 on 2017-09-11
> **foxes45 said:**
> Hi everyone, I am ubuntu 17.04 user. My PC always automaticly stops the network connection (e.g wifi, android usb tether). The problem is the network indicator is still active, even the connection information  still shows the network is running. In first 1 minute, when I start browser, or try "ping google.com" command in terminal, the network is normal, but after that the browser cannot opens any website, and the "ping google.com" command shows nothing :(

I also have a laptop with ubuntu 17.04 installed, but does not have any problem. Because I also use same router for my PC also my laptop. I don't have idea for fixing this problem



note : It also happens when I boot the PC with kali live usb or if I boot steam os



I have these exact symptoms, and have tsed to the same extent (ruled out network wide-issue w/ alternate ubuntu 17.04 running on same connection). I have not tried android usb tether, but have wired to enet with the same symptoms. 
 

I have attempted to run the following commands as listed:

> **praseodym said:**
> There is a bug in 17.04, please run

```
echo -e "\n[device]\nwifi.scan-rand-mac-address=no" | sudo tee -a /etc/NetworkManager/NetworkManager.conf
sudo sed -i "s/wifi.powersave = 3/wifi.powersave = 2/g" /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
sudo systemctl restart network-manager.service
```



I did show a disconnected/connected alert, but browser is still not displaying pages, returns "server not found."

I believe this may have some information of consequence: 
```
:~$ dmesg | grep wlp1s0
[   28.135390] ath5k 0000:01:00.0 wlp1s0: renamed from wlan0
[   30.122926] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   30.132759] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   30.144459] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   30.251910] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   31.134310] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[   31.167253] wlp1s0: authenticate with [MAC address]
[   31.171733] wlp1s0: send auth to [MAC address] (try 1/3)
[   31.174504] wlp1s0: authenticated
[   31.180070] wlp1s0: associate with [MAC address] (try 1/3)
[   31.183783] wlp1s0: RX AssocResp from [MAC address] (capab=0x431 status=0 aid=5)
[   31.183890] wlp1s0: associated
[   31.183971] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready
[  610.970884] wlp1s0: deauthenticating from [MAC address] by local choice (Reason: 3=DEAUTH_LEAVING)
[  611.582342] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  611.709883] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[  613.385954] wlp1s0: authenticate with [MAC address]
[  613.394962] wlp1s0: send auth to [MAC address] (try 1/3)
[  613.404273] wlp1s0: authenticated
[  613.412065] wlp1s0: associate with [MAC address] (try 1/3)
[  613.415861] wlp1s0: RX AssocResp from [MAC address] (capab=0x431 status=0 aid=3)
[  613.415993] wlp1s0: associated
[  613.416118] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

```

---

### Post by foxes45 on 2017-09-26
I think problem solved 1 week ago. I have bought TP-LINK TL-WN722N usb wifi adapter and install custom tp-link driver for 4.10 linux kernel because there is no official tp-link driver for kernel 4 above. The networking runs fine even it much faster.

I think there is bug in linux when you use old wired networking or android usb tethering, better move on to wifi. Thanks for the help! :p:p:p
And I'll mark this post as solved

---

