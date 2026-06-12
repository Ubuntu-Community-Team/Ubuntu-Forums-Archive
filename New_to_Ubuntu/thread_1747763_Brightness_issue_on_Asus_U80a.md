---
title: "Brightness issue on Asus U80a"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Image0fman on 2011-05-03
Hi All, 

When I use the brightness hotkey on my Asus u80a (Fn+f5/f6) it displays the brightness indicator applet but dosent actually do anything.. or it does but its completely laggin.. then the indicator notification just keeps popping up every 2mins.. When I try to click on the +/- in the indicator applet it just disappears as soon as I click it.. here is modinfo on my video module (not sure if this is the right one):

filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/acpi/video.ko
license:        GPL
description:    ACPI Video Driver
author:         Bruno Ducrot
srcversion:     4482B1F3B85716D9D0AF5BE
alias:          acpi*:LNXVIDEO:*
depends:        output
vermagic:       2.6.35-28-generic SMP mod_unload modversions 
parm:           brightness_switch_enabled:bool
parm:           allow_duplicates:bool

---

