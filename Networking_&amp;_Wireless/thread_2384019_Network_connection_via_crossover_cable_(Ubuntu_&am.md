---
title: "Network connection via crossover cable (Ubuntu &amp; Windows)"
date: 2018-02-01
forum: Networking &amp; Wireless
---

### Post by saibabachris on 2018-02-01
Hi everyone,

currently I am trying to connect my notebook (Ubuntu 16.04, Internet access) with my Desktop PC (Win 7, CAD & CFD workstation, no Internet access) via crossover cable.

First I would like to be able to transfer data and in the next step, enable internet access to the workstation via the notebook.

I found this tutorial ([https://www.techwalla.com/articles/how-to-connect-ubuntu-to-windows-with-a-crossover-cable](https://www.techwalla.com/articles/how-to-connect-ubuntu-to-windows-with-a-crossover-cable)), but unfortunately the terminal reports this (translated from german to [COLOR=#ff0000]eng.[/COLOR]) :

SIOCSIFADDR: Kein passendes Gerät gefunden / [COLOR=#ff0000]no matching device[/COLOR]
eth0: FEHLER beim Auslesen der Schnittstellenmerker: Kein passendes Gerät gefunden / [COLOR=#ff0000]ERROR while reading the interface : no matching device[/COLOR]
SIOCSIFNETMASK: Kein passendes Gerät gefunden / [COLOR=#FF0000]no matching device[/COLOR]
eth0: FEHLER beim Auslesen der Schnittstellenmerker: Kein passendes Gerät gefunden / [COLOR=#FF0000]ERROR while reading the interface : no matching device

[/COLOR]Any advice, tutorials or tools ?

Greetings,
saibabachris

---

### Post by tps-mail on 2018-02-01
I would try plugging in a straight cable, instead of a crossover. Modern NICs autosense, and will do the right thing.

---

### Post by saibabachris on 2018-02-01
Tried that, same error!

Edit: Found the solution ([https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)).

Greetings,
saibabachris

---

