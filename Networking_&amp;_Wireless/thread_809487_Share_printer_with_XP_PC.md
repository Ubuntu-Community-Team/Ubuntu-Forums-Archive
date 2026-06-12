---
title: "Share printer with XP PC"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by aleska on 2008-05-27
Having difficulty finding a recent post or relevant how-to on how to share my printer, attached to my Ubuntu Hardy pc via USB, to a windows XP pc on same home lan.
I used to share my printer with all my home pcs (ubuntu, mac, windows) by attaching it directly via usb to a linkstation nas running samba.  I didn't have to configure anything, it was just available.
Now I'm attaching my printer directly to my ubuntu hardy box, because I need to use scanning functions which weren't workable when attached to the NAS.  
My Mac was able to locate it no problem.  My other ubuntu pcs are also able to find it no problem.  
I installed samba, and changed /etc/samba/samba.conf and changed options to include things like "browseable = yes" and "guest ok = yes".  
Windows XP shows my ubuntu computer now, but doesn't seem to see any associated printer to include when going through add a printer.  
Any tips to get me going in the right direction?  TIA

---

### Post by DocPaine on 2008-05-28
I hate to say "Me Too!" here, but me too!  I have a mixed-mode home network, and have finally convinced my wife to make the switch.  She's running 8.04 and having a blast with it -- problem is that our Epson CX5400 is hooked up to her computer.  While she was running XP there was no problems with sharing the printer with everyone (including my Ubuntu-based PC), but now that she's running Ubuntu full time the two windows-based PCs (one XP-based laptop and one Vista laptop (provided by the kid's school -- not MY choice, but hey, free laptop!)) can't see the printer anymore.

I'm the old-school user, so I've tried all the usual tricks with hand-configuring SAMBA.  The shares SHOULD work -- there's something I'm missing here...  :(

Cheers,

Doc

---

