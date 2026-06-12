---
title: "Wifi trouble with Qualcomm Atheros &amp; Ubuntu 16.04"
date: 2017-01-09
forum: Networking &amp; Wireless
---

### Post by sh809 on 2017-01-09
Hello !

I have a problem with a new Acer E5-573G computer (with a Qualcomm Atheros device [168c:0042]). I have installed Ubuntu 16.04 in dual boot with windows 10 and for some mysterious reason I can't connect to internet from ubuntu using the Wifi of my work place... I have been looking for a solution for a few days already but I could not find anything. (I have also already asked to the administrator of the network, but he is not familiar with linux and has no idea what my problem is)

For the record:
-I connect properly to all the other wifi I tried.
-I connect properly when I boot on windows 10.
-I have another, older, laptop under ubuntu 15.10 which can connect to internet on this wifi without problems (I'm writting from this one)

From my new computer booted on Ubuntu 16.04, I can connect to the wifi, I receive an IP adresse, if I ping my own IP address it works, but I don't get access to internet and nothing else respond to ping (using IP), not even the router or the DNS server: I always get the answer "From 192.168.12.23 Destination Host Unreachable" where 192.168.12.23 is my own IP.

Ping from another computer on the network to the IP of my computer does not work either.
The arp command only display one line with the IP adresse of the router, "(incomplete)" instead of the HWaddress and no other informations.


Any suggestion will be very welcom :-)

I'm attaching the result of the wireless-info script for both the new computer that can't acess the internet when it is connected to the wifi (wireless-info.tar.gz) but also for the older computer that can connect (wireless-info 2.tar.gz) in case it brings some additional information on the network...


Thank you !

---

### Post by jeremy31 on 2017-01-09
I would file a [bug report](https://ubuntuforums.org/showthread.php?t=1011078) as this is common with the ath10k devices

It seems that if the following error is in dmesg, it doesn't work
```
[   51.776196] ath10k_pci 0000:03:00.0 wlp3s0: disabling HT as WMM/QoS is not supported by the AP
[   51.776200] ath10k_pci 0000:03:00.0 wlp3s0: disabling VHT as WMM/QoS is not supported by the AP
```

---

