---
title: "Cannot pair bluetooth mouse"
date: 2021-02-17
forum: Networking &amp; Wireless
---

### Post by Ualpa on 2021-02-17
I haven't found any solution yet so I am posting this.

Problem: I cannot pair my Logitech MX Master mouse via bluetooth to my new laptop with a fresh install of Ubuntu 20.04.2.

I believe the problem is not related to the specific mouse since it has always worked on Ubuntu 18.04 (other machine) and it is working on this same machine under Windows.

Other bluetooth devices (phone, earbuds) have been detected and paired without any problems.

```
$ sudo lsusb |grep Bluetooth
Bus 003 Device 003: ID 1358:c123 Realtek Bluetooth Radio

[...]

blueman-assistant 08.10.59 ERROR    blueman-assistant:197 err       :  Authentication Canceled

[...]

$ bluetoothctl
Agent registered
[bluetooth]# devices
Device FE:45:2F:B4:76:B9 MX Master
[bluetooth]# pair FE:45:2F:B4:76:B9
Attempting to pair with FE:45:2F:B4:76:B9
[CHG] Device FE:45:2F:B4:76:B9 Connected: yes
[CHG] Device FE:45:2F:B4:76:B9 Connected: no
Failed to pair: org.bluez.Error.AuthenticationCanceled
```

Thank you in advance for any help you can provide.

Fran

---

### Post by CelticWarrior on 2021-02-17
[https://www.logitech.com/en-us/articles/mx-master-immersion-guide#section8](https://www.logitech.com/en-us/articles/mx-master-immersion-guide#section8)

---

### Post by Ualpa on 2021-02-18
> **CelticWarrior said:**
> [https://www.logitech.com/en-us/articles/mx-master-immersion-guide#section8](https://www.logitech.com/en-us/articles/mx-master-immersion-guide#section8)

Thank but I don't understand how that can help.

---

### Post by CelticWarrior on 2021-02-18
It's the start of the troubleshooting.

---

