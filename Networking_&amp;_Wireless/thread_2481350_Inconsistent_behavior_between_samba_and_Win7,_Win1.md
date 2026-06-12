---
title: "Inconsistent behavior between samba and Win7, Win10, and Win11 clients"
date: 2022-11-26
forum: Networking &amp; Wireless
---

### Post by johnzbesko on 2022-11-26
I am running Kubuntu 22.04 and samba. I have three Windows clients: a virtual Win7 running on the server, an old laptop running Win10, and my wife's newer laptop running Win11.

The Win10 machine detects a (samba-shared) Samsung C1860FW printer and is able to print a test page, using a Windows driver.
The Win11 machine detects the printer, but is unable to print.
The Win7 virtual machine is not able to detect or print, however, if the usb connection that connects the printer to the server is "bridged" to the virtual machine, the Win7 is able to print.

The Kubuntu 22.04 is a recent upgrade. I have had varying degrees of success in the past. In desperation, I completely removed samba and then re-installed and started over with a fresh smb.conf.

Various google searches lead me to mess with various authorization parameters, both in smb.conf and also in the Win registries.

I'm at wit's end and don't know what to make of the cryptic error messages I have gotten. Help is greatly appreciated!

---

