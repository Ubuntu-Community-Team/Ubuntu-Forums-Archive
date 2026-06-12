---
title: "Upgrade wireless problem"
date: 2008-04-25
forum: Networking &amp; Wireless
---

### Post by amazoohwawa on 2008-04-25
typed dmesg in terminal and and got a long script near the end of which it says:

Radio frequency Kill Switch is On:
Kill radio switch must be off for wireless networking to work.


The questions i have is: how do you turn of the kill switch???:confused:

---

### Post by chili555 on 2008-04-25
On your laptop, there is a physical switch or a key combination, Fn+F5 perhaps, that turns the wireless on and off. Turning the wireless off saves battery power if you are playing solitaire in the airport. dmesg is telling you that wireless is not able to run as long as the wireless card is physically switched off.

Sometimes the key combinations work perfectly, and sometimes they can be difficult. Post back if the problem persists.[IMG]http://www.thinkwiki.org/images/3/37/Wireless-switch.png[/IMG]

---

### Post by amazoohwawa on 2008-04-25
thanks,, but i did try both the combination and the physical key and nothing is happening:mad: i must say that i am truly shocked & disappointed that such problems exist and that no one seems to be able to help solve this problem. Wasn't this noticed when bata testing????

---

### Post by chili555 on 2008-04-25
Which wireless card? Some drivers, iwl3945 for example, work perfectly, but the LED doesn't light. It therefor appears the wireless is not working, but it is.

Open a terminal and do:```
sudo tail -f /var/log/messages
```See if the key combination gives any messages.

---

### Post by johnn1949 on 2008-04-26
I think the wireless kill switch  is part of your computer. Check the documentation in the owners manual.  My Dell says fn-f2turns the wireless card on/off.

---

### Post by Gmonster on 2008-04-26
Hi,
Ever since I upgraded to 8.04 my linksys WPC11 ver3 wifi doesn't work.  My ethernet cable does and my cellular EVDO card works, but not lynksys.  It worked fine before the upgrade on the previous OS.

When I ran this command:

sudo tail -f /var/log/messages

This is what I got (see attached).  Please advise.

---

