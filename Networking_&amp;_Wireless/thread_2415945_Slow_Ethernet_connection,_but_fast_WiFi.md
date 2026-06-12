---
title: "Slow Ethernet connection, but fast WiFi"
date: 2019-04-03
forum: Networking &amp; Wireless
---

### Post by tunoxd on 2019-04-03
Hi,

I have a laptop connected to a switch with a new Cat5e. I have Win10 and Kali installed on it, all fine, But when I switch to Kali, wired connection seems to be VERY SLOW (0.12Mbps, just checked it). Using WiFi it goes to 50Mbps. This is not happening on my Windows, so my wired connection is faster than WiFi (wich is normal)

Does anybody know what can I be doing wrong?

PD.: I'm unable to change my static IP, even changing the interfaces file and restarting the network service.

=========================

Static IP
Same plug

---

### Post by kc1di on 2019-04-04
Go to a terminal and type this command and post the results here:```
lshw -class network
```

---

### Post by SeijiSensei on 2019-04-04
Only use one connection to the router.  Either choose Ethernet or wifi.  Having two connections can cause routing problems.

If it's still slow using just Ethernet, I'd take a look at the physical connections.  Are there severe bends or crimps in the cable?

---

### Post by jeanmarc-louviaux on 2019-04-23
Hi,
I got the same issue since 19.04 using kernel 5.0, it's ok with 4.18 though #-o

> jeanmarc@astrolabe:~$ sudo lshw -class network  *-network                 
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: enp3s0
       version: 16
       numéro de série: e0:d5:5e:a7:59:ec
       taille: 1Gbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=192.168.0.26 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       ressources: irq:16 portE/S:3000(taille=256) mémoire:a3204000-a3204fff mémoire:a3200000-a3203fff

Any tips ?

---

### Post by wildmanne39 on 2019-04-23
Hello and welcome to the forum jeanmarc-louviaux, please start your own thread for support instead of posting in someone elese's that way you can both get the help you need and it does not create confusion for those involved.

Thanks

---

