---
title: "Compaq B1900 : Wireless not Working"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by anij on 2008-04-25
Hello all,
I have a Compaq B1900 laptop PC. I just installed 8.04
I have been trying for the past 3 generations of Ubuntu but wireless is not working. I am really desperate.
This way around the situation is slightly better. When I type lspci command I see that the OS detects the card and it also says that it has found it. It says that I have a Broadcomm BCM4312 802.11/a/b/g card. But then when I switch on the wireless modem and do a iwlist scan it does not find any signal. I then installed Wifi Radar and then configured it to detect a wireless connection with my SSID and still it shows that it is not getting any signal. Note at at the same places I have a signal strength of Excellent when using Windows XP.
I would really, really appreciate any help.
Internet using a Ethernet cable is working.
Similarly no sound but I will post this problem on another problem.
If anyone has any idea how to resolve this problem I would be very grateful to her/him.

---

### Post by Tim Sharitt on 2008-04-25
The Broadcom driver need additional firmware to work. I a terminal type
```
sudo apt-get install b43-fwcutter
```
After you do this, got to System > Administration > Hardware Drivers and make sure Broadcom 43 wireless driver is enabled. Reboot and it should work.

---

### Post by anij on 2008-04-25
> **Tim Sharitt said:**
> The Broadcom driver need additional firmware to work. I a terminal type
```
sudo apt-get install b43-fwcutter
```
After you do this, got to System > Administration > Hardware Drivers and make sure Broadcom 43 wireless driver is enabled. Reboot and it should work.

Worked like magic. Thank you very much.

---

