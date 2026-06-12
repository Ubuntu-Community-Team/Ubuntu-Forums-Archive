---
title: "wireless networking"
date: 2005-04-21
forum: Networking &amp; Wireless
---

### Post by paulfox on 2005-04-21
I'm connected to the internet wired through a router on LAPTOP1, and i want LAPTOP2 to connect to the internet via laptop1. (lap2 -> lap1 -> router)

how do I configure laptop1 to allow connections through it's wireless device from laptop2?
i've added the wlan0 connection(after ndiswrapper install etc) as a dchp connection, and after i click connect, after about 30 seconds the device becomes active, but the windows machine still cant see it. 

any ideas where i'm going wrong???

---

### Post by AlP on 2005-04-22
What you want is to build an ad-hock network, the WaveLan card of the Linux-PC has to be in a special mode, which is NOT "managed" (which I do not remeber), ask google. I do not know if the ndiswapper does support this.

---

