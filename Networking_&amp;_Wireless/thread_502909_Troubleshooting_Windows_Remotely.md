---
title: "Troubleshooting Windows Remotely"
date: 2007-07-17
forum: Networking &amp; Wireless
---

### Post by bmt on 2007-07-17
There are several posts asking for and offering help with remotely assisting Windows users from another machine.  One of the most convenient solutions for the technically-challenged Windows user is [UltraVNC Single-Click]("http://www.uvnc.com/addons/singleclick.html"), but it works best in a Windows-to-Windows situation (the non-standard vnc protocols are quite limiting if the listening machine is not running the Windows-only UltraVNC viewer).

I came across [Fazal Majid's weblog entry]("http://www.majid.info/mylos/weblog/2006/09/06-1.html"), describing his experiences supporting Windows users from a Mac.  His solution was to customise the UltraVNC server into a single Windows executable, pre-configured to connect to a specific IP address.  Although somewhat larger than UVNC-SC, it is still small enough for convenient download and works very well.  He now has a facility for customising and downloading the executable directly from his blog page.

After successful tests, this is now my VNC support tool of choice for those persistent family difficulties.;)

---

