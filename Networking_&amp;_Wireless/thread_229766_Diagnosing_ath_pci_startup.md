---
title: "Diagnosing ath_pci startup"
date: 2006-08-04
forum: Networking &amp; Wireless
---

### Post by skecherkid on 2006-08-04
I have just installed Ubuntu on my old Dell laptop.  I have two pcmcia cards - one for wired networking (which is working) and one for wireless (which is of course not working).  I have followed the steps in the Wireless troubleshooting Wiki.  I am loading ath_pci - I can see it using modprobe.  Is there a way to see a log file on startup?  I don't think my ath_pci driver is actually binding to my hardware - I get no ath0 in lshw or anywhere.

Wireless card us DWL-650 and I am using WEP however I haven't gotten far enough to actually configure that yet.  

Where should I look next?

---

### Post by tturrisi on 2006-08-05
/var/log/dmesg will show what loads at boot along w/ any errors.

---

### Post by skecherkid on 2006-08-05
Thanks - I went and checked dmesg and pci_ath is loading without any errors.  However below I am pasting what my system shows for lshw -C network and lshw -businfo.

I am not seeing the driver for my wireless pcmcia device and I am not sure the system is seeing it properly - or at least my output from these commands differs substantially from the example on the wireless troubleshooting Wiki.  

Output from lshw:

 sudo lshw -C network
Password:
  *-network
       description: DWL-650 Wireless PC Card RevP
       product: ISL37101P-10
       vendor: D-Link
       physical id: 0
       version: A3
       slot: Socket 1
  *-network
       description: Ethernet interface
       product: Cardbus Ethernet 10/100
       vendor: Xircom
       physical id: 1
       bus info: pci@02:00.0
       logical name: eth0
       version: 03
       serial: 00:10:a4:11:63:d4
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=xircom_tulip_cb driverversion=0.91+LK1.1 duplex=half ip=192.168.1.105 multicast=yes port=MII speed=100MB/s
       resources: ioport:1000-107f iomemory:22000000-220007ff iomemory:22000800-22000fff irq:11


Output from lshw -businfo:
 sudo lshw -businfo
Bus info     Device     Class          Description
==================================================
                        system         Latitude CPx J650GT
                        bus            Latitude CPx J650GT
                        memory         BIOS
cpu@0                   processor      Pentium III (Coppermine)
                        memory         L1 cache
                        memory         L2 cache
                        memory         System Memory
                        memory         DIMM DRAM Synchronous
                        memory         DIMM DRAM Synchronous
pci@00:00.0             bridge         440BX/ZX/DX - 82443BX/ZX/DX Host bridge
pci@00:01.0             bridge         440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
pci@01:00.0             display        Rage Mobility P/M AGP 2x
pci@00:03.0             bridge         PCI1225
pci@00:03.1             bridge         PCI1225
                        network        ISL37101P-10
pci@00:07.0             bridge         82371AB/EB/MB PIIX4 ISA
pci@00:07.1             storage        82371AB/EB/MB PIIX4 IDE
ide@0        ide0       bus            IDE Channel 0
ide@0.0      /dev/hda   disk           FUJITSU MHJ2181AT
ide@0.0,1    /dev/hda1  disk           Linux filesystem partition
ide@0.0,2    /dev/hda2  disk           Extended partition
ide@1        ide1       bus            IDE Channel 1
ide@1.0      /dev/hdc   disk           TOSHIBA DVD-ROM SD-C2302
             /dev/hdc   disk
pci@00:07.2             bus            82371AB/EB/MB PIIX4 USB
usb@1        usb1       bus            UHCI Host Controller
pci@00:07.3             bridge         82371AB/EB/MB PIIX4 ACPI
pci@00:08.0             multimedia     ES1983S Maestro-3i PCI Audio Accelerator
pci@02:00.0  eth0       network        Cardbus Ethernet 10/100
pci@02:00.1             communication  Cardbus Ethernet + 56k Modem
                        power          CGR-B/858



Any thoughts on where to check next?

---

### Post by tturrisi on 2006-08-06
1. restart comp.
2. rt click panel & select "add to panel".
3. add the icon for network monitor" or s/g like that.
4. rt click that icon on panel & select properties.
5. select ath0 from list of interfaces.

---

### Post by skecherkid on 2006-08-06
Did all that - however in my list I only had eth0 and l0 showing.  No ath0.  

Here is the relevant output from
sudo lsmod:

ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  2 ath_pci,ath_rate_sample
ath_hal               148816  2 ath_pci,ath_rate_sample

So ....  should I be looking for a different driver, or is there something else I am missing?

---

### Post by tturrisi on 2006-08-07
The dwl 650 rev P has a Intersil chipset.  You will need the prism drivers, not atheros (madwifi-ath0) drivers.

---

