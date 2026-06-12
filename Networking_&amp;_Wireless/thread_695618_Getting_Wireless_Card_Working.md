---
title: "Getting Wireless Card Working"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by mulletman1004 on 2008-02-13
Hi,

I just installed ubuntu studio edition and was looking to get my wireless card up and running. It's a Linksys PCI WMP54G ver 4.1. Now I checked the forum post about supported wireless cards, but it said that my card won't really work without my computer freezing all the time. BUT at one point before I had Ubuntu Gutsy running on the same comp. with the card working fine. I think with that there was some restricted driver I had to enable, but the driver isn't in that menu anymore. I ran lspci -v in the terminal and for the capabilities it says <access denied> if that helps any. I could ping my home network with it, but I can't connect to the Internet.
Any Suggestions?

---

### Post by dca on 2008-02-13
To see capabilities type:  sudo lspci -v
 
You can post the output here, what you're looking for is there should be two entries for ethernet connections... (Wired & Wifi)

---

### Post by mulletman1004 on 2008-02-13
okay i ran sudo lspci-v and this is what i got (note that I didn't copy and paste this so there might be some error)

02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (LOM) Ethernet Controller (rev 81)
      Subsystem: Dell Unknown device 0142
      Flags: bus master, medium devsel, latency 64, IRQ 21
      Memory at ff6fd000 (32 bit, non-prefetchable) [size=4k]
      I/O ports at dc80 [size=64]
      Capabilities: [dc] Power Management version 2

02:0c.0 Network controller: RaLink RT2561/RT61 802.11g PCI
     Subsystem: Linksys WMP54G ver 4.1
     Flags: bus master, slow devsel, latency 64, IRQ 23
     Memory at ff6f (32 -bit, non-prefetchable) [size=32k]
     Capabilities: [40] Power Management version 2

if theres anything else i need to put up just let me know

---

### Post by dca on 2008-02-13
Unfortunately the only thing I see with that Ralink chipset requires the use of ndiswrapper and the Windows driver to work, also the black-listing of the existing RL drivers...  
 
[http://ubuntuforums.org/showthread.php?t=563547](http://ubuntuforums.org/showthread.php?t=563547)
[http://www.gs1.ubuntuforums.org/showthread.php?t=653179](http://www.gs1.ubuntuforums.org/showthread.php?t=653179)
 
Also, if you put in RT2561 ubuntu in Google it references other Linux user(s) having issues with once the card is correctly config needing WICD instead of network-manager, but those articles are old...
 
In reference to Ralink open-source drivers, this offers a how-to also:
 
[http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php?title=Main_Page)
[https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT61)
 
 
...believe me I know, I hate when people leave me a bunch of links but I don't have a Linksys card to test with to even see if I could get it to work using the tutorials.  The nice thing is with all the wireless NIC hardware out there in the universe, there's bound to be someone who's gotten it work in Linux...

---

