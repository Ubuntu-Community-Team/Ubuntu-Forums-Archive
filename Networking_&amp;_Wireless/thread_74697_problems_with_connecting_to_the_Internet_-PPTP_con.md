---
title: "problems with connecting to the Internet -PPTP connection"
date: 2005-10-12
forum: Networking &amp; Wireless
---

### Post by zoobooboozoo on 2005-10-12
Hello everyone.
I'm having problems with connecting to the Internet.

The connection's properties:
Modem:  Terayon tj715x
Connects throuhgt USB nad not through LAN.
ISP: Barak 013
Connectin type: Cables - PPTP


I tried a few things, but dudn't succeed.
Mayb anyone tell me how to connect?

thx in advance

---

### Post by mips on 2005-10-12
[QUOTE=zoobooboozoo]Hello everyone.
I'm having problems with connecting to the Internet.

The connection's properties:
Modem:  Terayon tj715x
Connects throuhgt USB nad not through LAN.
ISP: Barak 013
Connectin type: Cables - PPTP


I tried a few things, but dudn't succeed.
Mayb anyone tell me how to connect?

thx in advance[/QUOTE]

Hi,

Did you even try to Google this problem ? Did you go to the Terayon Website ?

If you had read this  [http://www.terayon.com/tools/static_page/view.html?phase=show&id=1074125685&tool_id=100&cat_id=8.12](http://www.terayon.com/tools/static_page/view.html?phase=show&id=1074125685&tool_id=100&cat_id=8.12)

> 
7. Where can I download drivers for Linux?

We don't support Linux so there are no drivers. If you use ethernet as your connection you won't need drivers and it will work. 

then you would have known that there is NO Linux support for USB connectivity. I suppose you can try and struggle to use the USB port and maybe get it working after you pulled all your hair out but why?

You HAVE to use the ethernet port ! And it is much easier/simpler as well !

Just configure the TCP/IP setting on the Ethernet card of the PC for DHCP & Auto DNS and I'm pretty sure it will work.

For future reference your hardware's support page can be found here:
[http://www.terayon.com/tools/static_page/view.html?phase=show&id=1070438557&tool_id=100&cat_id=8.14](http://www.terayon.com/tools/static_page/view.html?phase=show&id=1070438557&tool_id=100&cat_id=8.14)

---

### Post by occy8 on 2005-10-13
[QUOTE=zoobooboozoo]Hello everyone.
I'm having problems with connecting to the Internet.

The connection's properties:
Modem:  Terayon tj715x
Connects throuhgt USB nad not through LAN.
ISP: Barak 013
Connectin type: Cables - PPTP


I tried a few things, but dudn't succeed.
Mayb anyone tell me how to connect?

thx in advance[/QUOTE]

try this
[http://www.freewebs.com/linuxnet/CableUSBLinuxEn.html](http://www.freewebs.com/linuxnet/CableUSBLinuxEn.html)

---

### Post by mips on 2005-10-13
[QUOTE=occy8]try this
[http://www.freewebs.com/linuxnet/CableUSBLinuxEn.html](http://www.freewebs.com/linuxnet/CableUSBLinuxEn.html)[/QUOTE]

Point 6 in the above guide recommends using the Ethernet port.... ;) 

I simply cannot understand why anyone would want to go through the hassle of setting up devices using the USB port, same problem with modem users. Use devices with standard Ethernet, Serial ports for your communication needs.

---

### Post by occy8 on 2005-10-13
[QUOTE=mips]Point 6 in the above guide recommends using the Ethernet port.... ;) 

I simply cannot understand why anyone would want to go through the hassle of setting up devices using the USB port, same problem with modem users. Use devices with standard Ethernet, Serial ports for your communication needs.[/QUOTE]

I saw that but it should work using USB. I wouldn't go through all that hassle either, but for some it's fun to work that out or it's the lack of money for a new modem.

---

### Post by mips on 2005-10-13
[QUOTE=occy8]I saw that but it should work using USB. I wouldn't go through all that hassle either, but for some it's fun to work that out or it's the lack of money for a new modem.[/QUOTE]

If you want a challenge then go for it but even the manufacturer says the Ethernet is faster & more stable.

This particular cable modem **[COLOR="Red"]has BOTH Ethernet & USB ports[/COLOR]**. No need to buy something new. Maybe a LAN cable and Ethernet NIC for the PC but it is so cheap it is a no brainer ;)

---

