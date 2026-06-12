---
title: "ndiswrapper invalid drivers msg - help!"
date: 2005-07-13
forum: Networking &amp; Wireless
---

### Post by bcashman on 2005-07-13
Hi all. I have a toshiba satellite A65, running 5.04, and can't get either of my wirless devices to work. I have a netgeat wg111v2 usb and a D-Link dwlg630 pcmcia card. I followed the directions in the setup ndiswrapperhowto in the ubuntu wiki and (ndiswrapper v1.2) everything seems fine until i install the drivers. when I do a ndiswrapper -l it shows the driver name (mrv8ka51, and netwg111) followed by invalid driver on each. I have no lights on either device. 'lsusb' detects the wg111 by name, 'lspci' shows unknow device in the pci bridge slot 14.4. Im a Noob to linux, and i have read all the info i could find but there is nothing about invalid drivers. Thanks in advance.

---

### Post by bcashman on 2005-07-13
I think I resolved the invalid driver problem. It was operator error with syntax. There is still a problem with the d-link card. the system is not seeing the card at all. the driver is loaded, but there is no device present msg. The netgear usb stick is blinking as it should be and shows up fine. Will test the connection at home.

---

