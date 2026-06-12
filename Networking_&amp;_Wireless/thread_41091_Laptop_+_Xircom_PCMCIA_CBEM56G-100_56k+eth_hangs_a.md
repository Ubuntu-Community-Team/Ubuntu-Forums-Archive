---
title: "Laptop + Xircom PCMCIA CBEM56G-100 56k+eth hangs at 'sudo pon'"
date: 2005-06-11
forum: Networking &amp; Wireless
---

### Post by lark5000 on 2005-06-11
I've installed a Xircom 10/100 ethernet + 56k modem in a HP N5450 laptop.  It is said to be supported by scanModem.  The vendor is Xircom and the device ID is 0103.  I bought this card off of ebay since the built in modem manufactured by ESS is definately not supported.  I have had no luck  trying to get this thing to fly.  I have compiled drivers from ltmodem-2.6.7-alk-7.tar.bz2 and ltmodem-8.31a10.tar.gz.  I activated each using sudo modprobe lt_serial and sudo modprobe lt_modem and when that didn't work, sudo modprobe ltserial and sudo modprobe ltmodem.  The problem is that the gui dialers and sudo pon hangs the system.  Its driving me crazy as I'm trying to ready this laptop by next week for someone who is sick of Windows malware/spyware.  Ethernet internet works fine at my home but he wants dialup.

Does anyone might know why it hangs?  Any help would be appreciated.

The odd thing is that the drivers documentation refer to the modem as /dev/ttLTM0.  WVDial insists that it sees it as /dev/ttyS14.  I don't know if this has anything to do with it.  The other question I have is whether I actually compiled the right driver.  I thought that since I have PCMCIA modem here that the PCMCIA driver from ltmodem.heby.de might be the right one, although scanModem only mentions the two I have mentioned above.  Any takers?

---

### Post by alex2035 on 2005-07-29
your modem is NOT a linmodem, are you trying to put windrivers?
I have a xircom ethernet 10/100 + 56K modem and a Dell Inspiron 3200. try to make this work in a lot of Linux distros. it only did in Feather and DSL but I wanted a distro a bit more "fat". went to ubuntu cause it is Debian as well, thought it would work out of the box. no way yet.

I have to start searching the tools in ubuntu but it might help to tell you this card needs xircom_tulip_cs or xircom_cs binded to serial_cs . type cardinfo to see if it is ready .
another useful command is cardctl status and cardctl ident. I got all this OK except cardinfo says there is NO card inserted! 

the device database hangs when it comes to the network detection, but device manager shows the 2 sides of the card recognized. what command or frontend do you use in ubuntu to detect7configure the netcard and modem?

thanx
alex2035

---

