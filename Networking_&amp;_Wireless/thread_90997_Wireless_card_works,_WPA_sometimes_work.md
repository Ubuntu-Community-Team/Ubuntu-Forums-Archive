---
title: "Wireless card works, WPA sometimes work"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by ubuntufans on 2005-11-16
Hi Guys,

I have netgear Wg311 with atheros chipset, it works out of box, and i install WPA supplicant, how do i call this wpa drivers? -D madwifi or something else?

Thanks

---

### Post by mindwarp on 2005-11-28
[QUOTE=ubuntufans]Hi Guys,

I have netgear Wg311 with atheros chipset, it works out of box, and i install WPA supplicant, how do i call this wpa drivers? -D madwifi or something else?

Thanks[/QUOTE]

Here is a list of drivers since madwifi may not be yours, in parentheses are the chipset names:

```

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3) [default]
	(this can also be used with Linuxant DriverLoader)
  hermes = Agere Systems Inc. driver (Hermes-I/Hermes-II)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  broadcom = Broadcom wl.o driver
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  bsd = BSD 802.11 support (Atheros, etc.)
  ndis = Windows NDIS driver

In most common cases, wpa_supplicant is started with

wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0

```

---

### Post by eMiles on 2005-11-28
[QUOTE=mindwarp]Here is a list of drivers since madwifi may not be yours, in parentheses are the chipset names:

```

drivers:
  hostap = Host AP driver (Intersil Prism2/2.5/3) [default]
	(this can also be used with Linuxant DriverLoader)
  hermes = Agere Systems Inc. driver (Hermes-I/Hermes-II)
  madwifi = MADWIFI 802.11 support (Atheros, etc.)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  wext = Linux wireless extensions (generic)
  ndiswrapper = Linux ndiswrapper
  broadcom = Broadcom wl.o driver
  ipw = Intel ipw2100/2200 driver
  wired = wpa_supplicant wired Ethernet driver
  bsd = BSD 802.11 support (Atheros, etc.)
  ndis = Windows NDIS driver

In most common cases, wpa_supplicant is started with

wpa_supplicant -Bw -c/etc/wpa_supplicant.conf -iwlan0

```[/QUOTE]


thank you but concerning PCI card with RT2500, what can i use??

best regrds

---

### Post by gosh on 2005-11-28
Have you tried ndiswrapper and wpa_supplicant?
You can find more on them at wiki.ubuntu.

---

