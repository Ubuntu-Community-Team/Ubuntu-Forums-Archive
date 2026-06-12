---
title: "Asus k53TA and Ubuntu 14.04.3, bluetooth not finding"
date: 2015-12-02
forum: Networking &amp; Wireless
---

### Post by azam4 on 2015-12-02
Asus k53TA and Ubuntu 14.04.3, bluetooth not finding , namely not working, What do you advice to do ? i installed some ***bluewho,bluez and also some drivers*** , but not working .
[ATTACH=CONFIG]265882[/ATTACH]

I couldn't find solve for this ,
[ATTACH=CONFIG]265883[/ATTACH]

---

### Post by jeremy31 on 2015-12-02
Open terminal and post the result from ```
uname -a; rfkill list all; hciconfig -a; lsusb; lsmod | grep bluetooth; dmesg | egrep -i 'blue|firm'
```

---

### Post by azam4 on 2015-12-02
Linux cyber 3.16.0-53-generic #72~14.04.1-Ubuntu SMP Fri Nov 6 18:17:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Bus 001 Device 003: ID 058f:a016 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1d57:ffa4 Xenta 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             446409  11 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
[    0.400395] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.400597] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.764977] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[   12.836561] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   12.836580] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   16.950573] Bluetooth: Core ver 2.19
[   16.950598] Bluetooth: HCI device and connection manager initialized
[   16.950606] Bluetooth: HCI socket layer initialized
[   16.950608] Bluetooth: L2CAP socket layer initialized
[   16.950619] Bluetooth: SCO socket layer initialized
[   16.957382] Bluetooth: RFCOMM TTY layer initialized
[   16.957401] Bluetooth: RFCOMM socket layer initialized
[   16.957415] Bluetooth: RFCOMM ver 1.11
[   17.107581] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.107587] Bluetooth: BNEP filters: protocol multicast
[   17.107598] Bluetooth: BNEP socket layer initialized
[  636.464322] [Firmware Bug]: battery: (dis)charge rate invalid.

[ATTACH=CONFIG]265886[/ATTACH]

---

### Post by azam4 on 2015-12-02
max@cyber:~$ uname -a; rfkill list all; hciconfig -a; lsusb; lsmod | grep bluetooth; dmesg | egrep -i 'blue|firm'
Linux cyber 3.16.0-53-generic #72~14.04.1-Ubuntu SMP Fri Nov 6 18:17:23 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
Bus 001 Device 003: ID 058f:a016 Alcor Micro Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 1d57:ffa4 Xenta 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
bluetooth             446409  11 bnep,btusb,rfcomm
6lowpan_iphc           18702  1 bluetooth
[    0.400395] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    0.400597] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[    2.764977] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x550f00)
[   12.836561] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   12.836580] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   16.950573] Bluetooth: Core ver 2.19
[   16.950598] Bluetooth: HCI device and connection manager initialized
[   16.950606] Bluetooth: HCI socket layer initialized
[   16.950608] Bluetooth: L2CAP socket layer initialized
[   16.950619] Bluetooth: SCO socket layer initialized
[   16.957382] Bluetooth: RFCOMM TTY layer initialized
[   16.957401] Bluetooth: RFCOMM socket layer initialized
[   16.957415] Bluetooth: RFCOMM ver 1.11
[   17.107581] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.107587] Bluetooth: BNEP filters: protocol multicast
[   17.107598] Bluetooth: BNEP socket layer initialized
[  636.464322] [Firmware Bug]: battery: (dis)charge rate invalid.

---

### Post by jeremy31 on 2015-12-02
How about ```
lspci -nnk | grep -iA2 net
```

---

### Post by azam4 on 2015-12-02
[ATTACH=CONFIG]265887[/ATTACH]

---

### Post by jeremy31 on 2015-12-02
Can you find the model number on the card, it should start with AR5B

---

### Post by azam4 on 2015-12-02
It's which you asked ? 
[ATTACH=CONFIG]265888[/ATTACH]

---

### Post by jeremy31 on 2015-12-02
You might find a sticker on the laptop or have to remove a cover on the bottom to find the wireless card, it should have a model number that starts with AR5B
The wifi card should be similar to
[Img]http://i.ebayimg.com/00/s/NDM1WDUwMQ==/z/sfgAAOSw9N1VzPZg/$_1.JPG[/img]

---

### Post by azam4 on 2015-12-02
[ATTACH=CONFIG]265889[/ATTACH]

---

### Post by azam4 on 2015-12-02
It can be ?

---

### Post by jeremy31 on 2015-12-02
That is just the laptop info but I did find that bluetooth was an option for that model.  I don't think your laptop has bluetooth

---

### Post by azam4 on 2015-12-03
Thanks , and what do you advice  to do? Have i to buy bluetooth output adapter ?

---

### Post by jeremy31 on 2015-12-03
> **azam4 said:**
> Thanks , and what do you advice  to do? Have i to buy bluetooth output adapter ?

Yes, the simple way would be to get an IoGear GBU521, they work fine in Ubuntu.

---

