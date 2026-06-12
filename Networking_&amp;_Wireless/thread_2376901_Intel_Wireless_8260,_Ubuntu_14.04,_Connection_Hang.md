---
title: "Intel Wireless 8260, Ubuntu 14.04, Connection Hangs"
date: 2017-11-07
forum: Networking &amp; Wireless
---

### Post by snowseven on 2017-11-07
Hi.

I recently installed Ubuntu 14.04 on my desktop and have been running into some wireless issues.
I have the Gigabyte Z170N motherboard that comes with the Intel Wireless 8260 wifi built-in.

The issue I've been having is that it connects to wifi, but every couple hours I lose internet connectivity. 
Ubuntu still says that it is connected to the internet (wifi icon on notification bar is still connected and says I am connected to the correct access point) and the adapter is still detected, I just can't load any webpages or ping 8.8.8.8.

After disconnecting and reconnecting a couple of times, the connection recovers for a while until the next disconnect.

This seems to be an Ubuntu and wireless card related issue; when I dual boot into Windows 10 I do not have this issue. I am also able to connect to the network on my other Linux machine without issues.

I ran the wireless-info script during one of these events, which I have attached as a tar.gz and pastebin below.
I also included a pastebin of wireless-info when the network is working normally for comparison.

Anyone have any ideas on how to fix this?

Thanks for your help!

[ATTACH]277442[/ATTACH]

Pastebin (during disconnect event): [https://pastebin.com/M5VLmmcw](https://pastebin.com/M5VLmmcw)
Pastebin (when working normally): [https://pastebin.com/5LwLEMEX](https://pastebin.com/5LwLEMEX)

---

### Post by ajgreeny on 2017-11-07
See [https://ubuntuforums.org/showthread.php?t=2331090](https://ubuntuforums.org/showthread.php?t=2331090) for some possibilities related I believe to the fact that you are still using 14.04 with that newer Intel wifi card.

Try some of the solutions mentioned and you may manage without having to upgrade your OS to 16.04 which, as far as I'm aware, should manage that card better.

---

