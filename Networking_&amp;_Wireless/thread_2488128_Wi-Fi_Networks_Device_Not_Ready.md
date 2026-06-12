---
title: "Wi-Fi Networks Device Not Ready"
date: 2023-06-23
forum: Networking &amp; Wireless
---

### Post by suomalainen on 2023-06-23
Hello My Friends!

I've been trying to solve for the last 5 hours why I cannot connect to wi-fi. All I see in the network manager is the text "Wi-Fi Networks Device Not Ready". When WIFI is working this text is replaced with the ESSID of the networks in vicinity.

I'm running Classic Ubuntu 22.04 LTS

In Terminal:

$ sudo iwlist wlp5s0 scan | grep ESSID
                    ESSID:"Luu5"
                    ESSID:"Luu5_5G"
                    ESSID:"optimumwifi"
                    ESSID:"optimum"


$ $ iwconfig
lo        no wireless extensions.

eno1      no wireless extensions.

wlp5s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off


So I think this much must tells us that the card is working cause the ESSID of other networks can be see.

Also, more terminal commands I ran:

$ lshw -C network
WARNING: you should run this program as super-user.
  *-network                 
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlp5s0
       version: 01
       serial: 00:26:82:61:8c:95
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **driver=ath9k** driverversion=5.19.0-45-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:a1100000-a110ffff

$ lspci | grep -i wireless
05:00.0 Network controller: Qualcomm Atheros AR928X Wireless Network Adapter (PCI-Express) (rev 01)


Would anyone like to help me get this WIFI working?

Thanks!

---

### Post by suomalainen on 2023-06-24
Bump....

---

### Post by suomalainen on 2023-06-25
Bump

---

