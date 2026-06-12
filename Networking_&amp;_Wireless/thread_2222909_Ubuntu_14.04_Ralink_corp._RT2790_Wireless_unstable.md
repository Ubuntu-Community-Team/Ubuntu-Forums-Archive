---
title: "Ubuntu 14.04 Ralink corp. RT2790 Wireless unstable connection."
date: 2014-05-08
forum: Networking &amp; Wireless
---

### Post by acidsnake-dev on 2014-05-08
Long story short, I updated from ubuntu 12.04 to 14.04, had some issues with the kernel (resolved by adding acpi=noirq and nomodeset as parameters) but overall everything was working fine, until I updated the kernel yesterday and wifi started giving me some problems, the syntoms are:
- connection drops after some minutes of using (sometimes it can stay connected up to an hour and then fail, sometimes only a few minutes).
- once the connection drops, it's unable to reconnect.
- streaming big chunks of data (like a youtube video or downloading a big file) makes the connection drop directly.
- sometimes I can get it back up by stopping network-manager, unloading the rt2800pci module, loading it again and starting network-manager, but this only works sometimes and I am forced to restart the computer.
- it's not a hardware fault, wifi works well in windows (none of the above symtoms).

I've tried the following to fix the issue:
- disable power management (it was already disabled anyways).
- disable 802.11n (which makes no difference as this card only supports 802.11n).
- compiling the rt2860sta driver (which works but still gives the same problems, probably even worse).
- compiling backports and compat drivers (couldn't get any of them to compile).
None of this worked.

Other things to note:
- when I updated the kernel the nvidia drivers weren't working (I have a GeForce 8200M G). I had to uninstall the drivers from command-line and reinstall them with "Additional Drivers". This also happened when I updated from 12.04 to 14.04.

---

### Post by acidsnake-dev on 2014-05-10
bump. I really need to fix this, or I'll have to format and go back to 12.04, which was thousands times better in every aspect.
Is the ubuntu team trying to copy microsoft even at failing?

---

### Post by nisko666 on 2014-07-09
I'm experiment the same problems. I don't know how solve this.

---

### Post by nisko666 on 2014-07-09
I'm testing this, [http://ubuntuforums.org/showthread.php?t=2204912&page=3](http://ubuntuforums.org/showthread.php?t=2204912&page=3)

---

### Post by flame2196 on 2015-01-06
Same problem still can't fix.
Bump for who know

---

### Post by UnderSurveillance on 2015-06-06
Any progress?  I'm having similar issues. Except that recently I haven't been able to connect at all.

---

