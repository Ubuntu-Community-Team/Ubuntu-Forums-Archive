---
title: "Trouble configuring a modem"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by scottevan on 2007-05-21
I have an on-board modem in my motherboard (Asus P5B-Deluxe) and I tried to set it up using the instructions [here]("https://help.ubuntu.com/community/DialupModemHowto/AlsaModem?highlight=%28modem%29"), but I get the following errors:
```
scott@scott-desktop:~$ sudo dpkg-reconfigure sl-modem-daemon -plow
Shutting down SmartLink Modem driver normally ... no slmodemd daemon running.
Unloading modem driver from kernel ... snd_atiixp_modem.
Allowing use of questionable username.
The user `Slmodemd' already exists as a system user. Exiting.
FATAL: Module ungrab_winmodem not found.
FATAL: Module slamr not found.
Starting SmartLink Modem driver for: auto.
Creating /dev/modem symlink, pointing to: /dev/ttySL0.
```
Does this mean anything to anyone? It looks like it might relate to [Bug 92777]("https://bugs.launchpad.net/ubuntu/+source/sl-modem/+bug/92777"). Any suggestions on what I should do? Thanks!

---

