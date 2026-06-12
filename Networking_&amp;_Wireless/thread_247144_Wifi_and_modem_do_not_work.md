---
title: "Wifi and modem do not work"
date: 2006-08-30
forum: Networking &amp; Wireless
---

### Post by tpariel on 2006-08-30
hi all,

I am installing my laptop and I need to install the modem and Wirerless connection because until now it hasn't been reconized. What can I do?

Thanks, Ariel.

---

### Post by Neobuntu on 2006-08-30
Today most devices just work. The following assumes your wifi device is not showing up and you can't then put in your wireless network name "ssid."

Please realize that just because something used to work with (now unsupported) Windows 98 (with greater effort to set up) does not always mean it's a failing of (k)ubuntu development.

Why? Because in order to cut costs, SOME cheap modems and Wireless devices were made by Linux hostle companies (AKA Microsoft partners) where they are little more than the connectors. They rely upon your processor to do the real work. Thus, it's all about the driver(Module.) If you have a good driver, it might have new features and it MIGHT be stable but if you don't, your actual throughput suffers, no matter the "connect speeds." In the end, these companies do not LET open development foster on their secret chipsets.

These were called Win-modems BUT now MOST of these devices have been reversed engineered and WORK GREAT with the likes of (k)ubuntu today anyway; no matter the politics. 

With a laptop you are more likey to find these cheap crappy devices. The less widespread, the more it may not be done yet.

There is NO good reason for unstandard dial-up and wireless devices.

WHAT TO DO:

First off you need to check and see what the internal chipsets say they are. Armed with this info, you can see what others are doing online.

If you are saddled with an unsupported or not yet working device, stop beating your head against the wall and replace it. New device that ARE KNOWN TO WORK WITH UBUNTU and can be had for about $10, total. So in summary, just do that.

ALTERNATIVE: If you have an XP driver available for your device, put them in your home directory and you can use ndiswrapper (see ubuntu wiki.) Just point to them again after each automatic kernel upgrade is done. You may wish to download (by direct connect) the GUI for ndiswrapper that makes it an easy point and click. 

NOTE: If a non-working module is loading for your recognised device you have to blacklist it (just put the name in the right text file) and insert ndiswrapper (so taht it works on restarting your computer) in your start up (modules) file. Detailed help abounds. 

Again, if you buy a $10 device (like a PCMCIA card) with a chipset known to work with ubuntu then you're done. The driver set up is automatic and with each kernel upgrade. This is what you want.

Avoid (the internal chipset) companies like Broadcom and Conexant.  I also note that Belkin brand crap doesn't even properly report the internal chipsets. What are they hidding?

In Kubuntu, just run Kinfocenter to see device info.

or type "lspci" in the console terminal to see PCI devices.

Ubuntu has it's own GUI device viewer as well.

Those that fail to get over this hump are doomed by Microsoft. A new world awaits you with Kubuntu. It's well worth the fight. Save time and a lot of money in the long run.

P.S. There is much specific help and guides available here and in the ubuntu wiki.

Dial-up: If you're dead set on dial-up then forget internel devices if you want the best experience (because dial-up is painfully slow and we all need downloads today) then make sure you obtain an old (56K and/or v.90 or better) 3com/USrobitics EXTERNAL and SERIAL connected modem. Yes you'll have to plug in it's power supply but the rewards are many. Steady throughtput, better line conditioning, easy setup, an off switch, volume control, and you can plug it into any other computers serial port for dial-up access post haste. It's almost zero driver setup. Someone may GIVE you their old external serial modem. See Stowetel.com for no-frills $5 a month dial-up (same lines as big wig ISP's.) But be warned, you'll pay $5 no matter what so that's what you risk, and I think the start of the month is about the 28th so be warned. 

WiFi: I've had good luck with Intel wireless devices and you can probably find one on ebay that plugs to your notebooks internal connecter type. But then again, a wireless PCMCIA aka PCCARD is movable. You don't need the fastest because a "b" card is probably faster than your fastest broadband ISP. Get a cheap "g" card with known ubuntu working chipset for a budget deal. I've seen them for $10 shipped (no tax no gas.)

Extra info:
Wifi ALTERNATIVE: You may get a "gaming" wireless ethernet bridge. This would connect WIFi to any computer(or any device with ethernet, like a game console) via it's LAN/networking (ethernet) port. Why? Because the Ethernet port (and it's driver) is already set up on most computers; so you'd now have ZERO driver/module setup and portability for the price of plugging up the external power supply (and about $50).

---

