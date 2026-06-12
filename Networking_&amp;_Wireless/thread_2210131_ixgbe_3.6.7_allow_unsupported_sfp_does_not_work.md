---
title: "ixgbe 3.6.7 allow_unsupported_sfp does not work"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by yoave on 2014-03-09
hi,

I'm running Ubuntu 12.04 with kernel 3.2.0-59-generic.
when trying to load ixgbe 3.6.7-k driver with param allow_unsupported_sfp=1, it does not work.
meaning the driver is loaded, but non-intel SFPs fail:

Mar  4 09:47:36 localhost kernel: [  962.782859] ixgbe 0000:04:00.0: eth-tg9: detected SFP+: 5
Mar  4 09:52:24 localhost kernel: [ 1250.677673] ixgbe 0000:04:00.0: [COLOR=#ff0000]failed to initialize because an unsupported SFP+ module type was detected.[/COLOR]


any ideas?


root@ubuild01:~# uname -r
3.2.0-59-generic


root@ubuild01:~# modinfo ixgbe
filename:       /lib/modules/3.2.0-59-generic/kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
version:        3.6.7-k
license:        GPL
description:    Intel(R) 10 Gigabit PCI Express Network Driver
author:         Intel Corporation, <linux.nics@intel.com>
srcversion:     BB7BF3E3F069BB9966A294D
alias:          pci:v00008086d00001560sv*sd*bc*sc*i*
alias:          pci:v00008086d0000154Asv*sd*bc*sc*i*
alias:          pci:v00008086d00001557sv*sd*bc*sc*i*
alias:          pci:v00008086d0000154Fsv*sd*bc*sc*i*
alias:          pci:v00008086d0000154Dsv*sd*bc*sc*i*
alias:          pci:v00008086d00001528sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F8sv*sd*bc*sc*i*
alias:          pci:v00008086d0000151Csv*sd*bc*sc*i*
alias:          pci:v00008086d00001529sv*sd*bc*sc*i*
alias:          pci:v00008086d0000152Asv*sd*bc*sc*i*
alias:          pci:v00008086d000010F9sv*sd*bc*sc*i*
alias:          pci:v00008086d00001514sv*sd*bc*sc*i*
alias:          pci:v00008086d00001507sv*sd*bc*sc*i*
alias:          pci:v00008086d000010FBsv*sd*bc*sc*i*
alias:          pci:v00008086d00001517sv*sd*bc*sc*i*
alias:          pci:v00008086d000010FCsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F7sv*sd*bc*sc*i*
alias:          pci:v00008086d00001508sv*sd*bc*sc*i*
alias:          pci:v00008086d000010DBsv*sd*bc*sc*i*
alias:          pci:v00008086d000010F4sv*sd*bc*sc*i*
alias:          pci:v00008086d000010E1sv*sd*bc*sc*i*
alias:          pci:v00008086d000010F1sv*sd*bc*sc*i*
alias:          pci:v00008086d000010ECsv*sd*bc*sc*i*
alias:          pci:v00008086d000010DDsv*sd*bc*sc*i*
alias:          pci:v00008086d0000150Bsv*sd*bc*sc*i*
alias:          pci:v00008086d000010C8sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C7sv*sd*bc*sc*i*
alias:          pci:v00008086d000010C6sv*sd*bc*sc*i*
alias:          pci:v00008086d000010B6sv*sd*bc*sc*i*
depends:        mdio,dca
intree:         Y
vermagic:       3.2.0-59-generic SMP mod_unload modversions 
parm:           max_vfs:Maximum number of virtual functions to allocate per physical function (uint)
parm:           allow_unsupported_sfp:Allow unsupported and untested SFP+ modules on 82599-based adapters (uint)

---

