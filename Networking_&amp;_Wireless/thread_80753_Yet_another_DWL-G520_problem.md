---
title: "Yet another DWL-G520 problem"
date: 2005-10-22
forum: Networking &amp; Wireless
---

### Post by ubutthead on 2005-10-22
I've been messing with this damn card for 6 hours now.  Nothing I have tried works.  I am unable to get a connection to the 'net, I can't ping my AP/router, I can't do a damn thing.

I've scrolled this forum for hours trying everything that was shown to work and I still cannot get it to work.  I'm using Ubuntu Breezy Badger Kernel 2.6.12-9-386.

I have downloaded, complied, and installed the newest version of madwifi - I've installed Shareutils, Binutils, apt-get install build-essential.

I've run the gamut of options and still nothing.  ifconfig and iwconfig both show the card as ath0 with all the necessary information there.  However, when I try dhclient I keep getting the errors:   No DHCPOFFERS received AND No working leases in persistent database - sleeping.

I cannot ping a damn thing and so far I'm seeing that I'm losing 100% of the packet's bein sent.  Nothing is being received.  HELP!

If I don't get this figured out very soon, I'm going to scrap Ubuntu and put another Distro on the PC.  I need this to work.

TIA

ubutthead.

---

### Post by malegria on 2005-10-23
I have the very same card and have been able to get it going quite easily. Here are some quick tips:

1. Are you on the right channel? (if not, do: sudo iwconfig ath0 channel #)
2. Do you have right essid? (if not, do: s udo iwconfig ath0 essid your_essid)
3. Are you in the right mode? (if not, change it: sudo iwconfig ath0 mode managed_or_master)
4. You DO_NOT need the newest version of madwifi. The Breezy one works just fine.
5. Also, before doing _sudo dhclient ath0_ first do _sudo ifconfig ath0 up_, ok? Or else there's no point of trying to run the dhclient

Hope this works, or else send me a PM with your chat info.

---

