---
title: "BCM4352  [14e4:43b1] constantly dropping connection"
date: 2018-02-01
forum: Networking &amp; Wireless
---

### Post by zofoxof on 2018-02-01
Hi everyone!

I've got some issues with my wireless card. Even if i've followed the sticky thread and installed the correct drivers, connection keeps going on and off.

I've attached the wireless info output.

[https://paste.ubuntu.com/26500073/](https://paste.ubuntu.com/26500073/)


hope someone can help.

best

---

### Post by praseodym on 2018-02-01
It loads another Ralink driver, too:
```

sudo modprobe -rfv rt2800usb wl
sudo modprobe -v wl
```

---

### Post by zofoxof on 2018-02-02
> **praseodym said:**
> It loads another Ralink driver, too:
```

sudo modprobe -rfv rt2800usb wl
sudo modprobe -v wl
```


thanks ,

I've tried but wifi keeps disconnecting. 
It's strange because under connection settings it says  that it's connected but then if I try to access 192.168.1.1 it won't connect to the router even.


EDIT: after a reboot the connection dropped one, but now seems stable. I'll update if something changes.





best

---

### Post by zofoxof on 2018-02-04
A little update:

seems like the solution provided didn't work as expected.

Still having connection drops once every few minutes.

attached the wireless info script after a connection drop.

Hope someone can help.

best [ATTACH]278434[/ATTACH]

---

### Post by praseodym on 2018-02-04
> ```
[    8.694437] wl: module verification failed: signature and/or required key missing - tainting kernel
```
Deactivate SecureBoot in your (U)EFI

---

### Post by Jay_E on 2018-02-04
Greetings!
I had similar problems when trying to get the "correct" driver.
I found this site/link very helpful.
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)


I have a Broadcomm chip and I finally found the right driver and used the wicd package

---

### Post by zofoxof on 2018-02-04
> **praseodym said:**
> Deactivate SecureBoot in your (U)EFI


Secure boot is already disabled. In fact if i try to enable it (just to disable again) it says i can't enable while i've selected legacy boot entries (i suppose it refers to ubuntu).


> **Jay_E said:**
> Greetings!
I had similar problems when trying to get the "correct" driver.
I found this site/link very helpful.
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)


I have a Broadcomm chip and I finally found the right driver and used the wicd package

i can't figure out how your link could help me: can you be more specific? 


best

---

### Post by zofoxof on 2018-02-08
Up,

no one has this problem?
my pc is an XPS-13 9343 .


best

---

