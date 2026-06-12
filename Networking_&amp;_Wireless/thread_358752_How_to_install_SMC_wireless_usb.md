---
title: "How to install SMC wireless usb?"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by Jeviar on 2007-02-11
Hello all!

I've just recently installed 6.06 on my PC. On that PC, I'm using a USB wireless adapter from SMC with the model number SMCWUSB-G.

Been trying the whole night but I don't seem to be able to make any headways. I've read the [WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") but so far, I still don't know what I'm supposed to see.

I did lshw and as far as I can tell, this is what I get for my usb wireless adapter:

```

usb: 0 UNCLAIMED
[INDENT]
description: Generic USB device
product: USB2.0 WLAN
vendor: SMC
physical id: 1
bus info: usb@1:1
version: 48.10
capabilities: usb-2.00
configuration: maxpower=500mA speed=12.0MB/s
[/INDENT]

```

---

### Post by Jeviar on 2007-02-13
Okay. I finally managed to install my driver using ndiswrapper. For users using SMC's SMCWUSB-G, copy + paste the all .inf and .sys files from the cd into a folder. preferably /home/<user>/smcwusb and then after that,

sudo ndiswrapper -i /home/user/smcwusb/<file>.inf

mine worked after i did this step. now i'm going to try and configure wireless access.

---

### Post by [HUN]Levente on 2007-04-19
Hi!

I have the same adapter(SMC WUSB-G), and I managed to install it with ndiswrapper, ifconfig wlan0 shows it perfectly, but I can't connect to any network.
It seems to me, that it does not use its radio, does not find any networks... I can't even set the ESSID, iwconfig always says that ESSID: off/any. The settings are OK, that's sure, because I tried with a König USB WLAN adapter, it sees the networks and can connect, too, and works fine. The SMC adapter is working in Windows.
Do you have any idea how to get it work in Ubuntu? I don't want to buy another one and I'm already tired of Windows, but I need internet :)
Thanks!

---

### Post by funky_D on 2007-11-08
hi everybody,
Jeviar, could you please explain with more detail what did you do to install the SMC wireless pen?
i didn't understand...
Or anybody that could help please do!
Thank you very very much.

Dino
p.s.-by the way, i'm using 7.04.

---

