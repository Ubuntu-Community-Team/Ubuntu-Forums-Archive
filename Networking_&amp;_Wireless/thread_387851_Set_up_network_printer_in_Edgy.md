---
title: "Set up network printer in Edgy"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by leupi on 2007-03-18
I have a desktop and a laptop and both are running Edgy. The desktop has a HP 6110 AIO printer attached via USB and I went to 'Printer Setting' > 'Print Server' > 'Share Printers on local network'. I then went to the laptop and went to 'Printer Setting' > 'Print Server' > Access Printers on local network'. I then went to 'Add Printer' and tried to add a 'Network Printer (TCP)'. After hitting next I had to fill out the Printer Address (I used the address of the desktop, 192.168.0.3) and the port, 631. When I hit scan, nothing was found. I then went to settings and found that the default subnetwork was 127.0.0.*. I changed it to 192.168.0.* and tried again. When I tried to rescan I got:
> You are about to scan a subnet (192.168.0.*) that does not correspond to the current subnet of this computer (127.0.0.*). Do you want to scan the specified subnet anyway?
I scanned anyway and it found nothing. Any ideas as to what I am doing wrong?

Thanks,
Todd

---

### Post by Floppyjoe on 2007-03-18
> **leupi said:**
> I have a desktop and a laptop and both are running Edgy. The desktop has a HP 6110 AIO printer attached via USB and I went to 'Printer Setting' > 'Print Server' > 'Share Printers on local network'. I then went to the laptop and went to 'Printer Setting' > 'Print Server' > Access Printers on local network'. I then went to 'Add Printer' and tried to add a 'Network Printer (TCP)'. After hitting next I had to fill out the Printer Address (I used the address of the desktop, 192.168.0.3) and the port, 631. When I hit scan, nothing was found. I then went to settings and found that the default subnetwork was 127.0.0.*. I changed it to 192.168.0.* and tried again. When I tried to rescan I got:

I scanned anyway and it found nothing. Any ideas as to what I am doing wrong?

Thanks,
Todd

Your printer address should look like this:
```
http://192.168.0.3:631/printers/PrinterName
```

---

### Post by leupi on 2007-03-26
Sorry for the delayed response. I tried what you said; however, I am getting the same result.  For printer address I tried each of the following:

[http://192.168.0.3:631/printers/hp6110](http://192.168.0.3:631/printers/hp6110)
192.168.0.3:631/printers/hp6110

For Port, I used:

631

Any other ideas?

Thanks for your help,
Todd

---

