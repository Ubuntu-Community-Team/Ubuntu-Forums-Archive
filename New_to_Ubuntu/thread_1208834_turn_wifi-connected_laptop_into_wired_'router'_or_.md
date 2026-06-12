---
title: "turn wifi-connected laptop into wired 'router' or 'modem' for 2nd computer"
date: 2009-07-09
forum: New to Ubuntu
---

### Post by earthpigg on 2009-07-09
hi,

my intent is to somehow make my ubuntu laptop and its wireless internet connection act as a wired internet connection for a 2nd computer.

reason:

wired internet is presently unavailable to me. sketchy semi-reliable wireless is what i have available.... it works for 5 min, then drops for 2 min, then starts working again, maybe next time it drops i just have to disable wireless and enable it again and it works right away, bla bla bla. lots of fiddling. 

i want to install either ubuntu-minimal or arch on the 2nd computer (netbook), and build up from there myself. i pretty much figured out what i want in VirtualBox, but ill need the internet to install it...

dealing with dropped wireless connections and all of that fiddling from the command line seems very daunting.
[U][B]
if i could plug an ethernet chord into my connected laptop, and the other end into the netbook, and have the laptop appear as simply an unsecured wired connection to the netbook... that would be awesome.[/B][/U]


laptop has ubuntu 9.04 amd 64 installed.


ideas?

---

### Post by LowSky on 2009-07-09
you need an cat5 crossover cable, thats first. then you need to enable pc as agateway to the internet for other machines.
[https://help.ubuntu.com/community/NetworkMonitoringBridge](https://help.ubuntu.com/community/NetworkMonitoringBridge)

---

### Post by LewRockwell on 2009-07-09
***This post is more for general reference and future readers of this thread***

The optimum solution for this particular situation would be to procure a wireless router that can be used as a repeater(say a Linksys WRT54G with DD-WRT after-market firmware)

with that solution, not only do you have the wireless functionality but you also have hardwired LAN connectivity

we now return you to your regularly scheduled programming

.

---

### Post by earthpigg on 2009-07-09
thank you for pointing me in the right direction, LowSky, ill post back here if i can't figure things out.

LewRock - yeah, that is probably the type of solution i would have been looking for if this situation where to be permanent for me :)

---

