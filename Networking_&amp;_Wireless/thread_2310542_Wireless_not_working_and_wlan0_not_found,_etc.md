---
title: "Wireless not working and wlan0 not found, etc"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by eddymeivogel on 2016-01-20
So after a long while I decided to use ubuntu again and it seems that my wireless driver isn't working. 
well, I have no idea how to fix this. So I post it here hoping someone can help me :) 
Thanks in advance.
(check Attachment for more information?)


(iwconfig, rfkill list all and ifconfig)
```

quget@Quget-Station:~$ iwconfig
wlp7s0 IEEE 802.11abgn ESSID:off/any 
Mode:Managed Access Point: Not-Associated Tx-Power=0 dBm 
Retry short limit:7 RTS thr:off Fragment thr:off
Power Management:off

lo no wireless extensions.


enp8s0 no wireless extensions.


quget@Quget-Station:~$ 
quget@Quget-Station:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
quget@Quget-Station:~$ 
quget@Quget-Station:~$ ifconfig
enp8s0 Link encap:Ethernet HWaddr 30:65:ec:69:d3:75 
inet addr:192.168.1.13 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::3265:ecff:fe69:d375/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:9580 errors:0 dropped:0 overruns:0 frame:0
TX packets:6894 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:8139710 (8.1 MB) TX bytes:1469112 (1.4 MB)
Interrupt:19 


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:65536 Metric:1
RX packets:642 errors:0 dropped:0 overruns:0 frame:0
TX packets:642 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:59010 (59.0 KB) TX bytes:59010 (59.0 KB)


wlp7s0 Link encap:Ethernet HWaddr 5c:93:a2:9c:a4:31 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)


```

---

### Post by kc1di on 2016-01-20
[this thread]("http://askubuntu.com/questions/607707/ath10k-installation") on Ask ubuntu may be of help to you. I think your missing the firmware for your card.

---

### Post by eddymeivogel on 2016-01-20
> **kc1di said:**
> [this thread]("http://askubuntu.com/questions/607707/ath10k-installation") on Ask ubuntu may be of help to you. I think your missing the firmware for your card.
I'm afraid that the solutions given there doesn't work.

This is how the folder looks like now, 

[https://imgur.com/rxfOAAA](https://imgur.com/rxfOAAA)

---

### Post by jeremy31 on 2016-01-20
Might just need ```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```
Reboot

It is getting the firmware and can see wireless networks

---

### Post by eddymeivogel on 2016-01-20
> **jeremy31 said:**
> Might just need ```
echo "options ath10k_core skip_otp=Y" | sudo tee /etc/modprobe.d/ath10k_core.conf
```
Reboot

It is getting the firmware and can see wireless networks

Thanks! it appears to be working now, I'm missing the network icon on my panel, I think that problems is with Mate.
Since it does show on Unity/at login screen. If anyone know something for that it would be cool. This problem is Solved!

---

### Post by kc1di on 2016-01-21
Glad you got it going :) 
Please take a moment and mark the thread as solved.

---

