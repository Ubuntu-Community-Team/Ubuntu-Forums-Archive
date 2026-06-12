---
title: "Conexant PCI Internal Modem"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by Filiprino on 2006-07-31
HI, I'm writting this post 'cos i have a problem with a conceptronic winmodem, based on a conexant chipset.
I've downloaded de linuxant driver and applied the patch to get the full 56Kbps speed, but it alerts me that I should change the init string from 'AT&F' to 'AT&F23+MS=V90,1,28800,33600,28800,56000'.
I don't know how to do this, I use the "default" network option under the 'system->admin' menu to connect, because when I use the gnome-ppp program (adding a new init modem register with the string which I have previously said), it tries to connect and then reports a "carrier not found message", so it can't connect, only being able to connect at 14.4Kbps with the default network management.
So... could someone tell me how to add that init string?
Thanks.

---

