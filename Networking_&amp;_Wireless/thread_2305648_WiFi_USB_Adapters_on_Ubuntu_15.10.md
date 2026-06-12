---
title: "WiFi USB Adapters on Ubuntu 15.10"
date: 2015-12-08
forum: Networking &amp; Wireless
---

### Post by Trowen on 2015-12-08
I've got a Netgear G54/N150 WiFi USB Micro Adapters (No. WNA1000M). The device can detect signals just fine but won't connect, or it will connect and then it'll timeout.

I have searched many threads, all having different kinds of solutions, none of them working. Could someone explain in simple steps how to fix this problem? I'm a Linux newbie so could you explain each command/flag you use. Thanks in advance :D 

Also I kind of have OCD about packages on my system, so if I do have to install any, a brief description of its contents would be nice.

---

### Post by Bucky Ball on 2015-12-08
Welcome. To get some clues please open a terminal and run this, with the dongle plugged in:

> sudo lshw -C network

Post the output here between code tags (see last link in my signature).

Have you plugged in with a cable and done an update then rebooted?

---

