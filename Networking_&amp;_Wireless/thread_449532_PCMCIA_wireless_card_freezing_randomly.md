---
title: "PCMCIA wireless card freezing randomly"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by Cryptorchild on 2007-05-20
Hi all.

I'm relatively new to wireless support in Ubuntu, and I am having a few problems with my PCMCIA laptop card.
I am using an Ubuntu 7.04 and the card is an Edimax EW-7108PCg, which is based, according to most, on the Ralink rt61 chipset (although not everyone agrees. According to [this page]("http://ralink.rapla.net/") my card is based on the RT2500 chipset).
I have two main problems:
1) Every time I put the card in to the PCMCIA slot, Ubuntu freezes completely, with no warning. This happens less frequently if I configure /etc/network/interfaces to auto ra0 dhcp.

2) I am aware of the fact that Network Manager doesn't support my card, so I installed RutilTv0.14. The only problem is that if I try and scan for the available wireless networks, the program outputs the following bizarre error message:
> 
Critical error :
Can't read in socket.
Code : 4

This same error message pops up if I try to configure, or do anything else to the card...


The one that is bugging me the most is the first problem, as I can still connect with the card, but it's a bit annoying having your machine to freeze randomly now and then.

Any ideas?

Any suggestion would be much appreciated... :)

---

### Post by Cryptorchild on 2007-05-20
Anyone?

I think the problem is something to do with the PCMCIA module. The reason why I say that, is cause if I leave the card on while booting up, taking out --quiet, this message pops up:

CPU #0 soft lockup during boot

...and the operating system won't boot up. I had a look through a few threads, and loads of people seem to suggest to switch back to 6.10, which isn't really an ideal solution...

---

### Post by jarocooke on 2007-06-01
I am having exactly the same problem.

Your card could be either rt2500 based or rt2561 (rt61) based.  Mine is rt61 based.

The reason for the lockups is the ralink drivers!!!  How this can be the case is anyone's guess given that I think they are open source, however there you have it.

What I am in the process of trying (if the windows drivers ever finish downloading), is blacklisting the rt2561 driver in Ubuntu in /etc/modprobe.d/blacklist and then installing the windows drivers using ndisgtk.

I am also changing /etc/modprobe.d/ndiswrapper to ra0 from wlan0 as per the post below.

[http://ubuntuforums.org/showthread.php?p=2720578](http://ubuntuforums.org/showthread.php?p=2720578)

I will let you know if it works, but I am hoping that it will allow me to use network manager properly this way and hopefully without the lock ups (I have them too using the default drivers).

---

### Post by loathsome on 2007-06-02
Hi guys,

If you haven't solved this problem, please try this:
[http://ubuntu.loathsome.us/doc/rt61](http://ubuntu.loathsome.us/doc/rt61)

loathsome :KS

---

### Post by Cryptorchild on 2007-06-03
Thank you both for your help.

I am pretty sure I tried loathsome's fix sometime ago, but I'll give it another shot when I get some time and post the results in here.

Also, jarocooke, please let us know on how it goes for you...

Cheers.

---

