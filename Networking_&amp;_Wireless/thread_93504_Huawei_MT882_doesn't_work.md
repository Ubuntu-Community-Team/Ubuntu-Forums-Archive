---
title: "Huawei MT882 doesn't work"
date: 2005-11-22
forum: Networking &amp; Wireless
---

### Post by cutOff on 2005-11-22
Hi all, 
has anyone managed to make work the Huawei MT882 Router via USB? When I run 'ifconfig', it doesn't seem to detect any network interface. Do I need install any driver?

Thanks in advance.

---

### Post by kosmic on 2005-11-22
Sorry but are you sure ? a router by USB ??

---

### Post by cutOff on 2005-11-22
[QUOTE=kosmic]Sorry but are you sure ? a router by USB ??[/QUOTE]
Yes, sure. It is a modem/router, with both ethernet/usb ports.

[http://www.adslzone.net/tutorial-46.1.html]("http://www.adslzone.net/tutorial-46.1.html")

Thanks for reply.

---

### Post by mips on 2005-11-22
cutOff,

Just a little tip, do NOT use the USB port, use the ethernet port instead. Setting  it up via Ethernet is much easier than going the usb route and trying to get drivers & PPPoE to work on the PC.

Were you using the USB port before ?

If yes then enter the routers config via a web browser. take it out of bridged mode and into 'routed' mode. You will have to have certain infos at hand to this. VPI, VCI, Encapsulation (PPPoE, PPPoA etc), username, password. Configure it for DHCP on the LAN site to automatically assign you PC and IP address.

It's not hard to do. If you get stuck post all the above infos here (except username & password or #### the critical bits out) + the country you live in, ISP and service used. A web link would help.

---

### Post by cutOff on 2005-11-22
[QUOTE=mips]cutOff,

Just a little tip, do NOT use the USB port, use the ethernet port instead. Setting  it up via Ethernet is much easier than going the usb route and trying to get drivers & PPPoE to work on the PC.

Were you using the USB port before ?

If yes then enter the routers config via a web browser. take it out of bridged mode and into 'routed' mode. You will have to have certain infos at hand to this. VPI, VCI, Encapsulation (PPPoE, PPPoA etc), username, password. Configure it for DHCP on the LAN site to automatically assign you PC and IP address.

It's not hard to do. If you get stuck post all the above infos here (except username & password or #### the critical bits out) + the country you live in, ISP and service used. A web link would help.[/QUOTE]
Thanks mips for the info. I've never used this router via USB in Linux formerly. I'm thinking of buying a network card though.

---

### Post by HecKel on 2006-03-03
Hi!

sorry reopen this thread, but anyone can help me to configure this modem/router?

I use the ethernet port, but i can't use net :( I don't known if is relevant..., but I install ubuntu without network connection.

HecKel

---

### Post by mips on 2006-03-04
You need to activate your ethernet card and configure it for dhcp.

The last time I installed Kubuntu with no network it would not allow me to activate the LAN card no matter what I tried so I reinstalled with network enabled.

---

### Post by HecKel on 2006-03-04
hummm, so I need to install again?

When I set my modem/hub to enable dhcp the "link" light doesn't turn on :(

tnks, HecKel

---

