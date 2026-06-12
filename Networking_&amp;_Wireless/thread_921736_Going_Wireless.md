---
title: "Going Wireless"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by calvert, phil on 2008-09-16
I have a Linksys Router WRT54G, and for internet I use Embarq 660 Modem. So far I cannot wirlessly connect my PCI Adapter (Linksys WMP54G v4.1) to connect or even work... Right now I am using an ethernet card to connect via cable, but am hoping someone knows how to connect wirelessly? Anyone with help that would be appreciated!

---

### Post by nixscripter on 2008-09-17
I think that's one of the cards you have to use ndiswrapper for. If you install the driver for it, it should just detect your access point.

You can find general directions for installing ndiswrapper here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you got a driver CD with the card, try and find an INF file on it which ndiswrapper can load (rather than going to the internet as they suggest).

Hope this helps.

---

