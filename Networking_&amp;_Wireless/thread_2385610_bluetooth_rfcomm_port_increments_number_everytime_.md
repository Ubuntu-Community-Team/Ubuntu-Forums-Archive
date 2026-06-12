---
title: "bluetooth rfcomm port increments number everytime the same bluetooth device is connec"
date: 2018-02-22
forum: Networking &amp; Wireless
---

### Post by shome on 2018-02-22
[COLOR=#111111][FONT=Ubuntu]I connect my Bluetooth device(HC05) to my laptop using blueman-manager. The device is set as trusted and I connect using the option "connect to serial port". Every-time I connect it connects it to new port number which is 1 more than the previous one. That is first time when I connect it connects to rfcomm0, then next time to rfcomm1, then to rfcomm2, so on and so forth. If I reboot my computer it starts from rfcomm0 again. 

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have tried to restart the bluetooth using: sudo systemctl restart bluetooth.service.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]But the number of rfcomm didnt reset to zero.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I am using ubuntu 16.04 on dell studio laptop with Dell wireless 365 bluetooth module.
 
[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]How do I solve this?[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR]

---

