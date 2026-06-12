---
title: "[SOLVED] w500 lenovo no wireless"
date: 2008-11-09
forum: Networking &amp; Wireless
---

### Post by rcmn on 2008-11-09
Intrepid Ibex
lspci
> 03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

iwconfig
> 
lo        no wireless extensions.
eth0      no wireless extensions.
pan0      no wireless extensions.


lshw -C network
>         
  *-network                        
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1c:25:94:06:a6
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 duplex=full firmware=1.8-3 ip=192.168.0.12 latency=0 link=yes module=e1000e multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 0a:bc:5c:ff:0f:8d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



So what next ?  

no ath0 or wlan0 but the prop driver are activated .

so do i have to modprob blabla and get my hands dirty?

---

### Post by rcmn on 2008-11-10
bump

---

### Post by rcmn on 2008-11-10
well this is solved i followed and adapted this 2 posts. I had to get the lenovo INF and use ndiswrapper.

I worked of this
[http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter](http://www.thinkwiki.org/wiki/How_to_install_ndiswrapper_for_the_ThinkPad_11a/b/g/n_Wireless_LAN_Mini_Express_Adapter)
[http://ubuntuforums.org/showthread.php?t=537132](http://ubuntuforums.org/showthread.php?t=537132)
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

**=HOWTO=**
**Pre-requisites:**

- First if the Drivers for Atheros are enable in the "Proprietary drivers" interface .Make sure to deactivate. 
-Or if it use an old driver ,Disable it.
```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

```
-Reboot
- go to lenovo and download the correct driver for your laptop mine was [[COLOR="Blue"]here[/COLOR]]("http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-70480"). After you should have a CAB that look like this 7xxxxxxx.exe
- install the necessary tools. 
```

#sudo apt-get install ndiswrapper-common cabextract

```

**Install**

-start in the folder where the 7xxxxxxx.exe file reside
```

#cd ~/.../ && cabextract 7xxxxxxx.exe

```

-then install the driver
```
#cd WINXP_2K/ && sudo /usr/sbin/ndiswrapper -i NETxxxx.INF
```
a lot of lines will show .

-check if the driver is installed
```
#ndiswrapper -l

netathw : driver installed
        device (168C:001C) present (alternate driver: ath_pci)

```

-now load the module
```
#sudo modprobe ndiswrapper
```

no check wlan0 is present.
```
ifconfig
```

**Post-install :**

the ndiswrapper module will unload after each reboot. So to have it loaded everytime
edit: /etc/modules
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
**ndiswrapper**

```

---

### Post by gatman3 on 2008-11-24
Weird, my W500 came with Intel 5100 AGN, not Atheros wi-fi:

> 03:00.0 Network controller: Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection

Not supported natively in 8.04, well supported in 8.10 (kernel 2.6.27).

---

### Post by rcmn on 2008-11-24
I don't know when u got yours but the Intel 5100 AGN was an option .So more $$$ . It look like 5300 AGN is now the option ;-)

---

### Post by Full_Auto_Legos on 2008-11-28
RCMN,
Thanks a ton.  The only possible thing missing in your post (for newbies and people who installed madwifi with high hopes) is the critical blacklisting of those old drivers in /etc/modprobe.d/blacklist (b43, ssb, ath_hal,ath_pci,etc) which are described in Section 3 Configuration here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Xubuntu newbies should use at the terminal prompt$ "sudo thunar" in order to edit the blacklist file in the modprobe.d directory.

I use lenovo w500 4058CTO with atheros card with xubuntu/ubuntu 8.10.  Everything works perfectly now. :)

---

### Post by rcmn on 2008-11-28
> **Full_Auto_Legos said:**
> RCMN,
Thanks a ton.  The only possible thing missing in your post (for newbies and people who installed madwifi with high hopes) is the critical blacklisting of those old drivers in /etc/modprobe.d/blacklist (b43, ssb, ath_hal,ath_pci,etc) which are described in Section 3 Configuration here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Xubuntu newbies should use at the terminal prompt$ "sudo thunar" in order to edit the blacklist file in the modprobe.d directory.

I use lenovo w500 4058CTO with atheros card with xubuntu/ubuntu 8.10.  Everything works perfectly now. :)

Thank You Full_Auto_Legos,

Just added to the post with the ref.

---

