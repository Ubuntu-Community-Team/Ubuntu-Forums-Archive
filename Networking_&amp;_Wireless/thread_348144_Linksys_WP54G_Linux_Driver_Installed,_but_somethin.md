---
title: "Linksys WP54G Linux Driver Installed, but something is missing"
date: 2007-01-28
forum: Networking &amp; Wireless
---

### Post by Jim Rogers on 2007-01-28
I downloaded the linux drivers from [http://www.ralinktech.com/ralink/Home/Support/Linux.html](http://www.ralinktech.com/ralink/Home/Support/Linux.html)
I compiled the source although do not think it was necessary as the .bin files were there.
I move the .bin files and the RT61STA.dat file to /etc/Wireless/RT61STA.
I then entered RT61STA and using nano -w modified the .dat for my environment which at present has no encryption enabled
The make indicated the drivers had been installed
(System reboot)
chedked everything again
Two things happened that are obvious to me:
lshw no longer shows the hardware as "UNCLAIMED"
iwlist ra0 scan finds 4 cells:
  cell 01 Address 00:14:BF:E9:60:BF
  ESSID "W4ATK"
  Mode: managed
  EncryptionKey: off
  BitRate:0 kb/s
  
  cell 03 and 04 have encryption enabled

  cell 04 ADDRESS 00:0F:B5:26:60:4E
  ESSOD "NETGEAR"
  Mode: managed
  Channel: 11
  EncryptionKey:off
  BirRate: 149 Mb/s

From this I gather the device is up and running. However Firefox still is not able to find my isp server when I type "http://www.bellsouth.net" into the address line.
I know I am missing something here. Any help would be appreciated.

---

### Post by Jim Rogers on 2007-01-28
Hallelujha!!!!

OK... The driver from ralink works well. The missing component was dhclient. As soon as I ran that.... linkup and Firefox works.

My goodness, only took 7 days to do what should have been able to do in 30 minutes, but it is a learning process is it not.?

Off to the books to find how to execute dhclient on boot. 

This thread is done!!!

---

### Post by TheWizzard on 2007-01-28
congratulations! 
please mark your tread as "solved" or something like that. may help others with similar problems.

---

### Post by Jim Rogers on 2007-01-29
SOLVED ---

Thanks to inCursorated for his solution shown below. 

Using "sudo nano -w /etc/network/interfaces"

add:
        auto ra0
        iface ra0 inet dhcp

SOLVED ...

---

