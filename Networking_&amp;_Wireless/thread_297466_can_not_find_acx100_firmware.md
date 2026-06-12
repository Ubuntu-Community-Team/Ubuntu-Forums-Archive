---
title: "can not find acx100 firmware"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by G|N| on 2006-11-11
I followed this: [https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111](https://help.ubuntu.com/community/WifiDocs/Driver/acx111?action=show&redirect=WifiDocs%2FDevice%2FAcx111) guide to install my d-link 520+.
The module installed fine and i found the newest firmware image, copied it to  /lib/firmware/`uname -r`/acx/1.9.8.b/tiacx100 and loaded the module. this is the error that i get:
[17183949.748000] acx: found ACX100-based wireless network card at 0000:00:08.0, irq:193, phymem1:0xDFFFE000, phymem2:0xDFFE0000, mem1:0xe0980000, mem1_size:4096, mem2:0xe09a0000, mem2_size:65536
[17183949.748000] initial debug setting is 0x000A
[17183949.748000] using IRQ 193
[17183949.748000] requesting firmware image 'tiacx100c0D'
[17183949.752000] acx: firmware image 'tiacx100c0D' was not provided. Check your hotplug scripts
[17183949.752000] requesting firmware image 'tiacx100'
[17183949.760000] acx: firmware image 'tiacx100' was not provided. Check your hotplug scripts
[17183949.760000] acx: reset_dev() FAILED
[17183949.760000] ACPI: PCI interrupt for device 0000:00:08.0 disabled
[17183949.776000] acx_pci: probe of 0000:00:08.0 failed with error -5
[17183949.776000] USB module v0.3.35 initialized, probing for devices...
[17183949.776000] usbcore: registered new driver acx_usb

where is the firmware directory in edgy?

---

### Post by FrodoB on 2006-11-12
Ok, someone has solved this one I think. See this post on a different card using the same chipset from what I can tell:

[http://www.ubuntuforums.org/showthread.php?t=296507](http://www.ubuntuforums.org/showthread.php?t=296507)

He explains how to get a firmware loaded.

Looks promising, there are a lot of firmwares already in Edgy. Look in:

/lib/firmware/2.6.17-10-generic/acx

to see them all and there is are readme.txt file.

---

### Post by G|N| on 2006-11-15
[I]Then, I opened up sudo gedit /etc/modprobe.d/options and added the following 2 lines:

#Ensure a working version of the acx111 firmware is used.
options acx firmware_ver=1.2.1.34[/I]

acx100 requires version 1.9.8.b.

but when i add the option i get the following error: acx: Unknown parameter `firmware_ver'

and modinfo acx show that firmware_ver is not an argument for the acx module.
filename:       /lib/modules/2.6.17-10-386/extra/acx.ko
license:        Dual MPL/GPL
author:         ACX100 Open Source Driver development team
description:    Driver for TI ACX1xx based wireless cards (CardBus/PCI/USB)
vermagic:       2.6.17-10-386 mod_unload 486 REGPARM gcc-4.1
depends:        usbcore
alias:          usb:v2001p3B00d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3B01d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v07B8pB21Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v057Cp5601d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0CDEp0017d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v0451p60C5d*dc*dsc*dp*ic*isc*ip*
alias:          pci:v0000104Cd00008400sv*sd*bc*sc*i*
alias:          pci:v0000104Cd00008401sv*sd*bc*sc*i*
alias:          pci:v0000104Cd00009066sv*sd*bc*sc*i*
srcversion:     0A4920423D4BEF202F6087C
parm:           debug:Debug level mask (see L_xxx constants) (uint)

---

### Post by FrodoB on 2006-11-15
What version of Ubuntu are you using? I know that the acx111 for instance is fully supported in 6.10 Edgy Eft. 

The firmware was already there. I can see it in Dapper and Edgy. Perhaps a clean install and then just insert the card and do a:


$ iwconfig

It may just show it.

---

