---
title: "ltmodem driver problems"
date: 2005-01-02
forum: Networking &amp; Wireless
---

### Post by dman on 2005-01-02
I've tried installing the Lucent Winmodem driver from the source found at ltmodem.hedy.de, version 8.31a10. I did ./build_module, ./ltinst2, ./autoload to install the driver.

However, when I go to activate by connection in gnome-ppp, the tick by my connection disappears after a second. No modem sounds whatsoever.

When i run wvdial in a terminal, I get "--> Cannot open /dev/modem: No such device or address." I go to /dev/ and find both modem and ttyLT0 are present.

I also found that lt_serial and lt_modem weren't in their correct places. They were in /lib/modules/2.6.8.1/extra and not 2.6.8.1-3-386/extra. I moved the files over to their correct place. 

The modem still doesn't work. So I tried modprobing the drivers
```
root@ubuntu:/home/dman # modprobe lt_serial
WARNING: Error inserting lt_modem (/lib/modules/2.6.8.1-3-386/ltmodem/lt_modem.ko): Invalid module format
FATAL: Error inserting lt_serial (/lib/modules/2.6.8.1-3-386/ltmodem/lt_serial.ko): Invalid module format
```
This is what I get.

What I can do to fix this?
The info I found in google and the forum search didn't work for me.

---

