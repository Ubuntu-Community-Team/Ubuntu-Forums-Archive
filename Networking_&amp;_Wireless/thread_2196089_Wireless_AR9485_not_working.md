---
title: "Wireless AR9485 not working"
date: 2013-12-27
forum: Networking &amp; Wireless
---

### Post by pgar23 on 2013-12-27
Hi, I saw post about this, but resolution isn't working. So I am creating new thread.
```

$lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: AR9485 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7d00000-f7d7ffff memory:f7d80000-f7d8ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:03:00.2
       logical name: eth0
       version: 06
       serial: d8:50:e6:38:fc:b5
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8402-1_0.0.1 10/26/11 ip=10.0.0.12 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

```

Following [http://ubuntuforums.org/showthread.php?t=2192472&highlight=ar9485](http://ubuntuforums.org/showthread.php?t=2192472&highlight=ar9485)
The following commands gets the wireless interface available...otherwise when I reboot, ubuntu doesn't see wlan0.

```

echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```

I tried to Load the driver by hand:
```

Code:    
sudo modprobe -v ath9k

```

```

$rfkill list
0: hci0: Bluetooth    Soft blocked: no
    Hard blocked: no
1: asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: asus-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

```

```

root@trapbox:/# grep ath /etc/modprobe.d/*
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/ath9k.conf:options ath9k nohwcrypt=1
/etc/modprobe.d/blacklist-ath_pci.conf:# which ath5k cannot recover. To prevent this condition, stop
/etc/modprobe.d/blacklist-ath_pci.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:#replaced by netathrx.inf ndisgtk
/etc/modprobe.d/blacklist.conf:blacklist ath_pci
/etc/modprobe.d/blacklist.conf:blacklist ath_hal
/etc/modprobe.d/blacklist.conf:blacklist ath9485
/etc/modprobe.d/blacklist.conf:blacklist ath9k

```

Following [http://ubuntuforums.org/showthread.php?t=2192218&highlight=ar9485](http://ubuntuforums.org/showthread.php?t=2192218&highlight=ar9485)
```

echo "options asus_nb_wmi wapf=1" | sudo tee /etc/modprobe.d/asus.conf

```

---

### Post by pgar23 on 2013-12-27
I am running 13.10 Saucy Ubuntu. I solved it with the following, but need to find out how to make this a permanent solution:

I disabled the ndiswrapper driver (netathrx.inf)

```

sudo update-grub
echo "options ath9k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k

```

If anyone knows how to make it permanent, I owuld be appreciative. Thx!

---

### Post by wildmanne39 on 2013-12-27
The commands you ran are permanent they only need to be ran once so it is most likely the ndiswrapper driver needs to be completely purged, you can try this command also to add the ath9k driver to modules to be loaded at boot.
```
sudo su 
echo ath9k >> /etc/modules 
exit
```

---

### Post by pgar23 on 2013-12-27
Thx Wild Man. How would I go about purging ndiswrapper?

---

### Post by Bucky Ball on 2013-12-27
This thread has been marked as solved yet there are still questions so it appears it is not ...

If the problem is solved it is rule of thumb and common courtesy to let the community know what you did to fix the issue. Thanks.

---

### Post by wildmanne39 on 2013-12-28
Like this:
```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
```
did the previous command solve your issue?
Thanks

---

