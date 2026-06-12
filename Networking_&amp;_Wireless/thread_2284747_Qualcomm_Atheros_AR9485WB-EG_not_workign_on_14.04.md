---
title: "Qualcomm Atheros AR9485WB-EG not workign on 14.04"
date: 2015-07-01
forum: Networking &amp; Wireless
---

### Post by nunocart on 2015-07-01
So I recently installed Xubuntu on my laptop, dualbooted with Windows. 

  Everything works perfectly on the Windows side, but in Xubuntu, for   some reason it doesn't either recognise or it can't access my network   card so I can't connect to the wifi. I have updated the Kernel and   Ubuntu itself (with the sudo apt-get update 
sudo apt-get upgrade) , I have checked for drivers on the manufacturer website(it's a Qualcomm Atheros AR9485WB-EG).

  I know almost nothing about Linux and Ubuntu so I am clueless on how   to solve this but I really need it to work as fast as possible so all   help would be highly appreciated.

  
Edit:

  lshw -c net :

  *-network DISABLED      
   description: Wireless interface
   product: AR9485 Wireless Network Adapter
   vendor: Qualcomm Atheros
   physical id: 0
   bus info: pci@0000:03:00.0
   logical name: wlan0
   version: 01
   serial: 24:0a:64:cb:f1:7f
   width: 64 bits
   clock: 33MHz
   capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
   configuration: broadcast=yes driver=ath9k  driverversion=3.16.0-41-generic firmware=N/A latency=0 link=no  multicast=yes wireless=IEEE 802.11bgn
   resources: irq:18 memory:f7900000-f797ffff memory:f7980000-f798ffff
  *-network
   description: Ethernet interface
   product: QCA8171 Gigabit Ethernet
   vendor: Qualcomm Atheros
   physical id: 0
   bus info: pci@0000:04:00.0
   logical name: eth0
   version: 10
   serial: bc:ee:7b:46:f6:ed
   size: 100Mbit/s
   capacity: 1Gbit/s
   width: 64 bits
   clock: 33MHz
   capabilities: pm pciexpress msi msix bus_master cap_list ethernet  physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=alx  duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=twisted  pair speed=100Mbit/s
   resources: irq:52 memory:f7800000-f783ffff ioport:d000(size=128)


  uname -a :

  Linux XubuntoV2 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


  rfkill list all :

  0: phy0: Wireless LAN
Soft blocked: no
Hard blocked: no

1: acer-wireless: Wireless LAN
Soft blocked: yes
Hard blocked: no

4: hci0: Bluetooth
Soft blocked: no
Hard blocked: no
     
Edit:
i have tryed the rfkill unblock all and rfkill unblock 1, nothing happens.

---

### Post by jeremy31 on 2015-07-01
Is it actually an acer laptop?

---

### Post by nunocart on 2015-07-01
.

---

### Post by nunocart on 2015-07-01
It is an asus laptop.

---

### Post by jeremy31 on 2015-07-01
Since it isn't an acer ```
echo "blacklist acer_wmi" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot and see if wifi works or you may need to ```
rfkill unblock all
```

---

