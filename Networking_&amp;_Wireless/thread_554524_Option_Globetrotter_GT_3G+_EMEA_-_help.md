---
title: "Option Globetrotter GT 3G+ EMEA - help?"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by michaelpo on 2007-09-19
hi.. i'm in Malaysia..3G operator is Maxis mobile..
i'm using ubuntu/linuxmint
how do i get Option Globetrotter GT 3G+ EMEA card working?
i've installed gcom..
then i run the command at terminal: gcom -d /dev/noz0...
which returns the result:

SIM ready
Waiting for Registration..(120 sec max)
Registered on Home network: "MY MAXIS",2
Signal Quality: 21,99

it seems i'm connected to the 3g...
but... how do i get ubuntu/linuxmint to connect through the 3g card?
or do i setup at the menu -> system -> network?

when i type the command gcom
or when i type the command gcom -d /dev/modem
Can't open GlobeTrotter /dev/modem.

[email]michaelpo@gmail.com[/email]

---

### Post by Spin84 on 2008-01-31
Hi

I have this card and successfully managed to get it working by using this project:
[https://forge.vodafonebetavine.net/](https://forge.vodafonebetavine.net/)

The Vodafone Mobile Connect Card Driver for Linux seems to work with a large variety of cards - see [http://en.wikipedia.org/wiki/Vodafone_Mobile_Connect_Card_driver_for_Linux](http://en.wikipedia.org/wiki/Vodafone_Mobile_Connect_Card_driver_for_Linux)
It is network independent and the documentation on their site is ok.

Hope this helps as I was searching for a way to get my 3G card working for ages!

---

