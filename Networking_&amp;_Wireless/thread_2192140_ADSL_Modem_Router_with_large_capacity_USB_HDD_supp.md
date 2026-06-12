---
title: "ADSL Modem Router with large capacity USB HDD support"
date: 2013-12-06
forum: Networking &amp; Wireless
---

### Post by arst06d on 2013-12-06
Hi

I currently have a TP-Link TD-W8968 wireless ADSL 2+ Modem Router.  It has a multi-function USB 2 port in the back to allow connection to either an external storage device or a printer.

I have just bought a HGST Touro 4TB external drive and, what do you know, the router does not recognise it.  On contacting TP-Link support they tell me 2TB is the max it can see.  Nothing about this in the specs or on their product pages, of course!  Their suggestion is to partition in half but change the partition mode to mbr instead of GPT.  As if I know what THAT means, or how to do it ...

The router also has a built in media server - but another limitation seems to be it can load only "about" 1000 files.  I just did a quick search on my music directory and am already past 14000 ...

So, suggestions please for:

[LIST]
[*]ADSL 2+ Modem Router
[*]1 or 2 USB 2 (or USB 3) ports to handle external HDD
[*]Capable of recognising LARGE capacity HDD ie > 2TB
[*]DLNA/UPnP certified media server built in
[*]
[/LIST]

Am I asking for too much?

Failing the above, can anyone tell me how to determine what partition mode the disk is currently and, if required, how to change it to mbr mode?


Thanks in advance

---

### Post by mikewhatever on 2013-12-06
You can read about the [GPT mode]("https://en.wikipedia.org/wiki/GUID_Partition_Table"), and to swich to the MBR mode, you'll have to use GParted, a GUI application found in the repositoreis.
I don't have any suggestions on what to buy, but it looks like you need a [home media server]("http://www.howtoforge.com/creating-a-home-media-and-file-server-with-ubuntu").

---

### Post by arst06d on 2013-12-07
Thanks for the reply.
I am already running a home media server, as I have 2 external disks connected to my Ubuntu 12.10 box running Mediatomb, TVMobili and Servii (I like to try things out) straming my music files.  I just wanted to consolidate into one box with increased capacity and take advantage of what the router seemed to offer.

---

### Post by mikewhatever on 2013-12-07
It's hard to think of a router that can offer the same amount of features and flexibility as a dedicated home server. I'd look at something like [dd-wrt]("http://www.dd-wrt.com/site/index"), and if it has what you need, get a compatible router.

---

### Post by arst06d on 2013-12-07
lots to research there - thanks

---

