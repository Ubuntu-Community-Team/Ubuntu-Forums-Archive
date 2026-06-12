---
title: "Ndiswrapper wlan0 is being reset"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by ArgyBargy on 2008-06-11
I have installed a wifi card on my laptop. Using ndiswrapper it works but only for a short period of time. After a few minutes the connection is lost and the card starts to reset itself. Dmesg shows the following:
ndiswrapper (mp_reset:62): wlan0 is being reset
ndiswrapper (mp_reset:62): wlan0 is being reset
....and so on.

Is there some way I can see if there is a conflicting driver or something that would cause this problem?

This maybe a clue to what is causing the problem but I´m not sure. When I power on for the first time the wifi will work for something between 1 to 5 minutes. Now if i reset, it still doesn´t work. However if I power down the laptop and remove the battery and power cable (to completly reset it) the wifi works but again only for a few minutes.

Here is a bit of info from the system. 

Op. System: XUbuntu 8.04
wireless card: Encore ENPWI-G2
Driver: net8185 via ndiswrapper

Is there something else I can give to help find out the problem?

thanks

---

