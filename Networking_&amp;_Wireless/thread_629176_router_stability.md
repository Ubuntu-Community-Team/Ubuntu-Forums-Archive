---
title: "router stability?"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by hvac3901 on 2007-12-02
I never had a problem while with windows, and now my router crashes from time to time.

in reality its a trade off for all the spam virus and mal ware i use to receive, but i was curious if i missed something. I am very new to Ubuntu and linux. So is there3 something i should know? other than my DSL isp doesn't really support linux too well.

---

### Post by Schalken on 2007-12-02
Different operating systems communicate with router's in a standardised fashion. They broardcast DHCP DISCOVER on the network, the router responds with IP and DNS info and from then on its just some periodic maintenance work.

I don't think there is much room for something to go wrong between a router and a computer. It's up to the router to respond to DHCP DISCOVER packets with the proper informations. That's the wonder of networks, their OS antagonistic and standardised nature.

Unless maybe your router is connected via USB, I've never done that before on Linux.

When you're router dies, do "sudo ifdown -a" (shutdown all network interfaces) followed by "sudo ifup -a" (startup all network interfaces again) and it will say what information it is sending and receiving from the network/router.

---

### Post by hvac3901 on 2007-12-02
thanks that was a bit wordy for me but i think i got it loud and clear.

MY OS doesn't matter. so the trouble i am having now (which is but a minor nuisance is maybe something else?

---

