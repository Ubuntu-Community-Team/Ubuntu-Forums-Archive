---
title: "msi ge620 ath9k Wifi Hard blocked in Ubuntu"
date: 2015-02-12
forum: Networking &amp; Wireless
---

### Post by d4v3d on 2015-02-12
Hello i have a problem with my wifi in ubuntu.
Im using dual boot and when i start my PC my wifi doesnt work and i have to restart, go to windows, activate the wifi and come back to Ubuntu.
This is annoying.

Fn F10 doesnt work. 

Please help me :(
Some commands i have tried:

[B]rfkill list
[/B]```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

[B]rfkill unblock all
[/B]Doesnt fix it


**lspci -nk | grep -A2 0280:**
```
04:00.0 Network controller [0280]: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: AzureWave AW-NE785 / AW-NE785H 802.11bgn Wireless Full or Half-size Mini PCIe Card [1a3b:1089]
    Kernel driver in use: ath9k

```

**lsmod | grep -e ath9k -e msi**
```
msi_wmi                13354  0 
sparse_keymap          13948  1 msi_wmi
ath9k                 164164  0 
ath9k_common           13551  1 ath9k
ath9k_hw              453856  2 ath9k_common,ath9k
ath                    28698  3 ath9k_common,ath9k,ath9k_hw
mac80211              630653  1 ath9k
cfg80211              484040  3 ath,ath9k,mac80211
wmi                    19177  3 msi_wmi,mxm_wmi,nouveau

```

---

