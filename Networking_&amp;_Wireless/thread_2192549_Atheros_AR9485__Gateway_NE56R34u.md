---
title: "Atheros AR9485 / Gateway NE56R34u"
date: 2013-12-08
forum: Networking &amp; Wireless
---

### Post by nbokowy on 2013-12-08
Hello everyone.  This is my first post so if I screwed something up, sorry 8)

I recently purchased a Gateway NE56R34u for my brother.  I put Ubuntu 12.04 on it and sometimes after I put in my wireless password it will attempt to connect but never actually make the connection.  This will go on for a few minutes or longer.  Eventually if I wait long enough it will connect.  Then it usually stays connected for a long while.  But this is very annoying.

I don't know much about computers but I can follow detailed directions.  Based on from what i've been reading I think you will need the below information from me.


Code:
iwconfig
lo        no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"RubyDeer"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 98:FC:11:3F:9F:A6   
          Bit Rate=72.2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:62   Missed beacon:0


eth0      no wireless extensions.


Code:
```
sudo lshw -C network-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 20:89:84:77:e6:9f
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Wireless interface
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: bc:85:56:32:f5:70
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-57-generic-pae firmware=N/A ip=192.168.1.145 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:c0500000-c057ffff memory:afc00000-afc0ffff

```

Any help would be greatly appreciated! 8)

Thanks

---

### Post by praseodym on 2013-12-08
Deactivate the hardware encryption of the driver via:
```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```

---

### Post by nbokowy on 2013-12-08
Thank you very much!  This seems to have fixed my brother's computer.  I also have the same computer as his and was wondering if I would have to do the same commands to fix mine?  My info is below.   Sorry for the noob questions 8)



```
 iwconfig
wlan0     IEEE 802.11bgn  ESSID:"RubyDeer"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 98:FC:11:3F:9F:A6   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=67/70  Signal level=-43 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0


lo        no wireless extensions.


eth0      no wireless extensions.






*-network               
       description: Ethernet interface
       product: NetLink BCM57785 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: b8:88:e3:5a:3a:16
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 firmware=sb latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 memory:c0430000-c043ffff memory:c0440000-c044ffff memory:c0450000-c04507ff
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 74:e5:43:70:01:19
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-44-generic firmware=N/A ip=192.168.1.148 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:c0500000-c0503fff
```

---

### Post by wildmanne39 on 2013-12-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by praseodym on 2013-12-09
Try a driver update:
```

sudo apt-get install --reinstall build-essential linux-headers-$(uname -r)
wget media.cdn.ubuntu-de.org/forum/attachments/39/19/5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
tar xvf 5443987-rtl_92ce_92se_92de_8723ae_88ee_0012.0207.2013.tar.gz
cd rtl_92ce_92se_92de_8723ae_88ee_linux_mac80211_0012.0207.2013/
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
sudo cp -r firmware/* /lib/firmware  
```
Reboot.

---

