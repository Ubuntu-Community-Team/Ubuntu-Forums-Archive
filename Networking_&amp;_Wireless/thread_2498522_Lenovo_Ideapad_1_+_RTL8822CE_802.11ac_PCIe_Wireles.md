---
title: "Lenovo Ideapad 1 + RTL8822CE 802.11ac PCIe Wireless Network + 24.04 = Terrible WiFi"
date: 2024-06-17
forum: Networking &amp; Wireless
---

### Post by irishnewguy on 2024-06-17
Hey there folks.

So the above combo, Noble Numbat, Lenovo Ideapad 1, with RTL8822CE 802.11ac PCIe Wireless Network Card is giving horrendous WiFi speeds.

Details....

sudo lshw -C network
  *-network                 
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: More numbers here
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=6.8.0-35-generic firmware=N/A ip=192.168.the.usual latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:138 ioport:1000(size=256) memory:a1100000-a110ffff

iwconfig
lo        no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"MY_NETWORK_HERE"  
          Mode:Managed  Frequency:5.3 GHz  Access Point: THOSE NUMBERS   
          Bit Rate=650 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=49/70  Signal level=-61 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:118   Missed beacon:0

Now, the router is about 4 metres away, 12 - 14 feet, the other side of a door, so....    Would switching to 2.4 GHZ help and then if so......  HOW?

---

### Post by currentshaft on 2024-06-18
How have you measured "horrendous WiFi speeds"? What test have you run to determine it's "terrible"?

---

