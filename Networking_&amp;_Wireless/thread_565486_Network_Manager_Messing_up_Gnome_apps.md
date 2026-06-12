---
title: "Network Manager Messing up Gnome apps"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by LavianoTS386 on 2007-10-02
On [my laptop]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01069930&lc=en&cc=us&dlc=en&product=3441683&rule=14752&lang=en") whenever I am connected to a network,  either wirelessly or by Ethernet, gnome applications fail to load beyond a window boarder and nautilus windows grey out when I try to open files. When I disable networking, everything is fine.

I'm using ndiswrapper for wireless and the latest version of Gutsy.

Where should I begin to look for the problem and is there anything I can do?

---

### Post by kevdog on 2007-10-02
Im not sure if you can blame this one squarely on Network Manager, however if you are fairly convinced its network manager, one thing you could do is to install wicd (a network manager alternative) and see if the same thing happens.

Be sure to use the testing version (not the stable version) -- I know it seems counterintuitive -- just trust me on this one:

[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

The 1.34 deb file is the one you want.

Instructions are listed here:
[http://wicd.sourceforge.net/wiki/doku.php?id=faq](http://wicd.sourceforge.net/wiki/doku.php?id=faq)

---

### Post by LavianoTS386 on 2007-10-02
Here's what shows up in my debug log...

> 
[ 3478.540000] spurious 8259A interrupt: IRQ15.
[ 7265.588000] wlan0: no IPv6 routers present
NetworkManager: <debug> [1191342543.247647] nm_print_open_socks(): Open Sockets List: 
NetworkManager: <debug> [1191342543.247676] nm_print_open_socks(): Open Sockets List Done. 

---

