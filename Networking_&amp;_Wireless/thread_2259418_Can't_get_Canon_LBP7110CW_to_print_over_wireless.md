---
title: "Can't get Canon LBP7110CW to print over wireless"
date: 2015-01-04
forum: Networking &amp; Wireless
---

### Post by jnorris2 on 2015-01-04
I've got this Canon ImageClass printer, it works fine over the network from my Mac, but I can't get it to do anything from Ubuntu 14.04.

I installed the driver from Canon's website and then tried the various options (HP Jetdirect, DNS, etc) provided by default. When I did that, the test pages never print, although they seem to leave the print queue. I then tried installing the "cups-backend-bjnp" which some had said was needed for Canon wireless printing.... I installed the printer using that new "Canon network printer" option, as bjnp://printer-IP:8611, and that had the same result as the first attempts. I'm now at a loss of what to do... the only thing I know to try now is to share the printer from my Mac and connect that way. Any ideas?

---

### Post by jeremy31 on 2015-01-04
[http://localhost:631/admin](http://localhost:631/admin)
And see if add printer or find printer helps

---

### Post by jnorris2 on 2015-01-04
> **jeremy31 said:**
> [http://localhost:631/admin](http://localhost:631/admin)
And see if add printer or find printer helps

If I try adding a printer that way, the print queue says this:

processing since
Sun 04 Jan 2015 11:57:52 AM CST 
*"bjnp_process_udp_command: no data received (recv)CRIT:  bjnp_process_udp_command: no data received (recv)CRIT:  bjnp_process_udp_command: no data received (recv)WARNING: recoverable:  Network host '10.10.10.39' is busy; will retry in 5 seconds..."*

One more thing, if I connect locally (USB) it prints fine...

---

### Post by jnorris2 on 2015-01-04
Well, I don't know what changed but I tried socket://IP-address:9100 and it now worked :\

---

