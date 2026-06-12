---
title: "networking always UP"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by electrickery on 2009-04-05
Can anyone help me with this. Im running Ubuntu and when I disconnect the networking icon, it crosses itself out to say it's disconnected but ifconfig and everything else says eth0 is still UP.

---

### Post by zigga15 on 2009-04-05
> **electrickery said:**
> Can anyone help me with this. Im running Ubuntu and when I disconnect the networking icon, it crosses itself out to say it's disconnected but ifconfig and everything else says eth0 is still UP.

This is because it is... the hardware is still working, and the back-end/daemon of the network manager is still doing stuff,

try unplugging your network cable and see what happens then, or if you are running wireless take your receiver out.

~ Dan

---

### Post by electrickery on 2009-04-06
Hmmm...well how it was on my last install on other system was that if I looked at SYSTEM > ADMIN > NETWORK TOOLS > DEVICES , and clicked on the Network Device menu Eth0 would not even show up if the network was deactivated via GUI. And using TCPDUMP would not output data.(it would just go straight back to prompt if network was supposedly OFF. But now TCPDUMP does continue to run even if Gui says network is off. I think thats very suss. as i say it was not like this with my last install...

---

