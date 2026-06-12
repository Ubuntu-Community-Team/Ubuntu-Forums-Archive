---
title: "Lenovo 3000 N200 Wifi, Intel Pro/Wireless 3945ABG"
date: 2014-12-06
forum: Networking &amp; Wireless
---

### Post by chris325 on 2014-12-06
So I've decided to convert my Lenovo into a Ubuntu boot, problem is I cant ge the wifi to work on either my USB adapter or my internal wifi card.

Both networks are coming up, but disabled up in the taskbar, and when I try to enable wifi it just immediately turns back off.

rfkill list gives no soft blocks or hard blocks.

My wireless card is the Intel Pro/Wireless 3945ABG [Golan]

and my USB wifi is the Realtek 802.11n WLAN Adapter.

Any help from some Linux masters would be appreciated because I'm royally stuck :(.  Thanks for the time.

---

### Post by chili555 on 2014-12-06
Please detach the USB as we'll fix the Intel and we don't want to fight any conflicts. Then show us:```
iwconfig
rfkill list all
dmesg | grep iwl
```Thanks.

---

### Post by chris325 on 2014-12-06
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
lo        no wireless extensions.

eth0      no wireless extensions.




0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



[   29.048294] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   29.048299] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   29.048358] iwl3945 0000:06:00.0: can't disable ASPM; OS doesn't have ASPM control
[   29.102279] iwl3945 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   29.102282] iwl3945 0000:06:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   29.102359] iwl3945 0000:06:00.0: irq 45 for MSI/MSI-X
[   29.224556] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'



Thank you for the help.

---

### Post by chili555 on 2014-12-07
> 1: acer-wireless: Wireless LAN
[COLOR="#FF0000"]Soft blocked: yes[/COLOR]
Hard blocked: noCan you unblock and therefore start the wireless with:```
sudo rfkill unblock all
rfkill list all
```What wmi module is loaded?```
lsmod | grep acer
```

---

### Post by chris325 on 2014-12-07
After I do the sudo rfkill unblock all it still shows up soft blocked.


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no


acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
wmi                    18673  1 acer_wmi
video                  18903  2 i915,acer_wmi

---

### Post by chili555 on 2014-12-07
How about if we unload acer-wmi?```
sudo modprobe -r acer-wmi
sudo rfkill unblock all
rfkill list all
```If this helps, we'll blacklist acer-wmi.

---

### Post by chris325 on 2014-12-07
Yes that did it! You're the best, it's amazing how I've been looking for this command for a few weeks now and it's such a tiny command.  

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2014-12-07
Let's blacklist the module so it doesn't interfere any more:```
sudo -i
echo "blacklist acer-wmi"  >>  /etc/modprobe.d/blacklist.conf
exit
```You should be all set.

Glad it's working. Please use thread tools at the top to mark Solved.

---

### Post by chris325 on 2014-12-07
Thanks again for you're help.  The Ubuntu community is the best community for support.

---

