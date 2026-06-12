---
title: "Problems with wireless driver"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by T-Grave on 2008-08-23
Hi,

So I'm working with an old Toshiba L10-144 which has an InProComm IPN 2220 Wireless chipset on the pci wireless card.

Since there is no linux driver for it and it's not supported out of the box, I had to use ndiswrapper and the most recent driver that I found on the toshiba website.

And it all went fine, I can pick up networks, connect to them ... but only when they aren't protected.

WPA or WPA2 doesn't work, it just won't connect or if it does, it's extremely unstable and not working at all.

When I use wpa_supplicant it constantly connects and disconnects, except from the output that wpa_supplicant gave me I can also verify that with the command "iwconfig" which gives 5 sec a 54mbit speed and then a second or 2 a 1mbit, and it keeps changing between those two...

I would give you some outputs, but I'm not where my laptop is atm.

Thanks in advance,

T-Grave

---

### Post by Sam Lars on 2008-08-23
I'd be interested in seeing syslog output when you try to connect with Ndiswrapper.
Same with wpa-supplicant.  Does it actually connect and disconnect, and you can verify that it's dropping the connection?

---

