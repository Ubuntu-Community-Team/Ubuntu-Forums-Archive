---
title: "Atheros AR9485"
date: 2015-01-15
forum: Networking &amp; Wireless
---

### Post by thib3113 on 2015-01-15
Hello, 
I make an update 14.04 to 10.10.

And now, i have sometimes a bug with wifi :
```
(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/27' failed in libnm-glib.
```


i make : sudo lshw -C network :
```
  *-network               
       description: Interface réseau sans fil
       produit: AR9485 Wireless Network Adapter
       fabriquant: Qualcomm Atheros
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: wlan0
       version: 01
       numéro de série: 24:0a:64:56:7d:ef
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.16.0-29-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       ressources: irq:18 mémoire:dc200000-dc27ffff mémoire:dc280000-dc28ffff
  *-network
       description: Ethernet interface
       produit: QCA8171 Gigabit Ethernet
       fabriquant: Qualcomm Atheros
       identifiant matériel: 0
       information bus: pci@0000:04:00.0
       nom logique: eth0
       version: 10
       numéro de série: ac:22:0b:1a:21:ae
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       ressources: irq:46 mémoire:dc100000-dc13ffff portE/S:d000(taille=128)
  *-network
       description: Ethernet interface
       identifiant matériel: 1
       nom logique: usb0
       numéro de série: a2:85:59:fa:de:67
       fonctionnalités: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.72 link=yes multicast=yes



```

I make lspci | grep Qualcomm :```
03:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Qualcomm Atheros QCA8171 Gigabit Ethernet (rev 10)

```

i make  iwconfig :
```
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
usb0      no wireless extensions.


lo        no wireless extensions.

```

and syslog say :
```
Jan 15 12:12:39 thib3113-G750JX NetworkManager[1146]: <info> (usb0): IP6 addrconf timed out or failed.Jan 15 12:12:39 thib3113-G750JX NetworkManager[1146]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Jan 15 12:12:39 thib3113-G750JX NetworkManager[1146]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) started...
Jan 15 12:12:39 thib3113-G750JX NetworkManager[1146]: <info> Activation (usb0) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Jan 15 12:12:39 thib3113-G750JX avahi-daemon[1096]: Withdrawing address record for fe80::e096:6eff:fef4:6fcc on usb0.
Jan 15 12:12:39 thib3113-G750JX avahi-daemon[1096]: Leaving mDNS multicast group on interface usb0.IPv6 with address fe80::e096:6eff:fef4:6fcc.
Jan 15 12:12:39 thib3113-G750JX avahi-daemon[1096]: Interface usb0.IPv6 no longer relevant for mDNS.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) starting connection 'WIFI-YNOV-TOULOUSE 1'
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0/wireless): access point 'WIFI-YNOV-TOULOUSE 1' has security, but secrets are required.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <warn> No agents were available for this request.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> Marking connection 'WIFI-YNOV-TOULOUSE 1' invalid.
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <warn> Activation (wlan0) failed for connection 'WIFI-YNOV-TOULOUSE 1'
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jan 15 12:14:15 thib3113-G750JX NetworkManager[1146]: <info> (wlan0): deactivating device (reason 'none') [0]

```
I have install openvpn and openvpn, but i have remove it and purge

---

