---
title: "ACX100 Wireless Help"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by darkeye123 on 2009-11-16
Hello,

I have been having some troubles with my getting a wireless card to work on an older computer. 

I have just installed Ubuntu 9.10 on it, and although it finds the hardware in lspci, it cannot use it to connect. (no iwlist scanning, or connect option)

The Wireless card is a D-link DWL 520+, which uses the ACX100 Chipset. (I think. :) )

Here is the lspci output:
```

00:08.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
```

I have read many different sites and tutorials on how to go about installing the drivers for this card, but since I'm really new to linux, I don't really understand how to go about installing the drivers for it. (If you provide step by step instructions I should be able to follow them.)

Thanks again for your help.

---

### Post by darkeye123 on 2009-11-16
I figured it out.

Turns out that I needed to download the driver from the Dlink Ftp and then use ndiswrapper to install it.

Thanks :)

---

### Post by darkeye123 on 2009-11-16
I guess my problems aren't over.

I have my Wireless Network set up correctly in the Network applet, and When I try to connect, it shows the rotating connector circle in the top panel. However, after about 30 seconds of this circle rotating, it prompts me for my password, which I enter. 
It will continually do this, until it finally gives up and disconnects me.

I am using a Dynamic IP address assigned by my router. Perhaps this is a dhclient issue?

---

### Post by Dude-PWB- on 2009-11-16
Have you tried taking your adapter down, and then back up?

I think the commands are:

```
ifconfig wlan0 down

ifconfig wlan0 up
```

or just:

```
sudo /etc/init.d/networking restart
```

---

### Post by darkeye123 on 2009-11-16
I tried what you stated above.

There doesn't seem to be much change. The network circle still spins endlessly, occasionally asking for my password before giving up altogether.

Thanks again!

---

### Post by Dude-PWB- on 2009-11-16
Did you get win98/2k/xp drivers for ndiswrapper?

Sometimes the older win drivers work better than the new ones in ndiswrapper.

What is the network section of lspci -vv?

---

### Post by darkeye123 on 2009-11-16
Yes, I am using the Win XP drivers for ndiswrapper. If worse comes to worse, I will try using some older drivers.

lspci -vv:

```
00:08.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
    Subsystem: D-Link System Inc Device 3b01
    Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 32, Cache Line Size: 32 bytes
    Interrupt: pin A routed to IRQ 16
    Region 0: I/O ports at d000 [size=32]
    Region 1: Memory at e2010000 (32-bit, non-prefetchable) [size=4K]
    Region 2: Memory at e2000000 (32-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ndiswrapper
```

Thanks

---

### Post by Dude-PWB- on 2009-11-16
Ok, here is another option I found. Looks like alot of work, and I'm no expert either. Just good at finding things. :)

[http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)

Also:

[http://forums.remote-exploit.org/158525-post10.html](http://forums.remote-exploit.org/158525-post10.html)

Looks like that last link the guy just installed it last month.

All for native linux drivers, rather than ndiswrapper.

Hope that helps.

---

### Post by darkeye123 on 2009-11-17
I downloaded the firmware, but when I went to place it in /lib/firmware/acx/
I discovered that were already a ton of folders in /acx/, with a ton of different firmware types.

I'm not really sure how to proceed at this point. Should I just go out and buy a less obscure network card? 

Thank you very much :)

---

### Post by darkeye123 on 2009-11-17
bump for help and ideas.

---

### Post by Dude-PWB- on 2009-11-17
Yeah, that might be a better plan than trying to hack that one together. I'm not completely sure where I would put that firmware without actually looking at it and messing it up and then fixing it again. ;)

I was kinda hoping someone else might chime in with some extra help.

Something with a ralink chipset, or atheros would be the best bet for a card, most of them work right out of the box.

---

### Post by darkeye123 on 2009-11-17
What card would be recommended then? I think I will be able to go tomorrow, and I want to make sure that I get a card that will work out of the box or work fairly easily with ndiswrapper.

What kind of card should I look for? Is the chipset of the card listed on the purchase box? Should I buy a card from a specific Brand?

Any Suggestions?
Thanks again

---

### Post by Dude-PWB- on 2009-11-17
I think almost all of the Ralink cards are fully supported in linux, and most of the realtek and Dlink cards will work one way or another.

Here is a list I found that might help: [http://www.fsf.org/resources/hw/net/wireless/cards.html](http://www.fsf.org/resources/hw/net/wireless/cards.html)

---

### Post by Dude-PWB- on 2009-11-17
Here is another list I found right here as well.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by darkeye123 on 2009-11-17
Thanks a lot.
Will post back when I get a new card. :)

---

### Post by aapo4 on 2009-11-18
There are one success story about native acx-driver on Karmic:

[http://ubuntuforums.org/showthread.php?t=1321303](http://ubuntuforums.org/showthread.php?t=1321303)

What is right place to make bug report and offer this patch? Because bug is acx is removed.

---

### Post by darkeye123 on 2009-11-18
Bought a Linksys WMP54G wireless card today. Installed without a hitch. 
Thanks for all your help!

---

