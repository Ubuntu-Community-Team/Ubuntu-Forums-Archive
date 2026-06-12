---
title: "Ideapad 320 | Ubuntu 19.04 - Cannot discover Bluetooth mouse"
date: 2019-04-23
forum: Networking &amp; Wireless
---

### Post by GTMoraes on 2019-04-23
Hi,

I'm trying to pair and use a Logitech MX Anywhere 2 mouse, but Ubuntu 19.04 is unable to even find and list the Bluetooth mouse. It used to work on 18.04 before, and it does work on Windows and on an Android device.
Bluetooth is seemingly working fine, as it can detect my Android phone, two sets of wildly different speakers from my home, my TV, an unknown iPhone (presumably my neighbour) and even two devices from my car two stories down below...

I've tried pairing it directly on bluetoothctl, but even there it is unable to find this BT Mouse. I event tried getting the mouse MAC address from my Android phone and connecting blindly to it, but bluetoothctl just says "<MAC> not available."
I've restarted several times, slept and resumed, ran a couple of commands, disabled wi-fi during bluetooth scan.. all to no avail.

I'm out of ideas, what should I do now?

----------------------------

After a day, it suddenly appeared on the Bluetooth list. I have no idea what made it get fixed, but perhaps an update did something. 
This Ubuntu was fully updated yesterday anyway. Well, it now works.

---

