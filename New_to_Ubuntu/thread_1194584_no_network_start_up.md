---
title: "no network start up"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by tonymoloney on 2009-06-22
Is it possible to boot up Ubuntu in a "no network" mode?
Every now and then I have to boot up my laptop when it is not physically connected to my network and it takes forever to start up, presumably because it is trying to connect. Even when it has started, I find that starting applications takes much longer than normal, as they seem to be trying to connect to the Net to see if any upgrades are available.
I no that I can issue an ifdown command from the terminal, but this is only after I have gone thru the slow process of booting up.

---

### Post by scrooge_74 on 2009-06-23
I think you should try to upgrade to 8.04, I had a bit of that kind of problems in the past, but with 8.04 it wont try to connect to wireless net till I log in the user. The network manager got improve by the next version.

Your laptop is also trying to update packages, you could tell the update system not to do it unless you manually tell it to.

But again it would be wise to upgrade

---

### Post by tonymoloney on 2009-06-23
Thanks Scrooge_74. At least your answer told me one thing - I need to update my signature! I have actually updated to 8.04 some time ago. Otherwise, not much help. I think what I'm looking for is a key-stroke that interrupts the start up and gives me the choice of network or no network. Does such a thing exist?

---

### Post by lswb on 2009-06-23
I've not experienced this with any of the 3 laptops I have used with any version of ubuntu. Is it possible you have configured some software that is looking for a network at boot? 

Another thought, if your laptop has a wifi adapter that is on at boot, and there are wifi nets within range, it may be trying to connect. If this is the case, maybe just turning off the wifi adapter will help.

---

### Post by scrooge_74 on 2009-06-24
Do you have any network drives? Or anything that requieres the network at start? Besides the network itself? 

I remember seeing a couple of threads about services asking or needing stuff from the network so when it was not on it would behive like this. 

Try checking the services that you have running or after booting open a console and type dmesg so you can see what came on when you booted, you may get some ideas there

---

