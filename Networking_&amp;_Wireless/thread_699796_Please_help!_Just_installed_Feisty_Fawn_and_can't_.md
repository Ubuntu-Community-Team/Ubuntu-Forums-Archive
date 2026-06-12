---
title: "Please help! Just installed Feisty Fawn and can't connect to the Internet :("
date: 2008-02-17
forum: Networking &amp; Wireless
---

### Post by MrWally on 2008-02-17
So I've used Ubuntu on and off over the past couple years, but I'm still pretty much a newb to the whole Linux scene. Right now I'm actually setting up a Ubuntu Linux Feisty Fawn on one of my very old AMD Duron desktops for my mother, who seems fairly excited to move into the Linux world.

However, I am experiencing some issues. First off, due to recent difficulties with AT&T I am connected directly into our Speedstream 5100 Modem, not through a router. Additionally, my older motherboard does not have onboard LAN, so I plugged in a very basic PCI network card. Right now it doesn't detect any network and I can't ping any sites and I'm pretty much at a loss at where to go next, especially because in my past setups networking has never been an issue (though I've always connected through our Linksys router). Again, I'm going to emphasize that this is not a wireless setup.

Please, does anyone have any suggestions?

---

### Post by 1337455 10534 on 2008-02-17
Have you tried the latest version of Ubuntu, Gutsy Gibbon?

---

### Post by MrWally on 2008-02-17
I have not, I do not currently have a cd for Gutsy Gibbon and, since I do not have a cd burner at the moment the only option would be to upgrade, but seeing as I don't have an internet connection...

I really don't see why that should be an issue, though. I haven't done any configuration to my network settings because I'm pretty much at a loss as to what I need to do, so I was fairly confident that there was a relatively simple fix to my problem, I just haven't learned it yet.

---

### Post by spartan_87 on 2008-02-17
What network card do you have? And does it show up when you run:
```
 lspci 
```

---

### Post by MrWally on 2008-02-17
Winbound Electronics Corp W89C940, apparently.

It's a very very basic Ethernet card.

---

### Post by Iowan on 2008-02-18
Some modems "lock onto" a MAC address.  Resetting the modem *might* help.

---

