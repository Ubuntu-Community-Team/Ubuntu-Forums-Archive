---
title: "Dell Latitude D430 Wireless not working on Ubuntu 13.10"
date: 2014-03-06
forum: Networking &amp; Wireless
---

### Post by Darryl_Brown on 2014-03-06
Hello I have a Latitude D430, and a D410 that I converted into a D430 by swapping out the motherboard to a D430. Now both have the Media Dock with DVD-ROM and both have an 80gb SSD, 2gb of ram, and 12cell batteries. The reason I went to the D430 is because the CPU will go 64bit. I got everything cheap and slowly upgraded everything one by one to the max. Now my problem is the wireless ! I'm new to Ubuntu so please...
   My goal is to sell both off, but under Windows 7 Home Premium 32bit they both are BRICKS !!! So to revive them I went to Ubuntu 13.10. Now I downloaded and burned an ISO but need help on the wireless. 
   I used [COLOR=#000000]firmware-b43-installer... no luck[/COLOR]
tried code: [COLOR=#000000][FONT=Ubuntu Mono]lspci -nnk.... no luck also 
   My next move might be to find a wireless card that will work, but from a different laptop, and is covered in the BIOS
[/FONT][/COLOR]

---

### Post by chili555 on 2014-03-06
> lspci -nnk.... no luck also Was there any result? What was it?

---

### Post by Darryl_Brown on 2014-03-20
Well I did get the WiFi to work. I just upgraded the card to an Intel 4965AGN this is supported in the BIOS plus an upgrade from the Dell a/b/g card. Now the WiFi led is blinking from receiving and sending info but at least its working !

---

### Post by chili555 on 2014-03-20
> **Darryl_Brown said:**
> Well I did get the WiFi to work. I just upgraded the card to an Intel 4965AGN this is supported in the BIOS plus an upgrade from the Dell a/b/g card. Now the WiFi led is blinking from receiving and sending info but at least its working !What would you prefer the LED to do? One of the dependencies of the driver is iwlegacy which has an available driver parameter:```
$ modinfo iwlegacy
filename:       /lib/modules/3.11.0-18-generic/kernel/drivers/net/wireless/iwlegacy/iwlegacy.ko
license:        GPL
author:         Copyright(c) 2003-2011 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    iwl-legacy: common functions for 3945 and 4965
srcversion:     BC2DEA74DD4DC4E093C27BE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.11.0-18-generic SMP mod_unload modversions 
[COLOR="#FF0000"]parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking (int)[/COLOR]
parm:           bt_coex_active:enable wifi/bluetooth co-exist (bool)
```Tell us which you prefer and we'll be happy to show you how.

---

