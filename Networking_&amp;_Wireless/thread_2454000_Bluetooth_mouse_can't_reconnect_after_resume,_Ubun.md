---
title: "Bluetooth mouse can't reconnect after resume, Ubuntu 20.10"
date: 2020-11-21
forum: Networking &amp; Wireless
---

### Post by zhangweiwu on 2020-11-21
Bluetooth Mouth works until sleep. After resuming from sleep, however, the mouse will try to reconnect then, failing that, turns itself off.

This issue appears only after updating to 20.10 (from 20.04). In fact, in the past decade, every time when I upgrade Ubuntu to something, Bluetooth stops working. It is the component always expected to break.

lsusb says I have

Bus 001 Device 004: ID 8087:0a2b Intel Corp. Bluetooth wireless interface

The mount is Logitech MX Master 2S.

3 workaround works. This post asks for a method to return it to the Ubuntu 20.04 level of experience (that the mouse connects by clicking).

[LIST]
[*]    Reboot Ubuntu
[*]    Plugin another mouse and use it to access the Bluetooth configuration, choose the mount "MX Master 2S" and flip "Connection" Switch on.
[*]    Run this command (with the ID of my mouse)```
$ echo connect DA:8E:70:A2:34:F1 | bluetoothctl
```
[/LIST]

P.S. Is this something to do with the kernel? 5.8.0-28-generic might be too new?

---

