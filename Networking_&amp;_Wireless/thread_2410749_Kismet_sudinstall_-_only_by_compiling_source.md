---
title: "Kismet sudinstall - only by compiling source?"
date: 2019-01-20
forum: Networking &amp; Wireless
---

### Post by x70 on 2019-01-20
Hello,
I'm trying to install Kismet to troubleshoot my home WiFi ([https://www.kismetwireless.net/docs/readme/suid/](https://www.kismetwireless.net/docs/readme/suid/)) and since i have read that it is better to never run the SW as root, i was trying to use the suggested sudinstall option.
However it seems that this is possible only when first compiling from source and not when installing from package?
I'm new to Linux and not fully familiar with installation of software that require compiling. At the above link it seems it is just a matter of three commands:
[I]$ ./configure
$ make
$ sudo make suidinstall
[/I]It would be very helpful for me understand all the steps required.

So far i only managed to install from package via sudo install / sudo upgrade but it seems that by doing so kismet can only be run as root; I tried to add my user to the kismet group but kismet never shows up in the list of the groups i belong (even i after logging out/in). Then if i run a *getent group kismet* my user appears in the list of group members... I'm new to Linux so i probably miss something fundamental here, so i'd appreciate some advise.

Thanks,
Teo

Ubuntu 18.04

---

