---
title: "how to configure static ip address"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by SanRaje on 2008-01-28
hi friends.
   when i am installing ubuntu desktop 7.10. that's time my pc's  wireless card automatically taking wireless router default getway. that's  time internet is working. this taking dynamically ip address. but when i am configuring statically my wireles card that time it doesn't work.u tell how to configure static ip adddress. tell step by step.

thank's

---

### Post by NullHead on 2008-01-29
I use a program called "wicd" it will static you're ipaddress if you specify it to do so.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by hahahan on 2008-01-29
For me using Menu>System>Administration>Network works too.
Disable roaming mode, enter your static data, close the dialog box and check the DNS tab for a decent nameserver, since you don't use DCHP you w'll have to enter it manually.

Hope it's help you, regards .

---

### Post by wieman01 on 2008-01-29
> **SanRaje said:**
> hi friends.
   when i am installing ubuntu desktop 7.10. that's time my pc's  wireless card automatically taking wireless router default getway. that's  time internet is working. this taking dynamically ip address. but when i am configuring statically my wireles card that time it doesn't work.u tell how to configure static ip adddress. tell step by step.

thank's
If you happen to use Network Manager, then you cannot use Static IP Addresses as it does not support them (yet). 

If you want to go for a manual wireless connection (possibly WPA secured), then take a look at my tutorial (signature "WPA"), it explains how to set them up.

Let me know if you have more questions.

---

### Post by hahahan on 2008-01-29
Wieman101,

I don't see any problems using Menu>System>Admin...etc to configure a nic static.
I'm running 7.10 and it works fine for me.
What do you mean by Network Manager, the gnome tool or an other installed network tool?

Regards.

---

### Post by wieman01 on 2008-01-29
> **hahahan said:**
> Wieman101,

I don't see any problems using Menu>System>Admin...etc to configure a nic static.
I'm running 7.10 and it works fine for me.
What do you mean by Network Manager, the gnome tool or an other installed network tool?

Regards.
You're right, let me elaborate. The standard Gnome networking tool does support the use of static IP addresses, however, it's functionality with regard to wireless security is limited to WEP. WPA is not supported.

So that's why most people revert to using Network Manager, which is an enhanced networking tool that supports WPA and other security protocols. So in fact you have two options.

I don't encourage people to use WEP, so naturally I suggest that they use Network Manager as their default networking application. And the latter - I am afraid - does not support static IP addresses. Sorry for the confusion, I should have made that clear in the first place.

So, SanRaje, what tool do you use?

---

### Post by hahahan on 2008-01-29
Tx Wieman101,

That makes things clear for me, I din't understand why so many fooks use a Networkmanager, now I do. I have a poorman's router (No WPA(2) :( , so the gnome tool is just fine for me, I add "restricted" manualy in /etc/network/interfaces.

---

### Post by wieman01 on 2008-01-29
> **hahahan said:**
> Tx Wieman101,

That makes things clear for me, I din't understand why so many fooks use a Networkmanager, now I do. I have a poorman's router (No WPA(2) :( , so the gnome tool is just fine for me, I add "restricted" manualy in /etc/network/interfaces.
Got it. :-)

Just a side note... WEP is higly vulnerable while it can be easily cracked in a matter of minutes. Of course I am not saying you should replace your router, but maybe there is a firmware upgrade available that would add extra security feature such as WPA.

---

### Post by hahahan on 2008-01-29
Tx Wieman101,

I'm aware of that, I can crack the key within minutes, the SKA option only slows down the hack a little and makes it fairly impossible without a client connected.
I indeed found a firmware upgrade but it's not clear that it supports wpa-suppliant. I can imagine it needs more hardware. A was anxious to flash it for probbably very little improvement, when it fails for some reason the router is broke for ever.
The router is Sitecom WL 521-R, current firmware Version 1.0 Release 25. Do you have a clue?

---

### Post by wieman01 on 2008-01-29
> **hahahan said:**
> Tx Wieman101,

I'm aware of that, I can crack the key within minutes, the SKA option only slows down the hack a little and makes it fairly impossible without a client connected.
I indeed found a firmware upgrade but it's not clear that it supports wpa-suppliant. I can imagine it needs more hardware. A was anxious to flash it for probbably very little improvement, when it fails for some reason the router is broke for ever.
The router is Sitecom WL 521-R, current firmware Version 1.0 Release 25. Do you have a clue?
Very little to be frank. I don't really know the model, so I can give little advice. Usually firmware upgrades are not very problematic, I would give it a go. Since WPA2/WPA is an standardized security protocol, wpa-supplicant should by all means be able to cope with it. Whether your wireless adapter supports it (i.e. WPA/WPA2) is another story though. But I don't want to hijack this thread and go into detail, if you are interested, send me a message by PM and we continue from there. :-)

---

