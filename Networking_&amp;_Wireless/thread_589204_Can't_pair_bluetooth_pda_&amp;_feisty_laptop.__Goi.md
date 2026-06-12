---
title: "Can't pair bluetooth pda &amp; feisty laptop.  Going nuts!"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by quixote on 2007-10-24
Everything's working, EXCEPT pairing.  Why?? [updated]

My treo 650 and my computer can see each other.   "hcitool scan" shows the treo and its MAC address.  "hcitool (MAC addr) info" shows all the expected info.  I followed the instructions on the[ ubuntu Palm Bluetooth Howto]("https://help.ubuntu.com/community/PalmBluetoothHowto"), and the excellent how-to  step-by-step at[ pilot-link.org]("http://howto.pilot-link.org/bluesync/fb.html").  As per instructions, I have bluetooth DUN off (although it feels like it should be on!)

But when I follow the instructions on that last page above, it simply will not pair.  

I've checked what's installed.  Gnome-bluetooth is there,  bluez-utils, bluez-pin, bluez-gnome.  It *looks* like everything useful is installed. (?)
I've edited hcid.conf to have the correct passkey, turned security to "none", and entered the device name (palmo).

This treo 650 was once a Verizon phone.  I've never used it for that, but it still has all that junk on there.  Maybe that's interfering?

Once I turned security off, the treo would spend a lot longer trying to verify the passkey I entered (correctly, btw :)), but the result was still the same:  "Unable to add computer-0 to your trusted device list."

Trying to do anything from the laptop end using gpilotd-control-applet gets me nothing but this error message: "Read/Write permissions failed on palmo (/dev/pilot)."  It does this even if I run it as root.  If I use a different connect type (USB, network, etc) I get an error message saying "the port is in use by another application."

I've restarted bluetooth after making changes, and when that didn't help, I've rebooted the system.  Also nothing.  I've tried it in Gutsy.  Same problem with pairing.

I hope someone can tell me what the solution is!  

](*,)

---

### Post by quixote on 2007-10-24
(erm... hopeful bump?)

---

