---
title: "PPC with Broadcom Wireless"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by majkmil on 2005-11-20
I have this ( Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02) wireless card in my G4 ibook laptop. I have a network icon in the taskbar on top. It shows activity. When I go to properties it shows packets transmitting and recieving. There is a button for configureing but it is greyed out. It is called (lo) in properties but does not showup in the network, only etho and modem. Seems odd that I cannot configure. Do you think the driver is installed and if so how can I tell?   Thanks

---

### Post by mips on 2005-11-20
I might be mistaken but as far as I know there is no LInux broadcom drivers yet. The i386 versions use NDIS wrapper to make the card work using original windows drivers which will not work on PPC architecture.

There are attempts to write a native Linux driver for the broadcom chipsets though. I have also heard of people getting the card to work via some for of emulation via OSX or something like that but I'm not sure about ths.

---

### Post by punkr0x on 2005-11-21
lo is the loopback device, I don't know why gnome bothers showing network activity for that...

---

