---
title: "[SOLVED] T42 bluetooth not working on gutsy"
date: 2007-12-06
forum: Networking &amp; Wireless
---

### Post by tedrogers on 2007-12-06
Hi all,

Thought I would post the results of a problem that I managed to find the solution for. The problem was that although I could get my Bluetooth enabled and recognised, it would not connect properly on my IBM T42, but probably other systems too..

So you turn on Bluetooth on the T42 by holding Fn + F5, that was the easy bit.

When trying to connect to a bluetooth device, like a phone, If you get the error in gutsy:

**"obex://[nn:nn:nn:nn:nn:nn]" is not a valid location**

...then this command fixed the problem for me (essentially installing "gnome-vfs-obexftp"):

```
sudo apt-get install gnome-vfs-obexftp
```

All of this information and more is available here:

[https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29](https://help.ubuntu.com/community/BluetoothSetup?highlight=%28bluetooth%29)

I hope this helps someone else and means they don't have to look around too much for a solution.

---

