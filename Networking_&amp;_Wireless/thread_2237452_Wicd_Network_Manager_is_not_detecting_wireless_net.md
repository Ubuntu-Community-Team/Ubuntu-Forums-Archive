---
title: "Wicd Network Manager is not detecting wireless networks"
date: 2014-08-01
forum: Networking &amp; Wireless
---

### Post by Domgoa on 2014-08-01
Hello, i am new to this forum and this is my first post.

I am useing Crouton Xfce4 on my Acer C710 Chromebook (Ubuntu 12.04.4 LTS, precise).

When i open Wicd Network Manager its telling me im connected to a wired connection although i am using Wifi. 

It dose not detect any wireless networks at all.

How can i solve this issue?

---

### Post by TheFu on 2014-08-02
In a terminal, run
**rfkill list**
See if the wifi is locked.  Unlock it.

---

### Post by Domgoa on 2014-08-02
When i enter the command[B]: rfkill list


bash: rfkill: command not found


[/B]

---

### Post by TheFu on 2014-08-02
I don't know which package it is in, but this  ...
```
$ rfkill list
1: phy0: Wireless LAN
        Soft blocked: yes
        Hard blocked: no
2: hci0: Bluetooth
        Soft blocked: no
        Hard blocked: no

```
is the output when wifi is locked and needs to be unlocked. I ran that on my C720 a few seconds ago.  I'd recommend finding the package it is in and installation, then running the command.

I only use wifi when there isn't an ethernet connection available. At home, now, I'm using a wired GigE ethernet connection, which is why the wifi is locked, I think.

---

