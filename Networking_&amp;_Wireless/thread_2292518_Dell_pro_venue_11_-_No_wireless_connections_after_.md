---
title: "Dell pro venue 11 - No wireless connections after sleep"
date: 2015-08-28
forum: Networking &amp; Wireless
---

### Post by stef-baly on 2015-08-28
I try for a long time to set-up the wifi for my dell pro venue 11 (wifi chipset Intel Corporation Wireless 7260).
The wifi connection is perfect until the computer is suspend. After a suspend, even activating the wifi from network manager is impossible (picture).

Recently 15.04 has been update to 4.2 RC8. Nothing new !

A file unload_modules has been created.
/etc/pm/config.d with SUSPEND_MODULES="$SUSPEND_MODULES iwlwifi" without any effect.

sudo service network-manager restart doesn't work too !

Is there a command to force the wifi card ?

Thanks U

Stef

---

### Post by Hadaka on 2015-08-28
Hi open a terminal ctl/alt/t then copy and paste

```
echo SUSPEND_MODULES="iwlwifi" | sudo tee -a /etc/pm/config.d/config
```
```
sudo iw reg set FR
sudo sed -i 's/^REG.*=$/&FR/' /etc/default/crda
```

BOOT

---

### Post by stef-baly on 2015-08-29
thanks U but no effect !...

---

### Post by Hadaka on 2015-08-29
give this a try.. from here
[http://askubuntu.com/questions/614164/no-wifi-on-a-system76-laptop-after-upgrade-to-15-04/614584#614584](http://askubuntu.com/questions/614164/no-wifi-on-a-system76-laptop-after-upgrade-to-15-04/614584#614584)

Please COPY and paste to avoid typos.
```
sudo mv /lib/firmware/iwlwifi-3160-12.ucode /lib/firmware/backup-iwlwifi-3160-12.ucode
sudo mv /lib/firmware/iwlwifi-3160-10.ucode /lib/firmware/backup-iwlwifi-3160-10.ucode
```

*If it didnt work..restore to original code with..
```
sudo mv /lib/firmware/backup-iwlwifi-3160-12.ucode /lib/firmware/iwlwifi-3160-12.ucode
sudo mv /lib/firmware/backup-iwlwifi-3160-10.ucode /lib/firmware/iwlwifi-3160-10.ucode
```
thanks.

---

### Post by stef-baly on 2015-09-01
Still doesn't work !
After suspend even an exit doesn't reconnect to the wifi connection. It seems that the wifi chipset is off and it's impossible to wake up.
I must reboot.

Thanks

---

### Post by stef-baly on 2015-09-01
Before suspend

@utopie:~$ sudo lshw -C network
  *-network               
       description: Interface réseau sans fil
       produit: Wireless 7260
       fabriquant: Intel Corporation
       identifiant matériel: 0
       information bus: pci@0000:01:00.0
       nom logique: wlan0
       version: 83
       numéro de série: 5c:51:4f:d9:2e:75
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.2.0-040200rc8-generic firmware=25.30.13.0 ip=192.168.0.50 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       ressources: irq:49 mémoire:f7d00000-f7d01fff
  *-network DÉSACTIVÉ
       description: Ethernet interface
       identifiant matériel: 1
       nom logique: wwan0
       numéro de série: 1e:51:e0:b8:e1:da
       fonctionnalités: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes

After suspend (no more wifi chipset !).
@utopie:~$ sudo lshw -C network
  *-network DÉSACTIVÉ     
       description: Ethernet interface
       identifiant matériel: 1
       nom logique: wwan0
       numéro de série: 1e:51:e0:b8:e1:da
       fonctionnalités: ethernet physical
       configuration: broadcast=yes driver=cdc_mbim driverversion=22-Aug-2005 firmware=CDC MBIM link=no multicast=yes
baly@utopie:~$ ^C

---

