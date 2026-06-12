---
title: "Network problems"
date: 2007-06-03
forum: Networking &amp; Wireless
---

### Post by mAkKoOo210 on 2007-06-03
Hi Guys, 
 I've a modem with a Conexant chipset. So I followed to guides to mount the drivers to make it work...but I still can't access to the internet:(
[http://wiki.ubuntu-it.org/Hardware/Modem/DigicomMichelangeloUsbCx?highlight=%28michelangelo%29](http://wiki.ubuntu-it.org/Hardware/Modem/DigicomMichelangeloUsbCx?highlight=%28michelangelo%29)
[http://guide.debianizzati.org/index.php/Installare_i_driver_conexant_accessrunner](http://guide.debianizzati.org/index.php/Installare_i_driver_conexant_accessrunner)
I know they're in Italian but you should understand the terminal commands.
I followed both the guides, and changed the settings, and...
when I type
> cat /proc/net/atm/cxacru\:0It seems to be all Ok, but, opening Firefox, or trying to refresh the list of application, I can't access to the internet...

then I tried to type
> tail /var/log/messagesbut I received some errors messages, to make it clear, they were NOT as these:
> Jun 3 00:07:40 localhost pppd[5101]: Plugin /usr/lib/pppd/2.4.2/pppoatm.so loaded.
Jun 3 00:07:40 localhost kernel: PPP generic driver version 2.4.2
Jun 3 00:07:40 localhost pppd[5101]: PPPoATM plugin_init
Jun 3 00:07:40 localhost pppd[5101]: PPPoATM setdevname_pppoatm - SUCCESS:8.35
Jun 3 00:07:40 localhost pppd[5126]: pppd 2.4.2 started by root, uid 0
Jun 3 00:07:40 localhost pppd[5126]: Using interface ppp0
Jun 3 00:07:40 localhost pppd[5126]: Connect: ppp0 <--> 8.35
Jun 3 00:07:43 localhost pppd[5126]: PAP authentication succeeded
Jun 3 00:07:43 localhost pppd[5126]: local IP address 82.59.0.222
Jun 3 00:07:43 localhost pppd[5126]: remote IP address 192.168.100.1
Jun 3 00:07:43 localhost pppd[5126]: primary DNS address 80.17.212.208
Jun 3 00:07:43 localhost pppd[5126]: secondary DNS address 151.99.125.1I did all the steps a number of time, but I still don't understand where I'm wrong...
Please help me

---

