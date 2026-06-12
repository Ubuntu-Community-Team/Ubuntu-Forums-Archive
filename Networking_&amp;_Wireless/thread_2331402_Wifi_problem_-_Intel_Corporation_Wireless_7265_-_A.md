---
title: "Wifi problem - Intel Corporation Wireless 7265 - Asus k501u"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by lortdc on 2016-07-21
Installed Ubuntu 16.04 alongside windows 10, wifi works in windows 10 but not in ubuntu. rfkill list shows that the wireless LAN is hard block: yes, tried unblocking it but still nothing. This is the wireless info: [ATTACH]270262[/ATTACH]
Can somebody please help me? Thank you. :)

---

### Post by jeremy31 on 2016-07-21
Welcome to the forums

Please use the default font and size

Try ```
echo "options asus_nb_wmi wapf=4" | sudo tee /etc/modprobe.d/asus_nb_wmi.conf
```
Reboot

---

### Post by lortdc on 2016-07-22
It worked! Thank you very much!

---

