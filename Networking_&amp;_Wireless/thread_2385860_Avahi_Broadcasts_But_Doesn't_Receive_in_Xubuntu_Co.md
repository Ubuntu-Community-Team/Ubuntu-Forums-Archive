---
title: "Avahi Broadcasts But Doesn't Receive in Xubuntu Core"
date: 2018-02-26
forum: Networking &amp; Wireless
---

### Post by Jack Waugh on 2018-02-26
I just installed Xubuntu Core on an old slow 32-bit computer. I am used to Avahi working fine between regular Xubuntu LTS systems (not "Core"). I tried connecting such a regular system to the new Core system. The regular Xubuntu system sees the Core system but not the other way around. The Core system can connect to the regular Xubuntu system via the latter's IP number, but doesn't succeed to look up the ".local" name. I have made sure the content of /etc/nsswitch.conf is the same on the Core system as it is on the regular system, which has been working both ways fine with its other regular mates. I rebooted the system that has Core installed on it, so the nsswitch change should be in effect.

---

