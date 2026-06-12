---
title: "Ubuntu 16.04 New Install - Wifi Keeps Dropping"
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by bl79 on 2016-11-04
Just installed Ubuntu to dual boot with Windows. This is my first foray into Linux so please bear with me.

Anyway, my wifi regularly drops and loses connection. The wifi connection bar doesn't indicate anything is wrong though, pages just wont load. Disconnecting and reconnecting the wifi immediately corrects the issue consistently. Drops are somewhat random but will sometimes happen within 10m of each other. Windows doesn't have any issue

I've turned power management off. I disconnected the b/g/n connection as well as I thought it may be interfering with my network card. Tried some google fixes but nothing seems to have helped. I wish I kept a better record of what I had changed - mostly power management and updates though.

Kind of at a loss at this point as far as next steps

iwconfig:
```
lo        no wireless extensions.


enp0s25   no wireless extensions.


eno1      no wireless extensions.


wlxdc85de003ac1  IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=30 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlp2s0    IEEE 802.11abg  ESSID:"CFMWM"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:7F:28:C0:FE:C2   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```



Please let me know if you need any more information for troubleshooting. Thanks!

---

### Post by ajgreeny on 2016-11-04
We need more info in order to help you so see the thread at [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) and run the **Wireless-info script** that is shown there and show us the output.

It will tell us a lot more about your hardware than you have told us so far and help us to help you.

---

### Post by bl79 on 2016-11-05
Oof, missed the sticky. Sorry!

Ran the update and rebooted and then also ran the script and realized I have a broadcom card. Followed the broadcom driver instructions but wifi still drops. 

Script output attached.

---

### Post by bl79 on 2016-11-08
Any ideas? Wifi still drops often but disconnect/reconnect fixes it. I followed the Broadcom instructions to reinstall the latest bcmwl-kernel-source but it didn't help

Also fwiw when I click on the wireless icon I see 2 different network adapters available, the Broadcom BCM 4360 802.11ac as well as a Ralink 802.11 n WLAN. I disconnected the Ralink though as I initially thought it may be interfering. 

This is on a [SIZE=2]desktop[/SIZE] with a **[SIZE=2][TP-Link Archer T8E AC1750 Dual Band Wireless PCI Express Adapter]("https://www.amazon.com/gp/product/B00RL4A314/ref=oh_aui_search_detailpage?ie=UTF8&psc=1") - [/SIZE]**[SIZE=2]appears to use the BCM4360 chipset so far as I can tell (still not sure where the ralink comes from, embedded in the mobo?)[/SIZE]**[SIZE=2][/SIZE]**

on an [Intel LGA1155 mobo]("https://www.amazon.com/gp/product/B007SSJWDS/ref=oh_aui_search_detailpage?ie=UTF8&psc=1")

When I search for the broadcom BCM4360 a lot of macbook issues come up - haven't found many remedies for my particular issue though.

---

