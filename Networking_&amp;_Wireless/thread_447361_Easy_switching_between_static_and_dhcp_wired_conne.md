---
title: "Easy switching between static and dhcp wired connections?"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by organelas on 2007-05-17
Hello,

I connect usually to 2 networks. At home I use an automatic DHCP wired connection and at work I use a static IP wired connection. Is there a way to configure network connections to automatically recognize which type of net I'm on?

On windows I do this by setting it to automatic recognize network and putting my static IP data on the "Alternate IP Address" tab. This way it would connect either way, just plugging the cable. I thought Feisty new "Roaming Mode" would do such thing, but It is not working for me.

If I set a static ip address, and activate roaming mode, it ignores static ip data, and I cannot connect to work's network (until I set data and leave roaming off). After going home I have to change it manually to DHCP to connect.

Each time I change networks I'm being force to reboot to be able to connect, which is not very pleasant, and it is something that started with Feisty, since in Edgy I could activate the alternative connection without rebooting. Maybe I'm missing something or doing something wrong...

Any suggestions?!?

thanks!

---

### Post by gradedcheese on 2007-05-17
I don't know of an automatic way, but it's easy to ask for a DHCP address from the shell:

```

sudo dhclient eth0

```

So you can have a static configuration, and just use dhclient when needed.  (change eth0 to whatever your LAN interface is, if needed)

---

