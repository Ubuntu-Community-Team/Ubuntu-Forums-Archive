---
title: "IF: wlan0 state: down"
date: 2017-05-08
forum: Networking &amp; Wireless
---

### Post by statkute on 2017-05-08
I am seeing wlan0 error Connection is limited or no connectivity.

sudo lshw -C network
```
*-network
       description: Wireless interface
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 70:77:81:29:43:f1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=mt7630e driverversion=4.4.0-77-generic firmware=112.3 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f7100000-f71fffff
```

$ iwconfig

```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
eth0      no wireless extensions.
```


$ inxi -Nn
```
Network:   Card-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller driver: r8169
           IF: eth0 state: up speed: 100 Mbps duplex: full mac: 14:dd:a9:0c:d4:64
           Card-2: MEDIATEK MT7630e 802.11bgn Wireless Network Adapter driver: mt7630e
           IF: wlan0 state: down mac: 70:77:81:29:43:f1
```

~$ nmcli dev
```
DEVICE  TYPE      STATE         CONNECTION         
eth0    ethernet  connected     Wired connection 1 
wlan0   wifi      disconnected  --                 
lo      loopback  unmanaged     --    
``` 

Tried to add connection manually
```
ber@LB:~$ nmcli con add con-name "SKY" ifname wlan0 type wifi ssid <ssid>  
Connection 'SKY WISP 1446' (fccf22db-8741-4454-a848-4db163562338) successfully added.
ber@LB:~$ nmcli con modify "SKY" wifi-sec.key-mgmt wpa-psk
ber@LB:~$ nmcli con modify "SKY" wifi-sec.psk <psswd>
ber@LB:~$ nmcli radio wifi on
```
, but it gives the same errors:
"nmcli dev"  -  that wifi is disconnected
"inxi -Nn"  -  that IF: wlan0 state: down


What could be done?

---

