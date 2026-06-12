---
title: "Bluetooth speaker problem - Lubuntu"
date: 2017-12-11
forum: Networking &amp; Wireless
---

### Post by aubreybourke on 2017-12-11
Hi

I'm running Lubuntu.
I can discover and pair my bluetooth speaker. However, I cannot connect to it. Or see any sign of it in the pulse audio mixer.



Can anyone help?

---

### Post by jeremy31 on 2017-12-11
Check
```
pactl list short | grep blue
```
For module-bluetooth-discover, if it isn't listed
```
pactl load-module module-bluetooth-discover
```
Then see if you can connect and use the speaker.  Also post results for 
```
lsusb; dmesg | egrep -i 'blue|firm'
```

---

