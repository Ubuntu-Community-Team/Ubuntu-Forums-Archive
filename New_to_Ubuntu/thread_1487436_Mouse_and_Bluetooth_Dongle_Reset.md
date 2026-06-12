---
title: "Mouse and Bluetooth Dongle Reset"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by kid1000002000 on 2010-05-19
I have been sifting through threads for months to try and get this to work, but am finally giving up and just asking in hopes somebody can help me with this.

When I resume my laptop from suspend, I can not get my bluetooth mouse to connect.  I have a USB Bluetooth dongle, and always have to click a bunch of enable buttons from the bluetooth icon in the notification area, pull out my dongle, plug it back in, delete my mouse profile, and 'connect a new device' to get my mouse to work properly.

If I don't do all of these steps, sometimes the mouse will work for like a minute (or just not work at all) but then die on me.  Following these steps keeps the mouse connected indefinitely.

Can I get this to happen automatically?

Please Help!!!!

Edit:  Now its not staying connected indefinately.

---

### Post by kid1000002000 on 2010-05-20
bump [thread]

---

### Post by tgalati4 on 2010-05-20
Put the mouse bluetooth drivers in the reload section of the file:

/etc/default/acpi-support

---

### Post by kid1000002000 on 2010-05-24
that could solve part of the problem.  My mouse has now decided lately to stop working in the middle of sessions too now, so the whole issue is not solved.   Grr.

It seems as if your suggestion will solve the resume from suspend issue but not the middle of my session thing that the problem has now graduated too.  Now, my mouse just dies in the middle of my session.

Ideas?
If not, any ideas on how to reconnect usb devices to my computer via the terminal?  That would at least make it so I don't have to reach over and unplug the dongle every time.

---

### Post by kid1000002000 on 2010-05-28
bump!

---

### Post by kid1000002000 on 2010-06-06
bump

---

### Post by nushoin on 2011-11-07
Try this in a terminal window (or press Alt-F2 then type that):

```
sudo /etc/init.d/bluetooth restart
```

---

