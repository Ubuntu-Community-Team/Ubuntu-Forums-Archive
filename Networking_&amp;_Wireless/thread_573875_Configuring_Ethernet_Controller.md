---
title: "Configuring Ethernet Controller"
date: 2007-10-12
forum: Networking &amp; Wireless
---

### Post by Michl on 2007-10-12
I dual boot and had trouble connecting to the internet via LAN
in both W2K and edgy, but now got windows to connect but
am still having trouble.  What made the difference in Win2k was
changing the media type in the advanced window for configuring
the ethernet controller.  There is a choice there between
100Base Tx
10Base Tx
auto
Hardware control

and changing this to 10Base Tx solved my problems in windows.
Ubuntu under networking does not give me this option.  Where do
I do this?

For what it is worth, I need to use a static ip address and DNS
servers.  I've got this set-up exactly the same in both OS.

Michael

---

### Post by Michl on 2007-10-12
ethtools does it.  It is not totally transparent but with
trial and error and the man you can figure out how
to configure the device.  ethtools does not need to
be downloaded in edgy but comes with the distribution.

Michl

---

