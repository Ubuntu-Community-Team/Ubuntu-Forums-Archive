---
title: "Network symbol absent and wireless not working"
date: 2016-02-02
forum: Networking &amp; Wireless
---

### Post by A_K_S_Chand on 2016-02-02
Yesterday before installing r-base, I had used ```
apt-get update
``` and ```
apt-get upgrade
```. After installing r-base, I used ```
apt-get autoremove
``` as there was a message to do that. Some files were removed which I again reinstalled back and the internet (wireless) was working fine. I had not restarted the computer in the middle. Today when I switched the system on, both LAN and wireless are not working. Then I added the lines 
```
auto eth0 iface eth0 inet dhcp
``` to /etc/network/interfaces and when I ran the command ```
sudo ifdown eth0 && sudo ifup -v eth0
```, the LAN started working. 

However, the wireless is still not working. When I open Network in the Settings, there is an error message "The system network services are not compatible with this version."  ```
sudo service network-manager start
``` does not help. When I run ```
modinfo iwl3945 tg3
```, I get the following reply:filename:       /lib/modules/3.13.0-77-generic/kernel/drivers/net/wireless/iwlegacy/iwl3945.ko
firmware:       iwlwifi-3945-2.ucode
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:s
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     63597F7C72B07A97B142DC2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
alias:          pci:v00008086d00004227sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001044bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001034bc*sc*i*
alias:          pci:v00008086d00004222sv*sd00001005bc*sc*i*
depends:        iwlegacy,cfg80211,mac80211
intree:         Y
vermagic:       3.13.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:61:BD:20:E8:AC:66:64:3F:C6:DC:2D:56:66:8F:42:6E:33:E8:8F
sig_hashalgo:   sha512
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using software crypto (default 1 [software]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 1) (int)
parm:           fw_restart:restart firmware in case of error (int)
filename:       /lib/modules/3.13.0-77-generic/kernel/drivers/net/ethernet/broadcom/tg3.ko
firmware:       tigon/tg3_tso5.bin
firmware:       tigon/tg3_tso.bin
firmware:       tigon/tg3.bin
version:        3.134
license:        GPL
description:    Broadcom Tigon3 ethernet driver
author:         David S. Miller (davem@redhat.com) and Jeff Garzik (jgarzik@pobox.com)
srcversion:     B64DF02FCE4704AD2F64C68
alias:          pci:v000010CFd000011A2sv*sd*bc*sc*i*
alias:          pci:v0000106Bd00001645sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EAsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003EBsv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E9sv*sd*bc*sc*i*
alias:          pci:v0000173Bd000003E8sv*sd*bc*sc*i*
alias:          pci:v00001148d00004500sv*sd*bc*sc*i*
alias:          pci:v00001148d00004400sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B3sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B7sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001641sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001683sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001642sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016F3sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001643sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001687sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001686sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001682sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Fsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001657sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B2sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B3sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B4sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B0sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B5sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016B1sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001656sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001665sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001655sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001691sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001694sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001690sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001692sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001692sv00001025sd00000612bc*sc*i*
alias:          pci:v000014E4d00001692sv00001025sd00000601bc*sc*i*
alias:          pci:v000014E4d000016A0sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001699sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001689sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001688sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001680sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001681sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001684sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001698sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001713sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001712sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016DDsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001679sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001678sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001669sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001668sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Fsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001693sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001693sv000017AAsd00003056bc*sc*i*
alias:          pci:v000014E4d0000169Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001674sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001673sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001672sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Asv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FEsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016FDsv*sd*bc*sc*i*
alias:          pci:v000014E4d000016F7sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001601sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001600sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000167Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001677sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001676sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00001659sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000166Esv*sd*bc*sc*i*
alias:          pci:v000014E4d00001649sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000170Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000169Csv*sd*bc*sc*i*
alias:          pci:v000014E4d00001696sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016C6sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A8sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A7sv*sd*bc*sc*i*
alias:          pci:v000014E4d000016A6sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Esv*sd*bc*sc*i*
alias:          pci:v000014E4d0000165Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001654sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001653sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000164Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00001648sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001647sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001646sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001645sv*sd*bc*sc*i*
alias:          pci:v000014E4d00001644sv*sd*bc*sc*i*
depends:        ptp
intree:         Y
vermagic:       3.13.0-77-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        D9:61:BD:20:E8:AC:66:64:3F:C6:DC:2D:56:66:8F:42:6E:33:E8:8F
sig_hashalgo:   sha512
parm:           tg3_debug:Tigon3 bitmapped debugging message enable value (int)

---

### Post by A_K_S_Chand on 2016-02-08
Can somebody help me how to make the wireless work with the above issue? Thanks in advance.

---

