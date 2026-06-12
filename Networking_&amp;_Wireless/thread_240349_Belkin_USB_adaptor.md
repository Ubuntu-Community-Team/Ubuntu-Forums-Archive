---
title: "Belkin USB adaptor"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by CalonDdraig on 2006-08-20
I've just bought two of these adaptors from ebay for £15. I have the one with the Ralink RA2500 chipset shown here: [http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/) 

Are they any good and has anyoen had any sucess getting one going on Ubuntu? I'm a relatively experienced linux guy but I'm a wifi virgin on Linux - sorry for being a bother, but I would be grateful if anyone could share any advice on using one of these adaptors.

Thanks!

Calon

---

### Post by lupine_nickt on 2006-08-20
They are remarkably easy to get going; the only caveat is that they can have problems when under heavy connection load (e.g. p2p clients), and they dislike being unplugged, or indeed turned off.

I've got two separate Ubuntu computers running off of these (well, D-link, but the same chipset). 

You want to download and compile the rt2570 (aka. RT2500USB) CVS drivers - it's remarkably easy, just make sure that build-essential and linux-headers-`uname -r` are installed, then extract the rt2570 archive, cd into the directory it creates, and run 'make'. Once complete, run 'sudo make install', 'depmod -a', 'modprobe rt2570'. You're then set, and can configure it in /etc/network/interfaces (the driver doesn't get on well with wireless config utilities, IME)

Here's a sample config:-

```

auto rausb0
iface rausb0 inet dhcp
        wireless-essid=blah
        wireless-key=blah
        wireless-ap=xx:xx:xx:xx:xx:xx

```

Just modify it as required and append it to your /etc/network/interfaces file, then it'll automagically connect on startup.

xF,

...Nick

---

### Post by lupine_nickt on 2006-08-20
Forgot to say, you'll need to update the driver every time the kernel is updated. So keep the source somewhere safe! :D

xF,

...Nick

---

### Post by CalonDdraig on 2006-08-20
Thanks! That's great, I'll see what I can do then:D 

THanks for the help.
Looks like I've bought the right cards - you hear horror stories!

Calon

---

### Post by CalonDdraig on 2006-08-20
Ohh just as a by the by, and totally unrelated, can you use a passphrase as a key, or do you have to enter a hex key? Could I forget encryption and use ssh tunneling instead of link encryption?

Calon

---

### Post by lupine_nickt on 2006-08-20
WEP is basically worthless, so don't bother with it. WPA is supported by these cards, and is significantly better.

SSH tunneling in this instance would be "ok", but slower. 

xF,

...Nick

---

