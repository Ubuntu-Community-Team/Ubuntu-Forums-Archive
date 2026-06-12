---
title: "ser2net"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by kaktustopol on 2008-03-13
Hi,
has anyone been using ser2net application? I can't find good tutorials or explanations on how it works. 
I was wondering if you can only read data from serial port or if you can also write to it?

Thanks a lot

---

### Post by digitaldreams on 2008-04-15
You can read/write from/to the serial port via TCP socket and be able to use also the telnet protocol (other thant raw format) to send/receive ascii and/or binary data to/from the serial port. Currently the startup script (/etc/init.d/ser2net) doesn't seems to work as expected and I have to start/stop the daemon by hand (./ser2net, killall ser2net).

---

