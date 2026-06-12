---
title: "RT2500 Kismet on Hardy"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by e30power on 2008-02-29
Has anyone tried using kismet on Ubuntu Hardy? Kismet used to work with Gutsy, but since the new kernels are using the serialmonkey rt2x00 code in the kernel itself (is this also happening in Ubuntu?), kismet no longer works.  I can set the card into monitor mode by turning off network manager and then iwconfig wlan0 mode monitor, but when I load kismet, I get no networks showing up. Before upgrading to hardy, I could see 15 wireless networks.
Here is the output of lspci | grep - i network:

rob@laptop:~$ sudo lspci | grep -i network
02:00.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

rob@laptop:~$ kismet -v
Launching kismet_server: /usr/local/bin/kismet_server
Kismet 2007.10.R1
Done.


I have tried using hardy repo kismet and also the build from source, both without success.


Here is the output of modinfo rt2500pci:

rob@laptop:~$ modinfo rt2500pci
filename:       /lib/modules/2.6.24-10-generic/kernel/drivers/net/wireless/rt2x00/rt2500pci.ko
license:        GPL
description:    Ralink RT2500 PCI & PCMCIA Wireless LAN driver.
version:        2.0.10
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     DB2BF84365111437CD709C4
alias:          pci:v00001814d00000201sv*sd*bc*sc*i*
depends:        rt2x00pci,rt2x00lib,mac80211,eeprom_93cx6
vermagic:       2.6.24-10-generic SMP mod_unload 586 


Should I report this as a bug?
Thanks
Rob

---

### Post by Cannaregio on 2008-05-03
I have problems with kismet as well.
Worked fine in Gutsy with 2.6.22.14.
Doesn't work in Hardy with the new kernel 2.6.24.17.
So, after the upgrade, I can get kismet working ONLY if I grub from Hardy into the older kernel 2.6.22.14. 

Here the results if I try kismet with the new kernel:

```

sudo kismet
Server options:  none
Client options:  none
Starting server...
Will drop privs to cron (1002) gid 1002
Waiting for server to start before starting UI...
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (intel3945): Enabling monitor mode for ipw3945 source interface eth1 channel 6...
FATAL: Failed to set monitor mode: Device or resource busy.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}
:~$ 

```

Anyone knows of a solution?

And you should definitely file it as a bug.

---

### Post by thenetduck on 2008-05-03
I have the same problem on my computer. It freezes my computer when kismet runs. I think its something to do with the new vm kernel ubuntu is using. I don't want to downgrade my kernel, so for now am just doing without kismet until it gets fixed, but I think if you would downgrade your kernel to the older version it should work. Just a guess... 

The Net Duck

---

