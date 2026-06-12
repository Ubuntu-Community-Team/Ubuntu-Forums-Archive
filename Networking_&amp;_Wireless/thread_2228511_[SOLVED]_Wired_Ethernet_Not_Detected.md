---
title: "[SOLVED] Wired Ethernet Not Detected"
date: 2014-06-07
forum: Networking &amp; Wireless
---

### Post by sunnybubblegum on 2014-06-07
My computer is wired to my router by ethernet cable (via an ethernet-over-powerline adapter), but Ubuntu is not recognizing any connection. On my desktop, under 'Wired Network' (top right) it just says 'disconnected', and in the System Settings panel in 'Network' under 'Wired', it says 'Cable Unplugged' (followed by 'Hardware Address 20:CF:30:3F:FD:93').

However, the activity lights on my computer's ethernet card are flickering with activity.

I used to connect to the internet successfully using a wireless-G USB adapter, without any configuration. However, it died last week; that's why I've opted to go wired. Anyway, I know my Ubuntu is internet-capable.

Internet is working great on other devices in the house (via wi-fi), so the problem isn't there.

I've also tested with two different ethernet cables, and both work. So the issue isn't there either.

In terminal, if I enter 'ifconfig eth0', I get:

[I]eth0
[/I][INDENT][I]Link encap:Ethernet  HWaddr 20:cf:30:3f:fd:93
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)[/I][/INDENT]

If I enter 'lspci', among the listed is:[INDENT]*02:00.0 Ethernet controller: Qualcomm Atheros AR8131 Gigabit Ethernet (rev c0)*[/INDENT]

I've tried a number of solutions recommended on forums around the internet (i.e. 'eth0 down', 'eth0 up', network restart, etc), but nothing has worked.

I'm starting to wonder if maybe my ethernet card, the Atheros AR8131, isn't supported on Linux. Could this be the case?

Are there recommended ethernet cards that are known to 'just work' with Ubuntu?

Or, maybe there is just a step I need to perform to get Ubuntu to recognize my wired ethernet connection?

Is there any other helpful information I can provide on my system to ascertain the situation?

Thank you.

(Bear in mind, I'm typing all this on a tablet touchscreen. The shorter the console output, the better.)

(The ethernet-over-powerline kit I'm using is the Trendnet TPL-406E2K. I just got it yesterday.)

System specifications:
Ubuntu 12.04.4, 64-bit
Unity Desktop Environment (vanilla)
AMD Athlon II X4 645, 3.10 GHz
8GB RAM
AMD Radeon HD 6790
ATI/AMD Proprietary FGLRX Graphics Driver (**Experimental** Beta)
Apple AirPort Express 802.11n Wi-Fi Router
Trendnet TPL-406E2K Ethernet-Over-Powerline Adapter Kit

---

### Post by sunnybubblegum on 2014-06-07
I can't believe this, but I finally happened to notice there were *two* ethernet ports on the back of my computer, and I was plugged into the *wrong one*!

If you're like me, make sure you're plugging into the *onboard ethernet plug*, not the PCI one -- and make sure your *onboard LAN controller* is enabled in your *BIOS*.

My internet is working great now. Augh, I feel like such a dolt! :D

My greatest apologies if you actually took the time to read this tome.

---

