---
title: "T61 pcmcia modem problem"
date: 2007-11-09
forum: Networking &amp; Wireless
---

### Post by sierra_bravo on 2007-11-09
Hi
I've just moved from FC3 to Gutsy, and one of the problems I have is that my old faithful Sierra Aircard 555 that was working fine in FC3 is not being detected. I have installed all the files according to the instructions at [http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=310](http://www.sierrawireless.com/faq/ShowFAQ.aspx?ID=310), and I have come up to the point where cardctl gives the following output:

root@Mola-mola:~# cardctl info
PRODID_1="Sierra Wireless"
PRODID_2="AirCard 555"
PRODID_3="A555"
PRODID_4="Rev 1"
MANFID=0192,a555
FUNCID=6

Dmesg output
[  141.824000] pccard: PCMCIA card inserted into slot 0
[  141.824000] cs: memory probe 0xf8300000-0xfbffffff: excluding 0xf8300000-0xf86cffff 0xf8e70000-0xf923ffff 0xf9db0000-0xfa17ffff 0xfacf0000-0xfb0bffff
[  141.828000] pcmcia: registering new device pcmcia0.0

Nothing shows up in lspci

However, according to the documentation above, the computer should beep when the card is inserted (doesn't beep), and the device should appear as /dev/modem (doesn't). 

Any suggestions would be appreciated. TIA.


sb

---

