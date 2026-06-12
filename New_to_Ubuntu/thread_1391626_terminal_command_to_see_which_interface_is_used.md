---
title: "terminal command to see which interface is used"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by ja660k on 2010-01-27
hey guys, 

okay... im writing a networking category for conky, and i need a terminal command to say yes or no if wlan0 is connected.. or eth0 is connected.

i know that conky has if_up but that only works if the interface is up( not disconnected)

does anyone know a terminal command to do this for me?
thanks alot

---

### Post by diesch on 2010-01-27
```

IFACE="eth0"
if ifconfig|grep -q "^$IFACE"; then
 echo yes
else
 echo no
fi
```

---

### Post by ja660k on 2010-01-27
yeah, that didnt work :(

i always have eth0 up even though the cable isnt plugged in...

---

