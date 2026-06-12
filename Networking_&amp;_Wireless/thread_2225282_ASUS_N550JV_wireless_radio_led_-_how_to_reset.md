---
title: "ASUS N550JV wireless radio led - how to reset?"
date: 2014-05-20
forum: Networking &amp; Wireless
---

### Post by Remten on 2014-05-20
There is an led light on the front edge of the laptop. The problem I am experiencing is that the light is ON when the wireless radio is OFF. I want to reset the light setting so that the light is only on when the radio is active.
Anyone know how to achieve that?

---

### Post by varunendra on 2014-05-21
In the Asus models I have seen so far, that light turns on with Bluetooth also. So is bluetooth on? Please show us the output of -
```
rfkill list all
```

And as a quick shot, you can try -
```
sudo rfkill block all
```
..which should turn wifi, bluetooth, led - everything 'Off'.

---

