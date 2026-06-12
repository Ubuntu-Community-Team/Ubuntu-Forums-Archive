---
title: "Added Brother printer successfully, but printer now changes IP on its own!"
date: 2013-12-02
forum: Networking &amp; Wireless
---

### Post by estods76 on 2013-12-02
The title almost says it all, I added my printer using the Brother printer install script via the terminal, and now every time i go to print, the printer has changed its IP address. to correct the issue, i have to go to the printer properties on my computer and change the device URI to the new IP. Also, I have a windows 7 computer that cant access the printer anymore either. It just says that "the printer is now offline". Anybody know why this is happening and what i can do? I am very new to linux.

NOTE: the brother printer is a HL-2280DW, it is installed with the cupswrapper and drivers and whatnot using this [FONT=Courier New]http://www.brother.com/pub/bsc/linux/dlf/linux-brprinter-installer-1.0.4-1.gz [/FONT]

---

### Post by jboyette on 2013-12-04
you most likely need to download and install BRadmin light from solutions.brother.com and set the print server to a static IP address instead of AUTO or DNS.

---

