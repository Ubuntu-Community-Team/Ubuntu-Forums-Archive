---
title: "Wireless problem: cannot connect to wifi even if I see the SSID (Xubuntu 22.04LTS)"
date: 2023-08-02
forum: Networking &amp; Wireless
---

### Post by davide-gori on 2023-08-02
Hello everyone! I'm new in this forum. I'm having a lot of trouble with my fresh xubuntu installation!
I've just installed Xubuntu 22.04. Everything works fine except Wi-Fi.I managed to connect with a cable and did all the software updates, but the problem still remains. When I try to connect to my access point I can see the SSID as in this screenshot, but when I try to connect the "disconnected" banner appears and I cannot access the web.


I've also tried to connect to a different network, but it is the same.I've tried to check drivers: everything is up-to-date and there are no additional drivers available.Furthermore, I've tried to reinstall everything, but nothing changed.

You can find the output of my wireless-info [here]("https://pastebin.ubuntu.com/p/H2y4XCgZMg/").

EDIT:
I noticed the following logs at startup:

```

[  19.804361] Bluethoot: hci0: unexpected event for opcode 0x0000
[  20.042944] Bluethoot: hci0: hardware error 0x37

```



[IMG]https://i.stack.imgur.com/gAyOk.png[/IMG]

---

### Post by aljames2 on 2023-08-02
Have you tried disabling secure boot in your bios settings?  If that doesn’t work then…

Have you tried enabling your 5 Ghz wifi in your access point.  It should connect to both, but I noticed you have 5g disabled, may be worth trying.

---

### Post by davide-gori on 2023-08-04
Thank you for your answer!
I bought my laptop in 2011, hence I think there is no hardware support for 5g and secure boot was introduced later in the years.

I noticed the following logs at startup, maybe I can edit the first post:

```

[  19.804361] Bluethoot: hci0: unexpected event for opcode 0x0000
[  20.042944] Bluethoot: hci0: hardware error 0x37

```

---

