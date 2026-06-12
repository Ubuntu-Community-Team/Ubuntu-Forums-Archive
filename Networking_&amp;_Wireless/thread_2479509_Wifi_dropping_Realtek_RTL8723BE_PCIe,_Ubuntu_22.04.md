---
title: "Wifi dropping: Realtek RTL8723BE PCIe, Ubuntu 22.04.1"
date: 2022-09-27
forum: Networking &amp; Wireless
---

### Post by mvsfrasson on 2022-09-27
Hi. My wifi is dropping very frequently, every 10 minutes or so. Reboot sometimes reconnect, sometimes not.

I have followed "Before posting in Networking & Wireless". Full output is in [https://pastebin.com/aLTEHK0E](https://pastebin.com/aLTEHK0E)
Part of it is bellow. 

I appreciate all help. Thanks.

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 22.04.1 LTS
Release:    22.04
Codename:    jammy

##### kernel ############################

Linux 5.15.0-48-generic #54-Ubuntu SMP Fri Aug 26 13:26:29 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
    Subsystem: Lenovo RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [17aa:3821]
    Kernel driver in use: r8169

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Lenovo Z50-75 [17aa:b736]
    Kernel driver in use: rtl8723be

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8723be             159744  0
btcoexist             249856  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                40960  1 rtl8723be
rtlwifi               114688  4 rtl_pci,rtl8723be,btcoexist,rtl8723_common
mac80211             1253376  3 rtl_pci,rtl8723be,rtlwifi
cfg80211              974848  2 rtlwifi,mac80211
libarc4                16384  1 mac80211
ideapad_laptop         24576  0
sparse_keymap          16384  1 ideapad_laptop
platform_profile       16384  1 ideapad_laptop
wmi                    32768  1 ideapad_laptop
video                  61440  2 ideapad_laptop,i915

##### interfaces ########################

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd <MAC address>
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp2s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether <MAC 'enp2s0' [IF1]> brd <MAC address>
3: wlp3s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp3s0' [IF2]> brd <MAC address>
    inet 192.168.3.103/24 brd 192.168.3.255 scope global dynamic noprefixroute wlp3s0
       valid_lft 6993sec preferred_lft 6993sec
    inet6 fe80::e474:8e6f:b55f:b476/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

lo        no wireless extensions.

enp2s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"Frasson"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Frasson' [AC1]>   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=56/70  Signal level=-54 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:20   Missed beacon:0

---

### Post by jeremy31 on 2022-09-27
Start with ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
iwconfig wlp3s0 power off
systemctl restart network-manager.service
```

See if it works better with power management off

---

### Post by mvsfrasson on 2022-09-28
After some scary behavior (wifi interface disabled for a long time), it turned out everything ok. My laptop is hours connected, so I expect that this issue is solved. Thanks, @jeremy31 !

---

