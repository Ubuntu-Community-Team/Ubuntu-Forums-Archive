---
title: "ok...3rd try on my feisty wireless question.."
date: 2007-08-18
forum: Networking &amp; Wireless
---

### Post by kaufman on 2007-08-18
I have an IBM z60t with atheros wireless running Ubuntu 7.04 (dual boot).
It seems to recognize the wireless card, because it has no trouble detecting
networks and showing signal levels, and it even detects the security type
and asks for the appropriate password, but it has never been able to connect
to any of them…even unsecured networks.
I tried using my spare usb Linksys adaptor and it did the same thing.
It shows both adaptors (atheros and “unknown usb vendor specific”) and the
neworks listed under them, if I try to connect, I get the little orbiting comet icon,
and then nothing. I’m relatively new at Linux, but trying…just need a little help with this.
Thanks in advance.

---

### Post by Jamie Jackson on 2007-08-19
I don't know if/how there's a way to see what's going on while NetworkManager's doing its thing, which makes it hard to diagnose.

This is a shot in the dark, but try issuing:
dmesg | tail

...before and after a connection attempt. If there's any difference between the first and second dmesg, please post that difference.

---

