---
title: "Wireless Kubuntu LAMP"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by rconsol on 2006-10-22
Hi Folks,
  I am really frustrated - 2 weeks now and can NOT get my wireless DLink setup to work on Ubuntu LAMP server.
  I have a tri-boot setup, Win2K, Kubuntu, Ubuntu LAMP server.  Both Ubuntus are Dapper Drake - 6.06.1.  Installed Kubuntu and had to use one of the Network GUI tools to add the wireless key and all is working well.
  After trying about everything I could gleen from various forums I am about to give.  My last attempt (I "assumed" a brain storm) was to replicate the /etc/network/interfaces from the working Kubuntu to the Unbuntu server.  No luck.
  What is the difference between K and LAMP - other than the obbvious desktop - something else in the network arena must be different too.
  Is there some reason NOT to just install the Apache/MySql/PHP onto Kubuntu and just give up the LAMP server?
  All I want to is sunset my Win2K and have an inhouse server with an SQL database.
                  Cheers ...................... RonC

---

### Post by az on 2006-10-22
What chipset is the device?

As well, try installing the linux-386 kernel.  Maybe it's a server-kernel-that-does-not-play-well-with-desktop-hardware issue.

sudo apt-get install linux-386


Your server will be slightly less optimised, running the desktop kernel, but everything will work.

---

### Post by rconsol on 2006-10-24
Hi,
  Sorry for the delayed response but it is election season and I am an "early vote" poll worker.
  
  The card is a DLink DWL-G520 with the Atheros chipset.

  There still must be some non-desktop setup differences bewteen K and LAMP.  I also noticed that the K setup does not have a wpa_supplicant.conf - which I "assumed" to be the LAMP server problem.
           Cheers .............. RonC

---

