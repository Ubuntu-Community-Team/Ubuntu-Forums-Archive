---
title: "There's any usb adapter I can use with Ubuntu"
date: 2006-08-21
forum: Networking &amp; Wireless
---

### Post by Arijua on 2006-08-21
Hi there;

I try to work on a wireless connection on ubuntu, but there is a usb adapter that I can buy and connect with no promblems ?

I have a Belking g router

a Desktop and a laptop 

Need help with that

Please:

---

### Post by encompass on 2006-08-21
Actually, I went a got a wireless bridge and it was one of the greatest things I ever got...
it uses your ethernet connection to a wireless controller and gives great signal and works in anything with a hub... even things like the XBox and VOIP phones.
[http://www.usr.com/products/networking/wireless-product.asp?sku=USR5432](http://www.usr.com/products/networking/wireless-product.asp?sku=USR5432)
This is almsot the same thing I had... but mine was older and simpler.
It will work... No drivers needed... Just your webbrowser.

---

### Post by lupine_nickt on 2006-08-21
Hi,

Although a wireless bridge is great for zero-configuration, they're not exactly portable... ;)

There's a pretty comprehensive list of wireless usb adapters [here](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported#head-603c9481d6c6288b6b674cc50132d21f6d539c53)

In particular, any adapters which are based on Atheros or Atmel chipsets seem to be remarkably easy to set up; thos based on rt2500(usb)/rt2570 are fairly easy, but slightly unstable at the moment; broadcom is a mixed bag.

Your best bet is to print out the list and highlight any which are described as being easy to set up/supported, then check which ones you can actually get hold of. You can then check around the forum for other people's issues with cards using that particular chipset, and get a feel for the difficulties that people have encountered, and what %age have had serious problems, etc.

xF,

...Nick

---

### Post by encompass on 2006-08-21
ok ok you got me on portability... but for that desktop it would work great... and most get fantastic reseption!

---

### Post by tombs on 2006-08-21
Actually you can check those lists:
[http://tuxmobil.org/pcmcia_linux.html]("http://tuxmobil.org/pcmcia_linux.html")
[http://www.linux-wlan.org/docs/wlan_adapters.html.gz]("http://www.linux-wlan.org/docs/wlan_adapters.html.gz")

---

### Post by lupine_nickt on 2006-08-21
...assuming that the USB stick has a decent antenna (and most of them do, even if it doesn't look like it), there's no reason to suggest that a wireless bridge would give a better signal. If you rip open your wireless bridge, I'm certain it's gotr a miniPCI or PCMCIA card inside it that you can take out and use in your laptop or whatever. Assuming you can find drivers ;)

xF,

...Nick

---

