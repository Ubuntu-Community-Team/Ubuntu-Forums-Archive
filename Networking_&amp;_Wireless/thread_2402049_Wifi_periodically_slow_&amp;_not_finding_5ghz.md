---
title: "Wifi periodically slow &amp; not finding 5ghz"
date: 2018-09-25
forum: Networking &amp; Wireless
---

### Post by robinfriedli on 2018-09-25
Hi all!
I recently bought a new router (an ASUS RT-AC88U) that has both a 2.4 GHz and a 5 GHz channel. The router works fine on all other devices including a windows partition on the same PC. However, Ubuntu only finds the 2.4 GHz network, both in the wifi settings and when running ```
sudo iw wlp5s0 scan
```. On top of that, the connection gets unbearably slow every 10 minutes or so but returns to normal immediately when turning wifi off and on again. I tried defining my country code using
```
sudo iw reg set CH
sudo sed -i 's/^REG.*=$/&CH/' /etc/default/crda
```
with no luck. I also tried using the 2.4 GHz channel on other devices and it worked on all of them. I even completely reinstalled ubuntu because I was moving it to a different drive anyway.
My network adapter is an ASUS PCE-AC56 an I'm using the "Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source" driver. Ubuntu version is 18.04.1

iwlist chan returns this:
```
robinfriedli@Robin-Ubuntu:~$ iwlist chan
wlp5s0    32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 32 : 5.16 GHz
          Channel 34 : 5.17 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 66 : 5.33 GHz
          Channel 68 : 5.34 GHz
          Channel 96 : 5.48 GHz
          Channel 98 : 5.49 GHz
          Channel 100 : 5.5 GHz
          Current Frequency:2.457 GHz (Channel 10)


enp0s31f6  no frequency information.


lo        no frequency information.



```

---

