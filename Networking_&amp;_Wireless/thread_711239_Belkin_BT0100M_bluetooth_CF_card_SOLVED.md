---
title: "Belkin BT0100M bluetooth CF card SOLVED"
date: 2008-02-29
forum: Networking &amp; Wireless
---

### Post by jsa13 on 2008-02-29
This card is sometimes also rebranded as a D-Link I believe.  The belkin model is F8T020 for just the CF card or F8T006-PC for the CF card w/ PCMCIA adapter.  I did not get the gnome-bluetooth icon in my notify area until I created the file "/etc/pcmcia/bluetooth.conf" with:
```

card "Belkin FT8T020dE Bluetooth CF Card"
  manfid 0x0279, 0x950b
  bind "serial_cs"

```
I found this information at Cyblogic's Bluetooth Wiki [http://www.cyblogic.com/projects/cgi-bin/trac.cgi/wiki/Bluetooth/Bluetooth_Card_Support_under_Linux]("http://www.cyblogic.com/projects/cgi-bin/trac.cgi/wiki/Bluetooth/Bluetooth_Card_Support_under_Linux").

---

