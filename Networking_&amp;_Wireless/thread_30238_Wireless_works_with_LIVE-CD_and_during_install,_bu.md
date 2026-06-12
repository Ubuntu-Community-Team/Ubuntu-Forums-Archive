---
title: "Wireless works with LIVE-CD and during install, but not after reboot."
date: 2005-04-27
forum: Networking &amp; Wireless
---

### Post by ChristianL on 2005-04-27
Hi,

I just installed Ubuntu 5.04 (Hoary Hedgehog) on my DELL laptop. Everything seems to work great except for my wireless interface. It works fine with the Ubuntu LIVE CD, and it worked when I first installed Ubuntu. I even set my SSID and WEB key, and browsed the web. As soon as I rebooted after the install, no more wireless...  :???: The eth0 is GONE. **This is very frustrating**...

I'm using a "Linksys WCF12" 802.11b with a CompactFlash to PCMCIA adapter. This card uses the Prism 3 chipset. I found the following in /etc/pcmcia/config:

```
card "Linksys WCF12 Wireless CompactFlash Card"
   manfid 0x028a, 0x0673
   bind "orinoco_cs"
```

Therefore, my card is supported by the "orinoco_cs" driver. So far so good. When I type "cardctl ident" I get:

```
Socket 0:
   product info: "Linksys", "Wireless CompactFlash Card", "", ""
   manfid: 0x028a, 0x0673
   function: 6 (network)
Socket 1:
   no product info available
```

So my card was identified correctly by the PCMCIA. Also, the orinoco drivers came with the kernel, and when I type "modprobe orinoco" I don't get any error messages or warning.

Unfortunately, the "ifconfig" and "iwconfig" commands don't see my wireless card. The "Network settings" GUI doesn't see it either. It's as if it wasn't there.

It seems like something is falling through the cracks between the PCMCIA and loading the orinoco drivers. What else can I do? Any ideas?

Regards,
ChristianL.

---

### Post by ChristianL on 2005-04-27
I forgot to mention:

I looked in the /var/log/messages and nothing happens when I insert the card. I also looked in dmesg and nothing happens there either. I did notice that the orinoco in dmesg:

[PHP]orinoco 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
orinoco_cs 0.13e (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)[/PHP]

Please help...

---

