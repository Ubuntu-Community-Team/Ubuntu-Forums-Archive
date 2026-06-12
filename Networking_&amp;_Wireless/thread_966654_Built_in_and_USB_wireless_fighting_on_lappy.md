---
title: "Built in and USB wireless fighting on lappy"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by FreewheelinFrank on 2008-11-01
I have a built-in wireless widget on my laptop- which is useless- and a USB dongle which can actually pick up a signal from the router in the next room. 

On Intrepid they seem to fight occasionally: first the built-in wotsit tries to connect, then the plug-in, with two prompts for passwords. In the end Network manager says connected, but then drops the connection (and occasionally crashes.) I can disable the built-in wireless dubree from Windows, which was fine in Hardy, but in Intrepid this results in 'Enable Wireless' being greyed out.

When wireless is working OK, there's a dot in only the USB button in Network Manager. When built-in and USB are fighting, there's a dot in both buttons.

Is there any way to ensure Network Manager doesn't try to connect using the built-in wireless card? (At least not at the same time as the USB dongle.)

Many thanks.

---

### Post by FreewheelinFrank on 2008-11-02
It happened again.

The signal strength indicator on the built-in wireless card seems to be flaky: although the laptop doesn't move, the signal strength sometimes rises to 100%, and Network Manager tries to connect via the wireless card rather than (or at the same time as?) via the USB dongle.

Result: No connection at all.

Is there any way to stop Network Manager trying to use the built-in wireless card?

Attaching images is not working at the moment but I'll post some screenshots later.

---

### Post by FreewheelinFrank on 2008-11-02
Anybody?

---

### Post by neu2buntu on 2008-11-05
peter09,s method worked perfect...  i used     lsmod    in terminal to find name of driver then blacklisted as he said...i was having the same prob as you

---

### Post by FreewheelinFrank on 2008-11-05
I found a work-around to this problem here, courtesy of Peter09:

[http://ubuntuforums.org/showpost.php?p=6112316&postcount=15](http://ubuntuforums.org/showpost.php?p=6112316&postcount=15)

---

### Post by FreewheelinFrank on 2008-11-05
> **chrissy.mc.1@hotmail.co.u said:**
> peter09,s method worked perfect...  i used     lsmod    in terminal to find name of driver then blacklisted as he said...i was having the same prob as you

Thanks for posting!

---

