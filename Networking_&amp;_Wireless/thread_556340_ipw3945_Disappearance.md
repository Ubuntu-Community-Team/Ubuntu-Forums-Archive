---
title: "ipw3945 Disappearance"
date: 2007-09-21
forum: Networking &amp; Wireless
---

### Post by IknowJoseph on 2007-09-21
An interesting problem with my work provided HP Compaq nx7300...

I took it home, loaded Kubuntu 7.04 and brought it back to the office the next day; everything worked fine and I was happily connecting to the provided WLAN.

I came to work this morning, turned on the laptop and eth1 - my wireless card - has disappeared.

/var/log/messages shows that the card has been seen by Kubuntu, as does lshw -C network, but it's not shown by ifconfig, iwconfig of the KNetworkManager.

It seems to be a lot like this problem:

[http://ubuntuforums.org/showthread.php?t=427222](http://ubuntuforums.org/showthread.php?t=427222)

But, of course, I don't have a /proc/acpi/asus/ although I do have a button to turn the wireless on and off. Various restarts with it in various states have failed to resolve anything.

Any ideas?

---

### Post by cdiem on 2007-09-21
Could you post the output of:
```
dmesg | grep ipw
```
I believe it could be the kill switch.

---

