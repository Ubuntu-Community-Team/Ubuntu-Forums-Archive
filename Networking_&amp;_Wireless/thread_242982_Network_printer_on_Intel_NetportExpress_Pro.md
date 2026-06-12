---
title: "Network printer on Intel NetportExpress Pro"
date: 2006-08-24
forum: Networking &amp; Wireless
---

### Post by oliverb on 2006-08-24
I've been using a Panasonic KXP2123 connected via a NetportExpress Pro as a shared printer from Windows. As far as I know it's using SMB printing, though 
under 98 it seems incapable of printing unless the Netport software is installed. Anyway I decided to try to install it in Ubuntu (6.06).

My attempts to get it to work as a SMB printer failed but a look at Intel's site revealed that it probably supported LP printing as there were several varieties of unix mentioned.

So I tried Unix Printer (LPD) and got a rough printout, which was some improvement. However the printout shows signs of code mangling, possibly caused by automatic linefeed insertion, and the intel instructions say the remote printer name should be LPT1_PASSTHRU but there is nowhere to specify this except possibly queue name and this gets cleared when I close the config window.

---

