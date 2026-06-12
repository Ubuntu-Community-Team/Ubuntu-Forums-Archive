---
title: "&quot;sudo modprobe ath5k&quot; every time I boot..."
date: 2009-06-12
forum: New to Ubuntu
---

### Post by drkameleon on 2009-06-12
Well, THIS is my issue...

Every time, I start my system, before having access to my Wireless connection, I have to type :

```
sudo modprobe ath5k
```

What could I do in order to avoid this and get it done automatically?

Thanks a lot....

---

### Post by blueridgedog on 2009-06-12
You can add this command to /etc/init.d/rc.local
```

gksudo gedit /etc/init.d/rc.local
``` 

Add the line to bottom of the file.

Or..

Add just the module to /etc/modules, using the same syntax to edit (probably the preferred way)

---

### Post by Hospadar on 2009-06-12
add a line that says ath5k to /etc/modules

---

### Post by drkameleon on 2009-06-12
Lightning-Speed... LOL

Thanks a lot guys!!!

FIXED.

---

### Post by bhall430 on 2009-06-24
i've tried the above suggestions, but every restart i have to use

modprobe -r ath5k acer_wmi

then

modprobe ath5k

then the wireless works.  any ideas?

---

### Post by 3rdalbum on 2009-06-25
> **bhall430 said:**
> i've tried the above suggestions, but every restart i have to use

modprobe -r ath5k acer_wmi

then

modprobe ath5k

then the wireless works.  any ideas?

Add acer_wmi to /etc/modprobe.d/blacklist.conf (put "blacklist acer_wmi" at the end of the file).

---

### Post by kpkeerthi on 2009-06-25
You need to do these:

> **Hospadar said:**
> add a line that says ath5k to /etc/modules

[quote=3rdalbum]
Add acer_wmi to /etc/modprobe.d/blacklist.conf (put "blacklist acer_wmi" at the end of the file). 
[/quote]

---

### Post by MrCloudHands on 2009-06-29
I have the same problem and when I try to edit the file it says: 

"You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

How can I get permission to save the ath5k line to the folder? Thanks

---

### Post by blueridgedog on 2009-06-29
```
gksudo gedit /etc/modules
```

---

