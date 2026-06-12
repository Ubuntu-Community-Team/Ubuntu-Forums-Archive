---
title: "Wireless keeps losing connectivity with realtek 8185 card"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by diobrando on 2008-08-08
Hopefully someone can help me out with this. This wireless card has been nothing but trouble. I'm using the native linux driver for it and I'm able to connect and everything seems to work fine, but after about 3-5 minutes I lose connectivity.

If I run dhclient again I will be able to browse the web again but after a few more minutes I have to repeat the process.

I tried ndiswrapper with both the windows 98 and xp driver for the card but neither worked. In that case I couldn't connect to the access point at all, much less get an IP from DHCP.

> [  376.565112] Linux kernel driver for RTL8180 / RTL8185 based WLAN cards
[  376.565116] Copyright (c) 2004-2005, Andrea Merello
[  376.565117] rtl8180: Initializing module
[  376.565118] rtl8180: Wireless extensions version 22
[  376.565119] rtl8180: Initializing proc filesystem
[  376.565165] rtl8180: Configuring chip resources
[  376.565183] ACPI: PCI Interrupt 0000:06:07.0[A] -> Link [APC2] -> GSI 17 (level, low) -> IRQ 22
[  376.565230] rtl8180: Memory mapped space @ 0xfdfff000 
[  376.565240] rtl8180: MAC controller is a RTL8185 b/g (V. D)
[  376.565242] rtl8180: This is a CARDBUS NIC
[  376.565245] rtl8180: Reported EEPROM chip is a 93c56 (2Kbit)
[  376.582464] rtl8180: Card MAC address is 00:40:f4:f8:64:85
[  376.621811] rtl8180: EEPROM version 105
[  376.626731] rtl8180: Card reports RF frontend Realtek 8225
[  376.626733] rtl8180: WW:This driver has EXPERIMENTAL support for this chipset.
[  376.626735] rtl8180: WW:use it with care and at your own risk and
[  376.626737] rtl8180: WW:**PLEASE** REPORT SUCCESS/INSUCCESS TO Realtek
[  376.731820] rtl8180: This seems a new V2 radio
[  376.731823] rtl8180: Energy threshold: b
[  376.731824] rtl8180: PAPE from CONFIG2: 6
[  376.731896] rtl8180: IRQ 22
[  376.732400] rtl8180: Driver probe completed
[  376.732402] 
[  376.734060] rtl8180: Bringing up iface
[  376.941918] rtl8180: Card successfully reset
[  381.353228] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  415.337813] Linking with XGA
[  415.345210] rtl8180: Setting SW wep key
[  415.371759] Associated successfully
[  415.371763] Using B rates
[  415.438130] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  415.689216] wlan0: duplicate address detected!


relevant part of dmesg included in case that helps.

thanks in advance for any help.

---

### Post by okey666 on 2008-08-08
I used to have the same trouble (I think) as you. Are you using network manager and the madwifi drivers?

edit:sorry, you are not are you (I read above)

---

### Post by diobrando on 2008-08-08
Yeah, not using madwifi. As far as I know it's only for Atheros chipsets? If not it might be worth a try.

---

### Post by okey666 on 2008-08-10
sorry, got my chipsets mixed up.

---

