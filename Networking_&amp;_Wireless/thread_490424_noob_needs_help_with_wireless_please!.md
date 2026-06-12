---
title: "noob needs help with wireless please!"
date: 2007-07-02
forum: Networking &amp; Wireless
---

### Post by jnalli121 on 2007-07-02
hey guys, as  the title explains i am a noob to ubuntu who just downloaded it, everything seems to fine except for my wireless card, i dont think there is anything wrong with the zcom wireless card that is in my laptop because i dont see anything related to it in restricted drivers. could someone please help me fix this problem. if you need any further info please ask me for it.

---

### Post by thierce on 2007-07-02
Which chipset uses your WiFi card or what is its full name?

Typing 'lspci' in the console throws out a list in which you also should find your WiFi card.

---

### Post by TrueJk7 on 2007-07-02
> **thierce said:**
> Which chipset uses your WiFi card or what is its full name?

Typing 'lspci' in the console throws out a list in which you also should find your WiFi card.

Got the wiki for ya

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by jnalli121 on 2007-07-02
ok i did what it asked and here is the info it came up with for the wireless card

 Ethernet controller: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
        Subsystem: Winbond Electronics Corp W89C33D 802.11 a/b/g BB/MAC
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 6000 [size=256]
        I/O ports at 6400 [size=128]
        Memory at b3400000 (32-bit, non-prefetchable) [size=512]
        Capabilities: <access denied>

---

### Post by jnalli121 on 2007-07-02
someone please help

---

### Post by TrueJk7 on 2007-07-02
Well Ubuntu or Linux at that matter does not commonly support those cards. You most likely will go the route of Ndiswrapper. It makes the windows drivers work for Linux. 

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Also see if it's been tried before to get some more help
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

