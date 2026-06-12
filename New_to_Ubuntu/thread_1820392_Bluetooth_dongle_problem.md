---
title: "Bluetooth dongle problem"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by mysticway on 2011-08-07
I can't turn on my bluetooth dongle on Ubuntu Natty. When I plug it in the applet is marked red, when I press "Turn bluetooth on" nothing changes . To make it work I have to connect/disconnect  bluetooth dongle manually many times untill the red icon on the applet disappears! What does it mean? How can I solve it?

---

### Post by LowSky on 2011-08-07
simple fix... open the program terminal

type this command

```
sudo service bluetooth restart
```

---

### Post by mysticway on 2011-08-08
> **LowSky said:**
> simple fix... open the program terminal

type this command

```
sudo service bluetooth restart
```



Not so simple... I tried it but had no effect. After this command applet is permanently red. It seems that my laptop can't turn bluetooth on. If applet is normal and I click "Turn BT off" I can't turn it on again untill reboot or manual unplug. I tried a lot of methods described on the forums but :(:(:(

---

