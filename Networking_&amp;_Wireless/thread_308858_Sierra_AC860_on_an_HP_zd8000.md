---
title: "Sierra AC860 on an HP zd8000"
date: 2006-11-28
forum: Networking &amp; Wireless
---

### Post by flugh on 2006-11-28
Hello all!

I have an HP zd8000 notebook dual-booting WinXP Media and Ubuntu 6.10. My Sierra ac860 pcmcia card naturally works fine in Windows, but it refuses to play nice in linux. I followed instructions posted at the Sierra site (Linux is unsupported, but they provide a  .dat file for your /etc/pcmcia/cis directory and some config instructions). The failure comes when I run cardmgr and I get this (abbreviated from my notes, didn't copy them to a file before rebooting):
```

Could not adjust resource operation not supported
IO Ports 0x100 - ox3af: Function not implemented
IO Ports 0x3e0 - 0x4ff: Function not implemented
IO Ports 0xc00 - 0xcf7: Function not implemented
Memory 0xc0000 - 0xfffff: Function not implemented
Memory 0xa0000000 - 0xa0ffffff: Function not implemented
Memory 0x60000000 - 0x60ffffff: Function not implemented
IO Ports 0xa00 - 0xaff : Function not implemented

```
I've tried eject/insert/restart services/reboot machine cycles a bagillion times.

I've looked at every English text result Google shows for the above errors, all describe the same issue, but none with a fix that has worked for me. I'm appealing to the community for some help :D Any and all suggestions and assistance would be greatly appreciated!

---

### Post by Makyver on 2007-01-04
Sorry it took so long to get you a reply I had to remember how I did it and where I found the answer ... thus I've posted this on my blog too just so I won't lose it.

[http://makyver.blogspot.com/2007/01/...inux-udev.html](http://makyver.blogspot.com/2007/01/...inux-udev.html)

AC860 and Linux UDEV

Ok so go get the SW_8xx_SER.dat file from Sierra wireless and then copy it (renaming it in the process to) /lib/firmware/SW_7xx_SER.cis this tells the Kernel what the card is and sets it up as a serial device you can then use as a modem for the rest of the steps on Sierra's Linux how-to page ... you don't need to mess with any card utils for this card after that ... just deal with the pppd stuff and it will all go well ... Oh make sure it's not flashing orange it will not function properly when orange. Pull and re-insert it if it's orange it make even take a reboot with the card already inserted make sure you have used the card at least once under windows somewhere or it will still be locked and there isn't a way to unlock it under linux yet. Oh and it won't work until a reboot the first time if you stuck it in before you copied the file.

Get rid of all the stuff Sierra told you to do with card management and this will work great.

---

