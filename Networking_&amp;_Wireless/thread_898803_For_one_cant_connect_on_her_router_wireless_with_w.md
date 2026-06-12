---
title: "For one cant connect on her router wireless with wpa"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by burnit on 2008-08-23
I found this bug :

When you try connect on wpa on your router the driver deosnot reconised your card driver to be set them on /etc/network/interfaces file

You need to edit it manualy with root user and change on this line for your one card wireless.
1) On root :
gedit /etc/network/interfaces

change line wpa-driver for you once card wifi like this example :

for me its Atheros then i put in this line : "wpa-driver madwifi"

for other chipset its there name you put :

  wext = Linux wireless extensions (generic)
  hostap = Host AP driver (Intersil Prism2/2.5/3)
  madwifi = MADWIFI 802.11 support (Atheros, etc.) (this one is mine)
  atmel = ATMEL AT76C5XXx (USB, PCMCIA)
  ndiswrapper = Linux ndiswrapper
  ipw = Intel ipw2100/2200 driver (old; use wext with Linux 2.6.13 or newer)
  wired = wpa_supplicant wired Ethernet driver
  test = wpa_supplicant test driver

First time when i config my connection on wpa he doesnot change this one line he stay on wpa-driver wext (for linux generic driver)

And when i edit file and change line for my one driver extension its working now.

I hope this trick help you

---

