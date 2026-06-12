---
title: "Wifi disconnect"
date: 2018-05-11
forum: Networking &amp; Wireless
---

### Post by my.tom on 2018-05-11
Hello everyone, i just installed ubuntu 18.04. Everything look good except sometime wifi will be disconect. So i run command:

Sudo iw reg get
Sudo iw reg set JP (im living in japan)
Sudo gedit /etc/default/crda

And edit REGDOMAIN=JP

Everything look fine until now. After connected 6 hours, wifi was disconnect. I try run command iw again and found my country automatically changed to some other one like 00 or 98.

I runned command again and again but still change. What should i do? Some one can help me?

my wifi's info:
[http://paste.ubuntu.com/p/Cn8524377m/](http://paste.ubuntu.com/p/Cn8524377m/)
[ATTACH]279701[/ATTACH]

please help me

---

### Post by praseodym on 2018-05-11
Please run the wireless script from the sticky thread and show the outputs

---

### Post by my.tom on 2018-05-15
i was update the information. please help me

---

### Post by praseodym on 2018-05-15
Change the encryption mode in your router to WPA2-AES (CCMP), not mixed mode WPA/WPA2

---

### Post by my.tom on 2018-05-15
i am using wimax 2+ au
[http://internet-kyokasho.com/wp-content/uploads/2016/03/au-WiMAX-eye-catch-768x412.png](http://internet-kyokasho.com/wp-content/uploads/2016/03/au-WiMAX-eye-catch-768x412.png)

here is my security seting
[https://imgur.com/a/ZhnxhMi](https://imgur.com/a/ZhnxhMi)

my lan setting -> security setting -> encryption just have AES-TKIP & AES, confirmation is WPA/WPA2-PSK
so i change encryption to AES
Its ok?

---

