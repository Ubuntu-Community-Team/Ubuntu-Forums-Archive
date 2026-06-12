---
title: "Illegal output call of P2PObject:48  -- and P2PObject:49"
date: 2014-06-03
forum: Networking &amp; Wireless
---

### Post by sunshinelock on 2014-06-03
I have 3 computers running Ubuntu 12.04, networked with a Brother MFW490-CW wireless printer.

Just yesterday, 2 of my computers started giving errors of "Illegal output call of P2PObject:48" in the print box when sending a print command like so:

Right click,
"Print"
"Print using system dialog"
Then under the "Print" window, "General" tab, under my Printer Status, I get this "Illegal output call of P2PObject:48" and it rapidly cycles through "Illegal output call of P2PObject:49", back and forth.

The 3rd computer prints fine.

I've searched Google and Bing and this forum and nothing turns up.

I've rebooted my computers, my printer, my wireless network.  Nothing works.

---

### Post by sunshinelock on 2014-06-03
SOLVED.

Through error logs it appeared to be coming from CUPS.

I logged into [http://localhost:631](http://localhost:631) and entered my username and password and saw the print job with the error clogging the system. I deleted the print job and it started printing again.

---

