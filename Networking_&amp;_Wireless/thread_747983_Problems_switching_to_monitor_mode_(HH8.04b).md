---
title: "Problems switching to monitor mode (HH8.04b)"
date: 2008-04-07
forum: Networking &amp; Wireless
---

### Post by msjones on 2008-04-07
[FONT="Arial"]Hi,

I Have an intel 3945 wireless card in my laptop.

I am trying to switch this card to monitor mode with the following command:

**sudo iwconfig wlan0 mode monitor**

And iI keep getting back the following error:
[B]
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Device or resource busy[/B].[/FONT]

Can anybody help me? I have tried rebooting and this does not help. I am not using the card, I am connected with LAN.

I am using the latest 8.04LTS beta.

Thanks

---

### Post by msjones on 2008-04-07
Sorted!

Just needed to disable the wireless card and change the mode.

---

