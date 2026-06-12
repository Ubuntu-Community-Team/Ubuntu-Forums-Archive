---
title: "Blue tooth not connecting"
date: 2007-10-14
forum: Networking &amp; Wireless
---

### Post by polygone on 2007-10-14
I have this keyboard that will not connect via bluetooth.  It shows up as a device in the manager, but will not connect.  I get this error:


```
obex://[00:07:61:82:65:67] is not a valid location
```

It is seriously stopping me from doing anything and I think Jill is gonna kill me if I keep messing with it............

Any ideas?

---

### Post by linuxwizard on 2007-10-14
Look over this

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by polygone on 2007-10-14
Thanks man.  I should have looked there first.  It's an MX 5000 and it's not supported. Odd that it detects it, though. 

Too bad.  To bad I can't write device drivers.........  :)

---

### Post by polygone on 2007-10-14
Actually, I now have it working......


I ran:
```
sudo hidd --search
```

I saw the device, before, in the system tray blue tooth utility.  Odd.

Well, I just ran the above command and hit connect on the keyboard.

---

### Post by polygone on 2007-10-15
OK, I made a launcher to do this because I, obviously, can't type if the keyboard is not connected.  This is kind of a dumb question, but I can't for the life of me find it.  Does anyone know what folder the Bluetooth icon is in?  It's /usr/share/....

---

