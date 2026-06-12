---
title: "3Com 3CRWE154G72 Ndiswrapper problems!"
date: 2005-08-07
forum: Networking &amp; Wireless
---

### Post by shrimphead on 2005-08-07
Hi

Having problems setting up my 3Com Officeconnect (3CRWE154G72) revision 1 card using ndiswrapper.  I followed a guide that I found on the ubuntu forums and have blacklisted the prism54 driver.

I installed the driver successfully using ndiswrapper, ndiswrapper -l shows: 
```

Installed ndis drivers:
3c154g72        driver present, hardware present
```

and lspci shows:

```
0000:02:00.0 Network controller: 3Com Corporation 3com 3CRWE154G72 [Office Connect Wireless LAN Adapter] (rev 01)
```

Everything looks ok (I Think) but then when i do rmmod prism54 (just to be safe) and then rmmod ndiswrapper (again to be safe!  ;-) )

when I sudo modprobe ndiswrapper nothing happens and dmesg shows:

```
eth%d: ndiswrapper ethernet device 00:0e:6a:cc:1a:44
ndiswrapper: using irq 11
ndiswrapper (setup_dev:1254): unable to get mac address from driver
ndiswrapper (ndis_init_one_pci:127): Couldn't setup interface
3c154g72: probe of 0000:02:00.0 failed with error -22
```

I also noticed a thread about removing a rogue pipe in one of the ndiswrapper configuration files in /etc/ndiswrapper but I couldn't find a rogue pipe in any of the files so I left them as is.  I am running hoary using the standard 2.6.10 kernel.

thanks for any help in advance :) have been trying to get this working for ages!

on another note, this card worked flawlessly under slackware 10.1 with the prism54 module and in suse 9.2 with the prism54 module! wonder why it doesn't in hoary!

---

