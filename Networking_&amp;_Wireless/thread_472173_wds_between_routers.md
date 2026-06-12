---
title: "wds between routers"
date: 2007-06-12
forum: Networking &amp; Wireless
---

### Post by dracule on 2007-06-12
sorry if this is in the wrong section (since it doesnt really pertain to ubuntu, but rather wireless in general but i couldnt find a proper place for this.

so my question. i have a dlink wbr-2310 which cant have dd-wrt on it, but i have a la fonara which can (i dont use it because it only has 1 ethernet port), but my inquiry is that while reading dd-wrt's wiki, i saw it had something called wds, which makes it act like a repeater. now do both routers have to have dd-wrt's firware on them, or can i just have 1 router with it and set it up as a repeater?

---

### Post by dracule on 2007-06-13
bump

---

### Post by chili555 on 2007-06-13
I used two routers with wds, but the second one was set up as a bridge, not a repeater. In other words:

cable modem/internet----WRT54G  ~~~~~~~(wireless)~~~~~BEFW11S4----computer

The key here is both routers have to support wds. In my example, a firmware upgrade on the BEFW11S4 provided wds; HyperWRT firmware on the WRT54G provided it.

I tried to set up the BEFW11S4 as a repeater and could never get it to do so. I bought a WAP54G, upgraded it's Linksys firmware and have it repeating easily.

I would not have a clue how to set either of your routers as a repeater, however both, I believe, must support wds.

---

### Post by tgm4883 on 2007-06-13
> **dracule said:**
> sorry if this is in the wrong section (since it doesnt really pertain to ubuntu, but rather wireless in general but i couldnt find a proper place for this.

so my question. i have a dlink wbr-2310 which cant have dd-wrt on it, but i have a la fonara which can (i dont use it because it only has 1 ethernet port), but my inquiry is that while reading dd-wrt's wiki, i saw it had something called wds, which makes it act like a repeater. now do both routers have to have dd-wrt's firware on them, or can i just have 1 router with it and set it up as a repeater?

Both have to support WDS.  Setup is available here [http://www.dd-wrt.com/wiki/index.php/WDS_Linked_router_network](http://www.dd-wrt.com/wiki/index.php/WDS_Linked_router_network)

---

### Post by dracule on 2007-06-13
sorry for the question but can you make it act like a bridge(well not actually bridge) to a set comp? because i only have one computer with bad reception... would this require both having the firmware?

for example:

modem->router(without dd-wrt)~~~~~wireless~~~~router(with dd-wrt)~~wirelss~~comp with static ip

so it really isnt really usign wds

omg is this what i need? [http://www.dd-wrt.com/wiki/index.php/Universal_Wireless_Repeater](http://www.dd-wrt.com/wiki/index.php/Universal_Wireless_Repeater)

---

### Post by tgm4883 on 2007-06-13
Maybe with V24 and multiple SSID's, but wireless bridge or client mode will just connect to the access point, not repeat the signal

---

### Post by dracule on 2007-06-14
i bricked 1 of my routers trying to get the firmware installed, but by the sounds of the link i gave, it should work.

---

### Post by denix on 2007-06-21
> **chili555 said:**
> I used two routers with wds, but the second one was set up as a bridge, not a repeater. In other words:

cable modem/internet----WRT54G  ~~~~~~~(wireless)~~~~~BEFW11S4----computer

The key here is both routers have to support wds. In my example, a firmware upgrade on the BEFW11S4 provided wds; HyperWRT firmware on the WRT54G provided it.

I tried to set up the BEFW11S4 as a repeater and could never get it to do so. I bought a WAP54G, upgraded it's Linksys firmware and have it repeating easily.

I would not have a clue how to set either of your routers as a repeater, however both, I believe, must support wds.
Hi guys, 
interesting discussion! we just changed our ADSL router with a [http://adsl.free.fr/](http://adsl.free.fr/)
the problem is that this router has not the same power of the old one and to bring the net on all the house we would like to recycle the old BEFW11S4.
how can I configure it as a bridge like in your conf?

ADSL --- FreeBox ~~~ BEFW11S4 ~~~ computer

IP address doesn't matter, we only want to use internet

---

### Post by chili555 on 2007-06-23
> ADSL --- FreeBox ~~~ BEFW11S4 ~~~ computer
If you are trying to make the connection from the BEFW11S4 wireless, to extend the range of the signal in your house, then you are trying to get it to work as a repeater, which I could never get to work. Wired, yes, using wds. Wirelessly, never.

There are wireless range extenders manufactured by Linksys, among others. I bought a Linksys WAP54G on Ebay because it has a repeater mode in its newest firmware. I set it up and had it running in a very few minutes.

Incidentally, I found the BEFW11S4 especially unreliable.

---

### Post by tgm4883 on 2007-06-23
> **chili555 said:**
> If you are trying to make the connection from the BEFW11S4 wireless, to extend the range of the signal in your house, then you are trying to get it to work as a repeater, which I could never get to work. Wired, yes, using wds. Wirelessly, never.

There are wireless range extenders manufactured by Linksys, among others. I bought a Linksys WAP54G on Ebay because it has a repeater mode in its newest firmware. I set it up and had it running in a very few minutes.

Incidentally, I found the BEFW11S4 especially unreliable.

Are you saying that you connected it wired AND with WDS?

---

### Post by chili555 on 2007-06-23
> Are you saying that you connected it wired AND with WDS?WDS is the protocol used for my WRT54G and my BEFW11S4 to connect wirelessly. Then three computers (don't ask!) connected to the ethernet ports on the back of the BEFW11S4.

I have even weirder setups than that, actually!

Please see post #3 above.

---

### Post by tgm4883 on 2007-06-23
> **chili555 said:**
> WDS is the protocol used for my WRT54G and my BEFW11S4 to connect wirelessly. Then three computers (don't ask!) connected to the ethernet ports on the back of the BEFW11S4.

I have even weirder setups than that, actually!

Please see post #3 above.

Yea I know what WDS is, I just couldn't figure out why you would have it both routers connected wirelessly and wired.  Apparently you don't.

---

