---
title: "HP PSC 1210v wireless smb networking"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by apostledeets on 2008-08-03
Hello. I almost have my ubuntu system up as it should be. The final thing I have left to figure out is how to print to my HP PSC 1210v printer that's connected to an XP desktop over a wireless smb network. I've tried 

System --> Administration --> Printing --> New Printer --> Windows Printer via SAMBA --> Browse --> Network Name --> Computer Name--> HP PSC 120 --> OK --> Forward --> HP --> Forward --> Models --> PSC 1200 --> Drivers --> Tried both drivers --> Apply.

When I try printing the task shows up on the printer docket on the computer the printer is directly connected to, but nothing prints on the printer, and the printer actually locks up most of the time.

Any help would be greatly appreciated.

Thank you.

---

### Post by aeboi80 on 2008-08-30
Try visiting [http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html]("http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html") it should help.

---

### Post by jja7001 on 2009-03-24
> **apostledeets said:**
> Hello. I almost have my ubuntu system up as it should be. The final thing I have left to figure out is how to print to my HP PSC 1210v printer that's connected to an XP desktop over a wireless smb network. I've tried 

System --> Administration --> Printing --> New Printer --> Windows Printer via SAMBA --> Browse --> Network Name --> Computer Name--> HP PSC 120 --> OK --> Forward --> HP --> Forward --> Models --> PSC 1200 --> Drivers --> Tried both drivers --> Apply.

When I try printing the task shows up on the printer docket on the computer the printer is directly connected to, but nothing prints on the printer, and the printer actually locks up most of the time.

Any help would be greatly appreciated.

Thank you.

I am having exactly the same problem with an HP PSC-1210. In my case the network is ethernet, not wireless, but everything else is the same.

[LIST]
[*]psc-1210 is connected to Windows XP box via USB.
[*]Printer is shared, and works fine locally and from other XP boxes on the network.
[*]When I try to print from the ubuntu-linux box on the network, I see the print job appear in the queue on the XP box, the printer clicks and gurgles a few times, then nothing.
[/LIST]

If I connect the psc-1210 directly to the ubuntu box, it works fine. I can browse XP shares from ubuntu, and vice versa, so Samba seems to be doing its thing properly. 

I tried the suggested link (copied below) and didn't find anything helpful there.

[http://raldztech.blogspot.com/2005/1...-to-linux.html](http://raldztech.blogspot.com/2005/1...-to-linux.html) it should help.

Has anyone made any progress with this problem?

---

