---
title: "Help with Wireless 2200BG"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by Nicarlo on 2006-09-02
Hi all,

I have just installed a fresh version of ubuntu 6.06 and i am having alot of problems with my wireless internet.

I have a Dell Inspiron 6000 with the Intel Pro Wireless 2200BG card.

It sees my Network SSID but when i insert the WEP key and press ok it tries to connect for about a minute and then stops and i dont get connected. Ive checked the forums and although there were a few  that had problems i was not able to find a solution. If someone could tell me or point me to a thread in which this problem was resolved i would be extremly grateful. I really would like to enjoy Ubuntu in all areas of my home :)

Thanks all

---

### Post by Linuturk on 2006-09-03
I'm having the same problem.

I'm using a Toshiba Satellite R15-S822 with the Intel 2200BG chipset.

I can connect to unsecured networks just fine, but when I tried a simple 64-bit WEP key, my system won't connect to the network.

Quick side note, I'm using Network Manager as installed by Automatix.

---

### Post by Nicarlo on 2006-09-03
> **Linuturk said:**
> I'm having the same problem.

I'm using a Toshiba Satellite R15-S822 with the Intel 2200BG chipset.

I can connect to unsecured networks just fine, but when I tried a simple 64-bit WEP key, my system won't connect to the network.

Quick side note, I'm using Network Manager as installed by Automatix.



im not totaly sure exacly what i did but i deactivated my wireless internet and then reactivated it and for some weird reason it just started working and its been working since. Weird how this works.

---

### Post by fohfoh on 2006-09-03
i also have a dell inspiron 6000. my wireless was working before; but after i turned off the laptop one time, the wireless no longer works. i can connect to the router no problem, but nothing is transferred. so internet basically doesnt work.

---

### Post by Nicarlo on 2006-09-03
try to diactive both eth0 and eth1 and then activate eth1 (wireless adapater)

i think thats how i got mine working

---

### Post by schaefer on 2006-09-23
I was having the same problems, but found a solution. What you want to do is hold down the Fn key and press F2. This turns on your wireless connection, and allows you to enter secure networks. I hope this solves your problem.

---

