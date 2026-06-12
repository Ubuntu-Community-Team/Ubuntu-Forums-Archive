---
title: "Ubuntu , OSX printer sharing."
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by MacPC on 2006-11-05
A similar question to the last post.

This one is about printer.

Here is my LAN setup again.

Three Windows PCs using Windows 2000 pro and Windows XP pro.
One Linux PC using Ubuntu 6.06.
Two Macs using OSX 10.8.6.
One HP deskjet 630c printer connects to a Windows desktop via USB.
One Epson Stylus CX4200 printer connects to Mac mini via USB.

All Windows PCs can print to Epson or HP
All Macs can printer to Epson or HP.
Ubuntu can print to HP (the one connecs to Windows desktop, [COLOR="Red"]BUT CANNOT print to Epson (the one connects to the Mac.
[/COLOR]

I did have it working for awhile but then it stoped working.

I tried this:
In the Ubuntu, in the printer setup, I added the Epson as network printer:
Use CUPS, in the URL I typed in <Mac mini IP address>:631/printers/Stylus_CX4200.
in the driver I used Raw-Queue-standard. (I think this is how I get it to work the last time.)

and

Use CUPS, in the URL I typed in <Mac mini IP address>:631/printers/Stylus_CX4200.
in the driver I used Stylus CX4200-Queue-Stylus CX4200.

None of the methods work.

Again, any help will be appreciated. Thanks in advance.

MacPC

---

