---
title: "wireless mode change"
date: 2005-10-26
forum: Networking &amp; Wireless
---

### Post by steelisreal on 2005-10-26
My router is a linksys wireless -b and my wireless card is a dell 1350 wireless b/g 

when i do a iwconfig it says my card is in 802.11g

steelisreal@ubuntu:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11g ESSID:off/any
Mode:Managed Frequency:2.412 GHz Access Point: 00:00:00:00:00:00
Bit Rate:54 Mb/s Tx-Power:25 dBm
RTS thr:2347 B Fragment thr:2346 B
Power Management:off
Link Quality:100/100 Signal level:-10 dBm Noise level:-256 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

sit0 no wireless extensions.


could this be the reason my card will not get any dhcp offers?

if so how can i change the card to b mode??

---

### Post by fabiand on 2005-10-27
hey,

you can try to set your essid manualy

```
sudo wiconfig wlan0 essid MYESSID
```

afterwards a

```
sudo dhclient wlan0
```

suppose that there is a method to set which mode to use .. but you will have to use iwpriv to do this .. sory, can't hekp you with taht ..

- fabiand

---

