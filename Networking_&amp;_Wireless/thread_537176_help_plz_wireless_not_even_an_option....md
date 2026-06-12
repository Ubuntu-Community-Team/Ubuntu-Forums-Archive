---
title: "help plz wireless not even an option..."
date: 2007-08-28
forum: Networking &amp; Wireless
---

### Post by cevil203 on 2007-08-28
i dont even get the option to use a wireless network connection anymore...i  was albe to yesterday. but now the option to connect to a wireless network isnt there. just wired network or manual connection.. please help. i have a dell e1705 with the intel 3945abg card.

---

### Post by Zorael on 2007-08-28
You mean, there aren't any listed wireless networks to connect to in the network manager applet?

They're only there when the interface is in "roaming mode", I believe. You can reset it to such again if you wish, by entering those manual options, then entering the options for your interface and checking the box. If you're using Kubuntu, you have to enable DHCP, and maybe try to make all available fields blank (so as to reset it to how it was earlier).

Or you could install wicd which seems to do the job better in many cases.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by cevil203 on 2007-08-28
no no i cant even have the option to use my wireless card. i dont get far enough to chose a network, not even far enough to chose the ability to use wireless all together. its not an option in the menu : /   when i go to system---restricted drivers----itsthere and its enabled but it says "not in use"..hope this helps

---

### Post by Zorael on 2007-08-28
Hmm, enabled but not in use?


I'm not knowledgeable enough to know if that means it's loaded and just "not assigned" to any interface, or something else, so bear with me.


If you open a terminal and type 'lshw -C network' (without the quotes, case sensitive), you should get something like this:

```
zorael@azrael:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 12
       serial: 00:a0:d1:a0:ec:6b
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes **[SIZE="4"]driver=sky2[/SIZE]** driverversion=1.13 firmware=N/A latency=0 multicast=yes
       resources: iomemory:cc000000-cc003fff ioport:3000-30ff irq:16
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@07:00.0
       logical name: eth1
       version: 02
       serial: 00:18:de:6e:39:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes **[SIZE="4"]driver=ipw3945[/SIZE]** driverversion=1.2.0mp firmware=14.2 1:0 () ip=192.168.0.13 latency=0 multicast=yes wireless=IEEE 802.11b
       resources: iomemory:ce000000-ce000fff irq:19
```

Now, that's one big wall of text, but what you want to focus on is the driver name for your wireless interface. In my case, it's the lower one (ipw3945).

To see if that driver is loaded type 'lsmod | grep [driver name]'. In my case:
```
zorael@azrael:~$ lsmod | grep ipw3945
ipw3945               118816  1
ieee80211              34760  1 ipw3945
```

If there's no response, it's not loaded. Does it by any chance become "in use" if you type 'sudo modprobe [name of driver]'?
```
zorael@azrael:~$ sudo modprobe ipw3945
```

There's normally nothing printed when modprobing drivers, so don't worry if it's not very verbose.

---

### Post by cevil203 on 2007-08-28
when i did that commadn this is what i get

eric@nemesis:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:dcfff000-dcffffff irq:5
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:3a:d2:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.104 latency=64 multicast=yes
       resources: iomemory:dcbfe000-dcbfffff irq:17

---

### Post by Zorael on 2007-08-28
Hmm. What happens if you do a 'sudo modprobe ipw3945', and then another 'lshw -C network'?

---

### Post by cevil203 on 2007-08-28
eric@nemesis:~$ sudo modprobe ipw3945
Password:
FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)
2007-08-28 18:13:03: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection
eric@nemesis:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: iomemory:dcfff000-dcffffff irq:5
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@03:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:3a:d2:a8
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=1.01 ip=192.168.1.104 latency=64 multicast=yes
       resources: iomemory:dcbfe000-dcbfffff irq:17

---

### Post by Zorael on 2007-08-28
> FATAL: Error inserting ipw3945 (/lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko) : Unknown symbol in module, or unknown parameter (see dmesg)
2007-08-28 18:13:03: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

Hmm. And result of:
```
dmesg | egrep -i "(modprobe|ipw3945)"
```

?

---

### Post by cevil203 on 2007-08-28
eric@nemesis:~$ dmesg | egrep -i "(modprobe|ipw3945)"
[   17.708000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[   17.708000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[   17.708000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[   17.708000] ipw3945: Unknown symbol ieee80211_txb_free
[   17.708000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[   17.708000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[   17.708000] ipw3945: Unknown symbol escape_essid
[   17.708000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[   17.708000] ipw3945: Unknown symbol ieee80211_set_geo
[   17.708000] ipw3945: Unknown symbol ieee80211_rx
[   17.708000] ipw3945: Unknown symbol ieee80211_get_channel
[   17.708000] ipw3945: Unknown symbol ieee80211_channel_to_index
[   17.708000] ipw3945: Unknown symbol ieee80211_rx_mgt
[   17.708000] ipw3945: Unknown symbol ieee80211_get_geo
[   17.708000] ipw3945: Unknown symbol free_ieee80211
[   17.708000] ipw3945: Unknown symbol ieee80211_tx_frame
[   17.708000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[   17.708000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[   17.708000] ipw3945: Unknown symbol alloc_ieee80211
[ 2606.504000] ipw3945: Unknown symbol ieee80211_wx_get_encodeext
[ 2606.504000] ipw3945: Unknown symbol ieee80211_wx_set_encode
[ 2606.504000] ipw3945: Unknown symbol ieee80211_wx_get_encode
[ 2606.504000] ipw3945: Unknown symbol ieee80211_txb_free
[ 2606.504000] ipw3945: Unknown symbol ieee80211_wx_set_encodeext
[ 2606.508000] ipw3945: Unknown symbol ieee80211_wx_get_scan
[ 2606.508000] ipw3945: Unknown symbol escape_essid
[ 2606.508000] ipw3945: Unknown symbol ieee80211_freq_to_channel
[ 2606.508000] ipw3945: Unknown symbol ieee80211_set_geo
[ 2606.508000] ipw3945: Unknown symbol ieee80211_rx
[ 2606.508000] ipw3945: Unknown symbol ieee80211_get_channel
[ 2606.508000] ipw3945: Unknown symbol ieee80211_channel_to_index
[ 2606.508000] ipw3945: Unknown symbol ieee80211_rx_mgt
[ 2606.508000] ipw3945: Unknown symbol ieee80211_get_geo
[ 2606.508000] ipw3945: Unknown symbol free_ieee80211
[ 2606.508000] ipw3945: Unknown symbol ieee80211_tx_frame
[ 2606.508000] ipw3945: Unknown symbol ieee80211_is_valid_channel
[ 2606.508000] ipw3945: Unknown symbol ieee80211_get_channel_flags
[ 2606.508000] ipw3945: Unknown symbol alloc_ieee80211

---

### Post by Zorael on 2007-08-28
Okay.

What about...
```
lsmod | grep ieee80211
```

?

---

### Post by cevil203 on 2007-08-28
nothing happens

---

### Post by Zorael on 2007-08-28
EDIT: You may want to try 'sudo modprobe ieee80211' first, and if it says 'FATAL: Module ieee80211 not found.', proceed with the following:


Okay, you don't have the ieee80211 networking stack installed, for some obscure reason. :)

Head to [http://ieee80211.sourceforge.net/](http://ieee80211.sourceforge.net/)

Scroll down until you get to the downloads, and try - say - the most recent one (ieee80211-1.2.18.tgz). Once you've untarred it read the file named INSTALL for instructions, should hopefully be pretty straight-forward.

(I've never done it myself, should do the trick, but perhaps you need to compile the kernel again afterwards. I've no idea.)

---

### Post by cevil203 on 2007-08-28
ah well in that case i  got to figure out how to untar..ill go try to figure this out

---

### Post by cevil203 on 2007-08-28
ahah i found a .deb installer YAY lets see where this goes

---

### Post by Zorael on 2007-08-28
Try
```
tar zxvf ieee80211-1.2.18.tgz
```

Or open it with an archiving manager; Ark, KArchiver, XArchiver, Archive Manager, etc.


edit: oh, okay, even better. :>

---

### Post by cevil203 on 2007-08-28
hmm i dont think it did anything after it installed. any ideas?

---

### Post by cevil203 on 2007-08-28
sudo modprobe ieee80211 results in that fatal still? wtf lol

---

### Post by cevil203 on 2007-08-28
i think the kill switch is turned on..but i cant figure out how to change it.. fn+f2 isnt working anymore

---

### Post by spd106 on 2007-08-28
I think it might be wise to check that you don't have the files around.

Try these commands
```
modinfo ieee80211
modinfo ipw3945
```
or
```
sudo updatedb
locate ieee80211
```

It might also be worth refreshing the module dependencies then try reloading ipw3945 again.
```
sudo depmod
```

Also check that the linux-restricted-modules package is installed

---

### Post by Zorael on 2007-08-28
edit: Whew, now with someone else here who knows what he's doing (unlike me who fake my way around), I can relax. :)

---

### Post by cevil203 on 2007-08-28
to your first advice output

eric@nemesis:~$ modinfo ieee80211
modinfo: could not find module ieee80211
eric@nemesis:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)

---

### Post by cevil203 on 2007-08-28
sudo depmod doesnt seem to do anything

eric@nemesis:~$ locate ieee80211
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.20-15-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/lib/modules/2.6.20-15-generic/kernel/ubuntu/net/rtl_ieee80211
/lib/modules/2.6.20-15-generic/kernel/ubuntu/net/rtl_ieee80211/ieee80211-rtl.ko
/usr/src/linux-headers-2.6.20-16/net/ieee80211
/usr/src/linux-headers-2.6.20-16/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-16/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211/Makefile
/usr/src/linux-headers-2.6.20-16/ubuntu/include/net/rtl_ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-16/ubuntu/include/net/rtl_ieee80211.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.20-15/net/ieee80211
/usr/src/linux-headers-2.6.20-15/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-15/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211/Makefile
/usr/src/linux-headers-2.6.20-15/ubuntu/include/linux/ieee80211.h
/usr/src/linux-headers-2.6.20-15/ubuntu/include/net/rtl_ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-15/ubuntu/include/net/rtl_ieee80211.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211_crypt.h
/usr/src/ieee80211-1.2.15
/usr/src/ieee80211-1.2.15/.ieee80211_geo.o.cmd
/usr/src/ieee80211-1.2.15/ieee80211_tx.o.lst
/usr/src/ieee80211-1.2.15/ieee80211_tx.o
/usr/src/ieee80211-1.2.15/ieee80211_crypt_tkip.c
/usr/src/ieee80211-1.2.15/ieee80211_rx.c
/usr/src/ieee80211-1.2.15/ieee80211_rx.o
/usr/src/ieee80211-1.2.15/GIT_SHA1
/usr/src/ieee80211-1.2.15/ieee80211_wx.c
/usr/src/ieee80211-1.2.15/.ieee80211_crypt_wep.o.d
/usr/src/ieee80211-1.2.15/ieee80211_wx.o.lst
/usr/src/ieee80211-1.2.15/.ieee80211_tx.o.cmd
/usr/src/ieee80211-1.2.15/ieee80211_crypt_wep.o.lst
/usr/src/ieee80211-1.2.15/.ieee80211_module.o.cmd
/usr/src/ieee80211-1.2.15/ieee80211_crypt.o
/usr/src/ieee80211-1.2.15/ieee80211_crypt_wep.c
/usr/src/ieee80211-1.2.15/ieee80211_crypt.o.lst
/usr/src/ieee80211-1.2.15/ieee80211_module.o
/usr/src/ieee80211-1.2.15/.ieee80211_rx.o.cmd
/usr/src/ieee80211-1.2.15/.ieee80211_crypt.o.cmd
/usr/src/ieee80211-1.2.15/.ieee80211_wx.o.cmd
/usr/src/ieee80211-1.2.15/ieee80211_tx.c
/usr/src/ieee80211-1.2.15/ieee80211.o
/usr/src/ieee80211-1.2.15/net
/usr/src/ieee80211-1.2.15/net/ieee80211.h
/usr/src/ieee80211-1.2.15/net/ieee80211_radiotap.h
/usr/src/ieee80211-1.2.15/net/ieee80211_crypt.h
/usr/src/ieee80211-1.2.15/remove-old
/usr/src/ieee80211-1.2.15/ieee80211_crypt_ccmp.c
/usr/src/ieee80211-1.2.15/INSTALL
/usr/src/ieee80211-1.2.15/ieee80211_module.o.lst
/usr/src/ieee80211-1.2.15/idvals
/usr/src/ieee80211-1.2.15/CHANGES
/usr/src/ieee80211-1.2.15/ieee80211_geo.o.lst
/usr/src/ieee80211-1.2.15/ieee80211_geo.o
/usr/src/ieee80211-1.2.15/ieee80211_wx.o
/usr/src/ieee80211-1.2.15/.tmp_versions
/usr/src/ieee80211-1.2.15/.tmp_versions/ieee80211_crypt.mod
/usr/src/ieee80211-1.2.15/.tmp_versions/ieee80211.mod
/usr/src/ieee80211-1.2.15/in-tree
/usr/src/ieee80211-1.2.15/in-tree/Kconfig
/usr/src/ieee80211-1.2.15/in-tree/Makefile
/usr/src/ieee80211-1.2.15/LICENSE
/usr/src/ieee80211-1.2.15/.ieee80211.o.cmd
/usr/src/ieee80211-1.2.15/Makefile
/usr/src/ieee80211-1.2.15/compat.h
/usr/src/ieee80211-1.2.15/ieee80211_rx.o.lst
/usr/src/ieee80211-1.2.15/ieee80211_crypt.c
/usr/src/ieee80211-1.2.15/ieee80211_module.c
/usr/src/ieee80211-1.2.15/ieee80211_geo.c
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/wep.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/rtl/ieee80211.h
/usr/src/ieee80211-1.2.15.tgz
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/wep.h
eric@nemesis:~$ modinfo ieee80211
modinfo: could not find module ieee80211
eric@nemesis:~$ modinfo ipw3945
filename:       /lib/modules/2.6.20-16-generic/kernel/ubuntu/wireless/ipw3945/ipw3945.ko
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.0mp
description:    Intel(R) PRO/Wireless 3945 Network Connection driver for Linux
srcversion:     9B03103B15A8FE1824967C2
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        ieee80211
vermagic:       2.6.20-16-generic SMP mod_unload 586 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default 0 off) (int)
parm:           auto_create:auto create adhoc network (default 1 on) (int)
parm:           led:enable led control (default 1 on)
 (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
eric@nemesis:~$ 
eric@nemesis:~$ sudo depmod
eric@nemesis:~$ 


the restricted package is installed.  : /

---

### Post by Zorael on 2007-08-28
Way out of my league I'm afraid, hopefully someone out there knows what needs to be done though.

I offer this for comparison though; my output of a healthy locate ieee80211:
```
zorael@azrael:/usr/src$ locate ieee80211
/var/cache/modass/ieee80211-source.avail_version
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211
/lib/modules/2.6.20-16-generic/kernel/ubuntu/net/rtl_ieee80211/ieee80211-rtl.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_tkip.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_ccmp.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/ieee80211_crypt_wep.ko
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac
/lib/modules/2.6.20-16-generic/kernel/net/ieee80211/softmac/ieee80211softmac.ko
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-15/ubuntu/net/rtl_ieee80211/Makefile
/usr/src/linux-headers-2.6.20-15/ubuntu/include/net/rtl_ieee80211.h
/usr/src/linux-headers-2.6.20-15/ubuntu/include/net/rtl_ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-15/ubuntu/include/linux/ieee80211.h
/usr/src/linux-headers-2.6.20-15/net/ieee80211
/usr/src/linux-headers-2.6.20-15/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-15/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.20-15/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.20-15/include/net/ieee80211.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/wep.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/rtl/ieee80211.h
/usr/src/linux-headers-2.6.20-16-generic/include/config/ieee80211.h
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-16/ubuntu/net/rtl_ieee80211/Makefile
/usr/src/linux-headers-2.6.20-16/ubuntu/include/net/rtl_ieee80211.h
/usr/src/linux-headers-2.6.20-16/ubuntu/include/net/rtl_ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-16/ubuntu/include/linux/ieee80211.h
/usr/src/linux-headers-2.6.20-16/net/ieee80211
/usr/src/linux-headers-2.6.20-16/net/ieee80211/Kconfig
/usr/src/linux-headers-2.6.20-16/net/ieee80211/Makefile
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac/Kconfig
/usr/src/linux-headers-2.6.20-16/net/ieee80211/softmac/Makefile
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211_crypt.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211softmac_wx.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211_radiotap.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211softmac.h
/usr/src/linux-headers-2.6.20-16/include/net/ieee80211.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/ccmp.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/wep.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/crypt/tkip.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211/softmac.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/rtl/ieee80211.h
/usr/src/linux-headers-2.6.20-15-generic/include/config/ieee80211.h
```

---

### Post by cevil203 on 2007-08-28
i would really just love my wireless right now : C

---

### Post by cevil203 on 2007-08-28
man this is sucking bad now. is there anyone out there that will help me?

---

### Post by cevil203 on 2007-08-29
please help

---

### Post by kevdog on 2007-08-29
Clarification, Ive never done this but since it doesnt work for you anyway, try this

```

sudo aptitude install build-essential linux-headers-`uname -r`
cd ~
mkdir ieee80211
wget [http://umn.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz](http://umn.dl.sourceforge.net/sourceforge/ieee80211/ieee80211-1.2.18.tgz) -O ~/ieee80211
cd ieee80211
tar -zxvf ieee80211-1.2.18.tgz
cd  ieee80211-1.2.18
make

```

If it says something about old versions being found, go ahead and remove them
sudo make install

At this point Im not sure if the kernel module will be loaded into the kernel or not.
First
modinfo ieee80211

If nothing is found then
sudo modprobe ieee80211
Then recheck
modinfo ieee80211

Let me know where you are at this point.

---

### Post by spd106 on 2007-08-29
There's something else to try on this thread, [http://ubuntuforums.org/showthread.php?t=518702](http://ubuntuforums.org/showthread.php?t=518702).

I think you should focus on getting the hardware switch to work again as it looks like you have all of the software needed. Especially as it used to work ok.

---

