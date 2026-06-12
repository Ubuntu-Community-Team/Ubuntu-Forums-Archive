---
title: "how can I increase my computer's graphics performance?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by bhavananandan on 2008-12-07
I have a computer with:

Intel Pentium 4 Processor 2.60 Ghz
622.2 mb RAM.

But my graphics run awfully slow. This is clearly visible when I play a game. They are extremely slow. When I type the following in the terminal ```
lspci
```

It gives the following result:
> 00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 Communication controller: Conexant HSF 56k HSFi Modem (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)


Is it the fault of my graphics card, or is it my slow computer? Or is it something else?

Plz help me

---

### Post by cartisdm on 2008-12-07
What game are you trying to play?  You don't have very much RAM for one thing, but your computer isn't obsolete

---

### Post by kerry_s on 2008-12-07
try reducing the resources used, so you have more for the game. for instance install a light wm and use that for gaming, as it won't have as much stuff running behind the scenes.

---

### Post by x58 on 2008-12-07
To play games need to have MAXIMUM RAM.(2 GP is good).

---

### Post by DBrocks on 2008-12-07
Looks like its an integrated GPU (graphics processing unit). Integrated is never really truly good, but they work for most things. I would say get a REAL graphics card (PCI or AGP). But someone else probably has another solution. BTW, what game are you playing, and can you turn down the graphics level a bit? Running games on max graphics can result in slow graphics.

---

### Post by Rocket2DMn on 2008-12-07
For starters, make sure compiz is off when you play games since it competes with your game for direct rendering.  Revert to metacity in this case.
Since your graphics card is integrated, you may need to free up RAM space as well, so close unnecessary programs when you play games.
For terminal changing between compiz and metacity:
```
compiz --replace &
metacity --replace &
```
or use System->Preferences->Appearance, Visual Effects tab.

---

### Post by Skripka on 2008-12-07
> **DBrocks said:**
> Looks like its an integrated GPU (graphics processing unit). Integrated is never really truly good, but they work for most things. I would say get a REAL graphics card (PCI or AGP). But someone else probably has another solution. BTW, what game are you playing, and can you turn down the graphics level a bit? Running games on max graphics can result in slow graphics.

Integrated graphics are bad for just about anything graphics intensive.  In part because a good chunk of your system memory is eaten up (hence your "622Mb" figure--and is slow/



I presume this is a laptop?  If so you're pretty much SOL--about your only option is to buy a machine with a real graphics card in it.  This is why laptops suck-you cannot upgrade them, unless you want to pull out a soldering iron.  Turning off Compiz is about all you can do.

If this is a desktop box--see about getting an actual graphics card.

---

### Post by DBrocks on 2008-12-07
Or if its a desktop box, try upgrading your ram to the max your mobo will support. Boot into your bios, and try to set the memory allocated to video a bit higher. (This is only supported on Bios's that have integrated video chipsets. This will not work on all bios's)

---

### Post by bhavananandan on 2008-12-07
thank u all guys for your tips. I'll try them. Let me tell you the games I play:

(1)Counter Strike Condition Zero (on Wine)
(2)Nexuiz
(3)Torcs
(4)Motocross Madness (on Wine)
(5)Tremulous
(6)Xmoto
(7)FlightGear

The graphics run the slowest on (1), (2), (3), (4), (5), (7)[well, that means on almost all!]

---

### Post by bhavananandan on 2008-12-07
mine is a desktop. I use compiz.

Do you think that while playing games, I should stop it? Also will it help if I use Fluxbox(I have it)?

---

### Post by DGortze380 on 2008-12-07
> **bhavananandan said:**
> thank u all guys for your tips. I'll try them. Let me tell you the games I play:

(1)Counter Strike Condition Zero (on Wine)
(2)Nexuiz
(3)Torcs
(4)Motocross Madness (on Wine)
(5)Tremulous
(6)Xmoto
(7)FlightGear

The graphics run the slowest on (1), (2), (3), (4), (5), (7)[well, that means on almost all!]

time for a new comp. you can build one 100x better for $300 on Newegg.

---

### Post by Rocket2DMn on 2008-12-07
Turning off compiz when you play will definitely help.  However, we can't help you more than your hardware is actually capable of.  I don't know all those games, but you should be able to play some of them decently with compiz off and unnecessary programs closed to save RAM.  Fluxbox may save you some RAM and offer a little bit more speed in the GUI.

---

