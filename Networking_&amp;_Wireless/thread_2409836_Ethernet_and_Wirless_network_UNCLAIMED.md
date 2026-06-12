---
title: "Ethernet and Wirless network UNCLAIMED"
date: 2019-01-07
forum: Networking &amp; Wireless
---

### Post by mrdomoo on 2019-01-07
Hi !
I have a dual boot with ubuntu 16.04 alongside windows 8. A recent update broke my network drivers. I can not have internet acces under linux anymore. Here are few details (some outputs are in french sorry).

A really appreciate your help
Thank you


```
***** iwconfig *****

lo        no wireless extensions.
```


```
***** lshw -C network *****

  *-network NON-RÉCLAMÉ   
       description: Network controller
       produit: AR9485 Wireless Network Adapter
       fabriquant: Qualcomm Atheros
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       version: 01
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: bus_master cap_list
       configuration: latency=0
       ressources: mémoire:f7900000-f797ffff mémoire:f7980000-f798ffff
  *-network NON-RÉCLAMÉ
       description: Ethernet controller
       produit: AR8161 Gigabit Ethernet
       fabriquant: Qualcomm Atheros
       identifiant matériel: 0
       information bus: pci@0000:04:00.0
       version: 10
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: bus_master cap_list
       configuration: latency=0
       ressources: mémoire:f7800000-f783ffff portE/S:d000(taille=128)
```


```
***** lspci *****

00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GK107M [GeForce GT 740M] (rev a1)
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros AR8161 Gigabit Ethernet (rev 10)
```



```
***** uname -a *****

Linux lucas-N76VB 4.15.0-36-generic #39~16.04.1-Ubuntu SMP Tue Sep 25 08:59:23 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux
```


```
***** sudo modprobe -v ath9k *****

modprobe: FATAL: Module ath9k not found in directory /lib/modules/4.15.0-36-generic
```


**I've downloaded the generic package and tried to install it but (answer in french)**

```
***** sudo dpkg -i block-modules-4.15.0-36-generic-di_4.15.0-36.39_amd64.udeb *****

(Lecture de la base de données... 296005 fichiers et répertoires déjà installés.)
Préparation du dépaquetage de block-modules-4.15.0-36-generic-di_4.15.0-36.39_amd64.udeb ...
Dépaquetage de block-modules-4.15.0-36-generic-di (4.15.0-36.39) ...
dpkg: erreur de traitement de l'archive block-modules-4.15.0-36-generic-di_4.15.0-36.39_amd64.udeb (--install) :
 tentative de remplacement de « /lib/modules/4.15.0-36-generic/kernel/drivers/block/nbd.ko », qui appartient aussi au paquet linux-modules-4.15.0-36-generic 4.15.0-36.39~16.04.1
dpkg-deb : erreur : le sous-processus coller a été tué par le signal (Relais brisé (pipe))
Des erreurs ont été rencontrées pendant l'exécution :
 block-modules-4.15.0-36-generic-di_4.15.0-36.39_amd64.udeb
```

---

### Post by howefield on 2019-01-07
Thread moved to the "*Networking & Wireless*" forum.

---

