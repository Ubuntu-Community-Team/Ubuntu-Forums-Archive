---
title: "No wireless on sony vaio vgn fe48e"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by danmif on 2008-09-18
hi, i have a sony vaio vgn fe48e, and im having problems with wireless. i've just instaled the 8.04 version

i did this command modinfo iwl3945 and the result is shown below

ubuntu@ubuntu-laptop:~$ modinfo iwl3945

filename:       /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     8E95C617988943846696F97
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-19-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)

Can anyone help me please:)

Thanks 

Daniel

---

