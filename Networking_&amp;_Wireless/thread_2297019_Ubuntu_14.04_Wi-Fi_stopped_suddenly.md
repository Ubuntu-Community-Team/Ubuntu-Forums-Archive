---
title: "Ubuntu 14.04 Wi-Fi stopped suddenly"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by pavel27 on 2015-09-30
Hi, I faced with problem. I have HP Compaq laptop with dual boot (Win 10 an Ubuntu 14.04. Everything has been OK during few months, but suddenly Wi-fi stopped at all in Ubuntu. The connection is not enabled in fact. Wifi still works in Windows. After reading some threads, I did:
[B]iwconfig
[/B]```
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point:Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTSthr:off   Fragment thr:off 
          Power Management:off 
          
lo        no wireless extensions.
```
**rfkill list all **
```
0: phy0: Wireless LAN
    Soft blocked: no 
    Hard blocked: no 
1: hci0: Bluetooth 
    Soft blocked: no 
    Hard blocked: no 
2: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
3: hp-bluetooth: Bluetooth 
    Soft blocked: no 
    Hard blocked: no
```
[B]lspci -knn | grep Net -A2
[/B]```
02:00.0 Network controller [0280]:Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: Hewlett-Packard CompanyDevice [103c:1785] 
    Kernel driver in use: ath9k
```
Please, help me! What should I do? Thank you for your time

---

### Post by praseodym on 2015-09-30
```


wlan0     IEEE 802.11bgn  ESSID:off/any 
          Mode:Managed  Access Point:Not-Associated   Tx-Power=[COLOR="#FF0000"]0 dBm[/COLOR]   
```
Wifi is turned off. Button, switch, key or key combo? Checked the BIOS settings?

---

### Post by pavel27 on 2015-09-30
I've tried press f12 key (wireless on/off on my laptop) and activate/deactivate flying mode.
> **praseodym said:**
> Checked the BIOS settings?
I don't get how to. I opened BIOS and didn't see anything like WLAN enabled/disabled. Is it possible that there is no wi-fi settings in my BIOS?

---

### Post by praseodym on 2015-10-01
Is it a BIOS or an (U)EFI?

If BIOS: Reset it to default settings (here with F9) and save&exit (here: F10)

---

### Post by pavel27 on 2015-10-01
Thank you for your time! Actually, problem is solved now but...I don't know why :D I connected via wire and just after it I've seen normal network manager menu and turned on wi-fi by key. So now wi-fi is working normally. It seems like a kind of magic :D

---

### Post by SimonHGR on 2015-10-02
Oh serendipity! I just had the exact same problem and was freaking out. Many thanks, you solved my problem at least. (I had somehow nudged the "turn wifi off" button on my keyboard.)

---

