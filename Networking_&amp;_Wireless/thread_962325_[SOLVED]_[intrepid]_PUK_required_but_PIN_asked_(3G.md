---
title: "[SOLVED] [intrepid] PUK required but PIN asked (3G/Vodaphone)"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by stephanvaningen on 2008-10-29
I have a 3G/GPRS Datacard of Vodaphone (Proximus Belgium) of which the PIN code seems to be entered wrong since I get this in the system log (line 3 informs me that a PUK code is required):
```
Oct 29 10:45:17 CMHQLT062U NetworkManager: <debug> [1225273517.311985] nm_serial_device_open(): (ttyUSB0) opening device... 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  (ttyUSB0): GSM puk secret required 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Oct 29 10:45:17 CMHQLT062U NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4
```
If I disconnect and re-connect the card (PCMCIA) in the laptop, it prompts me again just for a PIN code, but it never asks for a PUK code.

How can I make sure the system asks for my PUK code?

---

### Post by stephanvaningen on 2008-11-07
Nevermind, I worked around this by putting the SIM-card of the datacard in my mobile phone and unlock the PIN from there by entering the PUK.

I started a new thread however describing the behaviour that [the card never creates a connection but immediately repetitively reports a 'PUK required' message in the system logs]("http://ubuntuforums.org/showthread.php?p=6128707").

---

