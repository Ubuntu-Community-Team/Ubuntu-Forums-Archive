---
title: "Printer Problem"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by Simon Tregear on 2010-06-06
Hi,

I'm a newbie starting out with Unbuntu 10.4 and cannot install the correct printer driver.  I have a Brother HL-2040 which is on a network using a HP JetDirect print server with a fixed IP number.  

When I use the Add Printer tool, I get all the way through to selecting the model from the database, but the HL 2040 isn't listed.

I've tried downloading the driver directly which the system says its installed, but I can't try to find it?

Using a hint from another post I installed the HL 2060 driver as an alternate, and this seems to work although it is noted that this does not print at all DPI setings and has some margin issues.

Can anyone assist with how to update the database for JetDirect printing or how to install the correct driver?  

I did try some of the suggestion for hp-setup from the terminal window, but this just gave me errors telling me I didn't have a GUI (???), or with the -i switch, said no devices were found.

Any assistance greatly appreciated.

Simon.

---

### Post by WinterRain on 2010-06-07
[Here]("http://www.profv.de/brother/") is the ppd file for your printer. During install, just point it towards this file.

---

### Post by Simon Tregear on 2010-06-07
Many thanks WinterRain - worked a treat.
:)

---

