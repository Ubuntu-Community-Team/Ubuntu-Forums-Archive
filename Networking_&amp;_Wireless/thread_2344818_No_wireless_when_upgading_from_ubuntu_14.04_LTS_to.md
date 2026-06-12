---
title: "No wireless when upgading from ubuntu 14.04 LTS to 16.04 LTS"
date: 2016-11-28
forum: Networking &amp; Wireless
---

### Post by ahmed11ber on 2016-11-28
I have upgraded my OS from ubuntu 14.04 LTS to 16.04 LTS and  my wireless doesn't work it seem desactived, but my ethernet link work fine
Here is the result after i issue the command : sudo lshw

```
   ahmed@ahmed:~$ sudo lshw -c network  
   *-network Desactivated      
        description: Wireless Interface
        product : RT3290 Wireless 802.11n 1T/1R PCIe
        fabriquant: Ralink corp.
        identifiant matériel: 0
        information bus: pci@0000:01:00.0
        nom logique: wlan0
        version: 00
        numéro de série: b8:76:3f:72:92:75
        bits: 32 bits
        horloge: 33MHz
        fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=rt2800pci driverversion=4.4.0-47-generic firmware=0.37 latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
        ressources: irq:16 mémoire:52510000-5251ffff
   *-network
        description: Ethernet interface
        produit: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
        fabriquant: Realtek Semiconductor Co., Ltd.
        identifiant matériel: 0
        information bus: pci@0000:02:00.0
        nom logique: eth0
        version: 05
        numéro de série: 74:46:a0:81:9f:5d
        taille: 10Mbit/s
        capacité: 100Mbit/s
        bits: 64 bits
        horloge: 33MHz
        fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s
        ressources: irq:26 portE/S:3000(taille=256) mémoire:52404000-52404fff mémoire:52400000-52403fff
```

And when I issue the command: ifconfig -a

```
ahmed@ahmed:~$ ifconfig -a
 eth0      Link encap:Ethernet  HWaddr 74:46:a0:81:9f:5d   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 lg file transmission:1000  
           Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
 
 
 lo        Link encap:Boucle locale   
           inet adr:127.0.0.1  Masque:255.0.0.0
           adr inet6: ::1/128 Scope:Hôte
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           Packets reçus:4 erreurs:0 :0 overruns:0 frame:0
```

---

### Post by howefield on 2016-11-28
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by wildmanne39 on 2016-11-28
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

