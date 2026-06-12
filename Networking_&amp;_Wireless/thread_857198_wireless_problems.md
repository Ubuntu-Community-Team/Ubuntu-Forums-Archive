---
title: "wireless problems"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by giolekva on 2008-07-12
Hi.
I've installed Ubuntu 8.04 on my Sony Vaio VGN-FE21B, everything is ok but wireless network, it cann't detect any wireless networks. 

"lshw -C network" gives this output:
```
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: PRO/100 VE Network Connection
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:0a:08.0
       logical name: eth0
       version: 02
       serial: 00:13:a9:08:54:85
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI firmware=N/A ip=192.168.16.72 latency=64 maxlatency=56 mingnt=8 module=e100 multicast=yes
```

"modinfo iwl3945" gives this output:
```
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
```

and "iwconfig" gives that:
```
lo        no wireless extensions.

eth0      no wireless extensions.
```

How can I "force" my laptop to connect wireless networks :)?

Here is my laptops specification: [http://www.ciao.co.uk/Sony_Vaio_FE21B__6483208#productdetail](http://www.ciao.co.uk/Sony_Vaio_FE21B__6483208#productdetail)

---

### Post by superprash2003 on 2008-07-12
hmm.. your lshw looks cool.. have you done a reboot after installing drivers ( if you did manually install)

---

### Post by giolekva on 2008-07-12
no all drives have been installed automaticaly

---

### Post by giolekva on 2008-07-13
Hmmm is anybody here? :)
All days I'm trying to solve this problem, but without result.
Don't u have any ideas?

---

### Post by saintthomas on 2008-07-29
I too had similar problem with Dell Vostro 1510 laptop. I installed Ubuntu 8.04 (Hardy). It detected my NIC and Wireless. But after some days I lost both networks. It is not functioning. Firstly I thought it may be a hardware issue. :confused:  But now I dont think it is so. If anyone get info, please help me...
:(  :confused:

---

