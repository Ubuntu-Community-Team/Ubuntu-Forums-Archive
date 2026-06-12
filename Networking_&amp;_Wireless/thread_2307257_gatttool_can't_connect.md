---
title: "gatttool can't connect"
date: 2015-12-23
forum: Networking &amp; Wireless
---

### Post by martin175 on 2015-12-23
Hello,
I can do hcitool lescan:

LE Scan ...
D7:01:00:9F:92:97 MyDevice

However performing:

sudo gatttool -b D7:01:00:9F:92:97 -I
[   ][D7:01:00:9F:92:97][LE]> connect

leads to:

Connecting... connect error: Transport endpoint is not connected (107)

Why? The device I'm trying to connect to is perfectly connectable from my Android phone or Qt application. I have Ubuntu 14.04.

---

