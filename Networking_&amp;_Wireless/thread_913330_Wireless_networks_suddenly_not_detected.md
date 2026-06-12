---
title: "Wireless networks suddenly not detected"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by yavamoni on 2008-09-07
I am using ubuntu 8.04. I recently upgraded to kernel 2.6.27-1-generic.

I have an Intel 4965AGN WiFi card, which was automatically detected. Sometimes after a restart in different networks, the network wouldn´t be detected, after reading around I found that by erasing the file /etc/networks/interfaces, and restarting the current networks were found. 

However this trick isn´t working any longer.

The network is just not detected (but it is active as other machines, and the same one when restarted in the "other OS", detect it). There is no list of available networks, and if I choose it manually, the "starting interface" takes a long time and finally gives an error (little orange exclamation mark on the network tray applet) During that time the signal intensity meter is in zero.

I wonder if there is some way to re-check for available networks. What else could be wrong? I am sure the password is correct... and everything was working the day before.

This is some commands I run to see if I could understand better, but I really can´t.
```
mance@monica-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0



``````




mance@monica-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network DISABLED      
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:1d:60:6c:14:63
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:97:8e:c3
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
mance@monica-laptop:~$ lspci -nn | grep -i Network
05:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection [8086:4229] (rev 61)


``````






mance@monica-laptop:~$  uname -m
x86_64


``````




mance@monica-laptop:~$ uname -a
Linux monica-laptop 2.6.27-1-generic #3 SMP Wed Aug 13 19:47:26 UTC 2008 x86_64 GNU/Linux


``````



mance@monica-laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     No scan results

mance@monica-laptop:~$ 

```

Any ideas? Any more info I could gather to help? 

Thanks!

---

### Post by yavamoni on 2008-09-10
Anything I should check? Any guide I should read? thanks!!!!

---

