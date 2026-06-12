---
title: "How can I simulate an ethernet connection? (-Help Please-)"
date: 2008-03-07
forum: Networking &amp; Wireless
---

### Post by Repgahroll on 2008-03-07
Hello Guys :D

I'm having a big problem here! :(

A bolt just fell near my house when I was using the dial-up internet on my notebook, then the internal modem has gone. OK...

But now I'm having a very strange problem:

A software that need to read the mac address of the etheret card to run, just can't do it anymore :( unless if I am connected on the DSL. :confused:
I cannot understand why this happens, because I can plug the rj45, connect, then unplug the cable, and then run the software.

It's not a matter of being connected or not, i think it's something about the ethernet being active, cause the diagnostic is:

If the ppp0 is up and in route, the software can read the mac. If not, the software just can read 00-00-00..., the ifconfig ALWAYS retrieve the correct address.


Now the questions:

1.- Is it possible to connect the ethernet without a service, just to create the ppp0 iface, or make the ethernet active?
(Maybe connect without replies; force a connection without check expected replies signals, connect just to a dsl modem without the service, cut an rj45 and connect some wires to make the ethernet think its connected or active :D, maybe theres some hardware that i can buy or make to connect in the ethernet port and connect the pc to a virtual provider,  there must be a way to do it...)

2.- Why the ethernet stop working properly if just the modem was connected and in use at the bolt moment? Do they (eth&modem) have some intercourse?

3.- I could hibernate, do it works? I could connect to the DSL at the company and then hibernate with the software openned and then just bring back from hibernation while at home, but my notebook have problems to hibernate in Ubuntu, and i think should be very hard to make it work, cause i just followed a lot of how-to's and still the same, so just confirms if hibernating should work and i'll try to make it work. Don't hibernate closes the ppp0 interface?

:)Thank you very much! :(Sorry my english!

---

