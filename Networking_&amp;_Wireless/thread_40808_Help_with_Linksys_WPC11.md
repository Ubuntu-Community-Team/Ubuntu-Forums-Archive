---
title: "Help with Linksys WPC11"
date: 2005-06-10
forum: Networking &amp; Wireless
---

### Post by daageep on 2005-06-10
Hey guys,

I've been tinkering with my wireless card and cannot get it to work 100%. My laptop has onboard ipw2100 centrino wireless and works flawlessly out the box. I can connect to my router with WEP using the graphical gnome networking tool. 

Lately I've been trying to install my Linksys WPC11 wireless pcmcia card (I think version 1.02)? Cardctl ident gives product info: "Instant Wireless ", " Network PC CARD", "Version 01.02", ""
  manfid: 0x0156, 0x0002

and I swear the cardctl ident also told me that my card is "prism 1" before. anyway I have compiled the newest wlanng drivers and patched it up, so the card seems to be detected and "working" on wlan0. 

I have two main issues I need help with: 
1) I cannot get any connection to my own router with this card but can with my centrino card. I've tried the graphical way and failed. I've tried sudo iwconfig wlan0 essid wireless and iwconfig wlan0 key my_wep_key.

2) I cannot use "sudo iwlist wlan0 scanning" at all: "Interface doesn't support scanning : Function not implemented" (I'm using prism2_cs). My centrino scans just fine. 

Is it because i'm using prism2_cs when I only have prism 1? Can anyone confirm this? Any help will be much appreciated! thanks.

---

### Post by jkndrkn on 2005-06-11
I haven't had any success with my wpc11, but my linksys wusb54g works fine.

---

### Post by daageep on 2005-06-11
does anyone know what chipset my card is? its wpc "instant wireless" version 1.02 when i type cardctl ident. thanks!

---

