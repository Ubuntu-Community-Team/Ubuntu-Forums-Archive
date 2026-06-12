---
title: "Dapper not finding newly installed external modem"
date: 2007-01-19
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-01-19
I have a external modem (Creative 56K) attached to the 9-pin connector on the back of the computer. The bios is autodetect for that channel. 

The modem is NOT being detected at boot. Help, please.

---

### Post by koenn on 2007-01-19
dial-up modems on a serial port (that 9pin connector) don't need to be "detected". Programs that need to use the modem just send ther output to the serial port, and whatever's on the other side of the cable will accept it. In this case : the modem will receive the data and use the telephone line to transmit them to whoever you're calling (your ISP ?)

you probably want something like wvdial to dialup to your ISP ? here's some info. It's not specific to Ubuntu so maybe you also have to look around for ubuntu-specific info.
[http://support.real-time.com/linux/dialup/wvdial.html](http://support.real-time.com/linux/dialup/wvdial.html)

---

