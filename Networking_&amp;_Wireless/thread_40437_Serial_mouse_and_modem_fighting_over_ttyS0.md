---
title: "Serial mouse and modem fighting over ttyS0"
date: 2005-06-09
forum: Networking &amp; Wireless
---

### Post by tendoku on 2005-06-09
Running Warty,
I had to edit some values in my XF86Config-4 so
that the mouse section appears thusly:

Section "InputDevice"
	Identifier  "Serial Mouse"
	Driver      "mouse"
	Option      "Protocol" "Microsoft"
	Option      "Device" "/dev/ttyS0"
	Option      "Emulate3Buttons" "true"
	Option      "Emulate3Timeout" "70"
	Option	    "SendCoreEvents"  "true"
EndSection
This serial mouse now works fine.

pppconfig can't see modem -it asks to assign tty manually.
The GNOME Network configuration dialogue reported BLANK
ATI values after clicking on the 'autodetect' button.
I tried this for ttyS0-ttyS4. No luck.
My modem is PCI, but has worked well under Libranet and Debian.
Along with the mouse...
It's a USR 5610, and it's "hardware-based".
From lspci:
0000:00:0a.0 Serial controller: 5610 56K FaxModem 56K FaxModem Model 5610 (rev 01)

I know the modem would work if the serial mouse wasn't "in the way".
I could go buy a USB mouse and be done with it, but the fact
this modem worked well under Libranet and the same serial mouse
also worked, is highly frustrating. ](*,) 
TIA for any clues!

---

### Post by tendoku on 2005-06-12
Sorry,
Well, out of desperation, I ran wvdial (which has goten a lot better than I remember it), and wvdial found the modem on ttyS14   S14!! Why can't  pppconfig fsking check
down to that many TTY's???

Now on to the fiddle with the ISA sound card.

What kills me is how UBUNTU found my bro's HP OfficeJet 5500 (brand new printer)
BUT CAN'T SEE THE piddly SOUNDCARD!?!?!?!?!?!?

***Crap like this makes me wonder if LINUX will EVER REALLY gain DESKTOP share in ANY significant measure..............***
Just goes to show that even UBUNTU is NOT 'there yet' WRT "the Desktop".
BAH! ](*,)

---

