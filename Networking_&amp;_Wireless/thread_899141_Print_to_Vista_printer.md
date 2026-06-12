---
title: "Print to Vista printer"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2008-08-24
Hi,

I'm trying to print form Ubuntu 8.04 to a HP Deskjet, which is attached via USB to Windows Vista.

Router Port 631 is forwarded to the XP machine (192.xxx.x.xxx) & Vista box is powered on.

I've tried to configure printing in Ubuntu via "IPP", however, it doesn't find the printer. 

Any ideas out there?

---

### Post by melojo on 2008-08-24
I did it with smb(samba)  I made sure print sharing was on the printer I wanted(goto control pannel-printers-find the printer and right click on it and goto sharing-turn it on(I don't have password protection on).

Then I had to goto control panel-network and sharing-print sharing click on the arrow and make sure it say on then I had to go down to password protect sharing and turn it off.

On the ubuntu machine I went to system-administration-printers-windows printer via samba-then hit the browse button and it pulled up my printers I clicked on the printer I wanted then I had to pick a driver that was a close match.

good luck

I haven't tried any other way yet, I hope this helps!!

---

### Post by DapperMe17 on 2008-08-25
Thanks melojo,

Good info & I'll give it a try!

---

