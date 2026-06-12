---
title: "LAN connection not working but ethernet light is active"
date: 2018-10-16
forum: Networking &amp; Wireless
---

### Post by jrsc on 2018-10-16
Hello,

I am trying to get an old computer (2006ish) to work again (installed windows 7 at first on it but the network drivers were only for xp and vista and i couldn't get them to work so i couldn't manage to establish a LAN connection).

Then, i've installed Lubuntu 18.04 32 bit on it because i know linux has better driver support, and even though the ethernet cable was connected during the OS installation and the light is still active, it cannot make a LAN connection.

I know the cable and the router are ok because when i plug it to my 2011 computer, it establishes a LAN connection instantly (automatic DHCP enabled). With the older computer, i have also tried adding an old network (neither the integrated card, neither this one have WIFI support, just wired) card just to see if the LAN would be working with it but it still doesn't even though the light works too when the cable is plugged in. I have experience with the linux command line but i never used it to fix a network issue so i'm quite lost, can you guys help please ?

Thank you

---

### Post by wyliecoyoteuk on 2018-10-16
Any idea what chipset?
Try```
ifconfig
``` and ```
lspci
```to see if there is anything detected.

---

### Post by jrsc on 2018-10-17
Thank you for the help, a friend fixed it for me, turns out the LAN was turned off in the BIOS, didn't even know that was possible !

---

