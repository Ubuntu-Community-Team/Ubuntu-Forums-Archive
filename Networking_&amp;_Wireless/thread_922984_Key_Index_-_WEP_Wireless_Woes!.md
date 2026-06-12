---
title: "Key Index - WEP Wireless Woes!"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by Leonpr on 2008-09-17
Hey guys,

Last couple of days been playing with a TC1100 Tablet & Ubuntu 8.04. From someone who is new to Linux its been interesting and defiantly learnt a lot getting everything working as I want it. However I am having major annoyances when it comes to WiFi.

Problem: Wireless at work is running on Key Index 3. Using the network manager just doesn't cut it.

1st I tried editing the interfaces file to the following:
```
auto eth1
iface eth1 inet dhcp
wireless-essid <ssid>
wireless-key3 <xxx-xxx-xx>
wireless-defaultkey 3

```

But this seems to do nothing at all, after setting this up nothing seems to connect and iwconfig shows it doing nothing at all (don't know if iwconfig would if you setup in interfaces?)

Next I started playing with just the iwconfig commands, after alot of playing around I got it seeing and 'connecting' to the wireless using the following:

```
as Sudo:
iwconfig eth1 essid key xxx-xxx-xx [3]
iwconfig eth1 key [3]

```

but it wouldn't get an IP address and after a few minutes would seem to give up.

Eventually I found by running dhclient eth1 straight away after changing the key to [3] it would get an IP address and work... Woo!! However how do I get it to work after I reboot?

Interface's file doesnt seem to want to play ball so I created the following text file and made it executable.

```
#!/bin/sh
iwconfig eth1 essid <ssid>
iwconfig eth1 key xxxxxxxx [3]
iwconfig eth1 key [3]
dhclient eth1

```

Only problem is that it has to be run with Sudo to actually work and don't know how to do it at start up. Also once it was connected via Sudo network manager app still said network disconnected which forced Firefox to open in Offline Mode.

Seem to be waffling a bit but hope you get the idea, I'm all googled out and wondering if you guys can help.

Cheers,
Leon

---

### Post by Leonpr on 2008-09-21
Bump. Anyone got any ideas?

---

