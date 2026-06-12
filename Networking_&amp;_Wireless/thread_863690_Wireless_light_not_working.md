---
title: "Wireless light not working"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by jross61 on 2008-07-18
Hi everyone, 
Ive been using Ubuntu for a few months and the computer,wireless internet, wireless printer are working flawlessly, if possible I would like to set the wireless led to on.
The computer is a Aspire 1640 running through a speed stream modem.
I have included a file which looks like a driver,about halfway down it says the led is set to off, would anyone know  who to turn it on thank you.

james@james-laptop:~$ modinfo ipw2200
filename:       /lib/modules/2.6.24-19-generic/kernel/drivers/net/wireless/ipw2200.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     77381637E34989F787D2947
alias:          pci:v00008086d00004224sv*sd*bc*sc*i*
alias:          pci:v00008086d00004223sv*sd*bc*sc*i*
alias:          pci:v00008086d00004221sv*sd*bc*sc*i*
alias:          pci:v00008086d00004220sv*sd*bc*sc*i*
alias:          pci:v00008086d0000104Fsv*sd*bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002762bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002761bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002754bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002753bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002752bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002751bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002742bc*sc*i*
alias:          pci:v00008086d00001043sv0000103Csd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002741bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002732bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002731bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002722bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002721bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002712bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002711bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002702bc*sc*i*
alias:          pci:v00008086d00001043sv00008086sd00002701bc*sc*i*
depends:        ieee80211
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default on) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 0 off)
 (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)
james@james-laptop:~$

---

### Post by jross61 on 2008-07-18
Hi again, I tried this link and it works. hopefully it may help some one else.
Thank you.

[http://ubuntuforums.org/showpost.php?p=3901309&postcount=10](http://ubuntuforums.org/showpost.php?p=3901309&postcount=10)

---

### Post by Tigin on 2008-07-18
well it did not worked for me QQ :(

---

