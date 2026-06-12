---
title: "[SOLVED] No wireless after upgrade!"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by ashoksagar on 2008-11-01
I just upgraded from 8.04 to 8.10 and have no wireless connection anymore. What is strange is this output I get when i run
'lshw -C network' :

*-network:1 DISABLED
       description: Wireless interface
       product: Atheros AR5001X+ Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wifi0
       version: 01
       serial: 00:0f:3d:a9:30:d3
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.9 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


Why is it disabled and how do I re-enable it again? Any help would be appreciated. Thanks in advance.

---

### Post by ashoksagar on 2008-11-01
BTW, I forgot to add that I failed trying to manually bring up the interface.

---

### Post by gewitty on 2008-11-01
Same problem here. 

*-network:0 DISABLED
     description: Wireless interface
     physical id: 1
     logical name: wlan0
     serial: 00:30:bd:64:82:ae
     capabilities: ethernet physical wireless
     configuration: broadcast=yes driver=at76_usb driverversion=0.14beta1 firmware=8.101.5-84 wireless=EEE 802.11b

Never had a problem with any previous versions of Ubuntu.

---

### Post by ashoksagar on 2008-11-01
As you can see from my first post, my connection is wifi0. Now when I connect manually, and use iwconfig I get ath0 as the one with wireless extensions and still can not ping my router although it says connected. i can see the traffic coming through wifi0 in network tools, with ath0 just idling, so what is happening here?

---

### Post by ashoksagar on 2008-11-01
I removed networkmanager and edited /etc/network/interfaces to activate just ath0, not wifi0. Now everything is working fine.

---

### Post by IreneMcKeever on 2008-11-02
Can someone walk me through terminal mode about this wireless problem I think this is my issue

---

### Post by sizzlefire on 2008-11-02
I have the same exact issue, it says wireless is disabled, but it was just enabled before I upgraded. I like 8.10 overall, and I hope theres a way to fix this :(

---

