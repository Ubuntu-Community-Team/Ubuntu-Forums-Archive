---
title: "Wifi problem"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by FIPROTO on 2011-05-12
I have an Acer Aspire 5745g, and i've  installed the latest Ubuntu. My windows operating system goes online easily, but on Ubuntu it does'nt give me any form of wireless internet opportunities at all. I'm a total noob - what do i do??? :(

---

### Post by frankbooth on 2011-05-12
Does your wireless detect any networks? Or is it totally dead, as in, network manager icon displays that you're disconnected?

If it's not dead, you should be able to choose between the available networks when clicking the network manager.

According to this article: [http://www.oz9aec.net/index.php/linux/351-ubuntu-linux-on-the-acer-aspire-5745g-laptop](http://www.oz9aec.net/index.php/linux/351-ubuntu-linux-on-the-acer-aspire-5745g-laptop)

The wifi should work out of the box on Ubuntu 10.04 and newer versions.

Image of the network manager:
[img]http://www.multimediaboom.com/wp-content/uploads/2010/11/networkmanagerapplet.png[/img]

---

### Post by anaconda on 2011-05-12
it seems that acer aspire has the atheros wlan chip.

IT's drivers have a known bug, which has a workaround.

workaround:
[http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en](http://www.ubuntusecrets.it/2011/04/hack-connessione-lenta-su-natty-forse-ho-la-soluzione-giusta-per-voi/?lang=en)

your chip should be the ath9k, so follow the instructions for that.

---

