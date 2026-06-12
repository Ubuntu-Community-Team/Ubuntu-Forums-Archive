---
title: "[SOLVED] wireless ethernet bridge?"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by tribble222 on 2008-10-13
Here is my problem:

I have dsl internet. The phone jack is in the kitchen, far away from the office where all the computers are.  I don't want to run any wires from the kitchen to the office.

What additional equipment do I need to get in order to use the kitchen's internet connection in my office's network?  And how do I set this up?  I tried searching but don't really know the proper terms to search for to do this.  Thanks!

My equipment:
I have an actiontec gt704wg wireless dslmodem/router as well as a 2wire 2701 wireless dsl modem/router.  Also have a linksys regular (non-wireless) router and a linksys switch.

---

### Post by kevdog on 2008-10-13
Cant you just hook up the wireless router in the dsl router and use this?  Am I missing something?

---

### Post by tribble222 on 2008-10-13
Hmm, I'm not sure what you're saying.  None of the computers in my office have wireless cards.  What I want to do is have some device (wireless router?) pick up the wireless signal from the kitchen and route it to the computers in the office.  Looking in the menus on my wireless router I don't see any place to indicate what ssid, password, etc. it should connect to...only what it should broadcast.

---

### Post by iponeverything on 2008-10-13
ok.. I see what you want.

Some wireless routers do bridging and some don't. The best solution might be to just buy some wireless usb dongles for the office computers..

---

### Post by kevdog on 2008-10-13
You need a device known as a wireless bridge.  Basically what is needed here is one router that broadcasts the signal from the kitchen (a regular router), and a second device that picks up the signal in the office (the wireless bridge router), and then is capable of distributing this signal via the devices plugged into the router.  Ive personally accomplished this via the use of a Linksys54GL (or 54GS,G family line of routers) flashed with the dd-wrt firmware.  With this firmware its capable of turning the regular linksys router into an enterprise router.

Another solution would be the use of additional hardware that would transmit the signals through the phone lines themselves locally.  I don't know the correct name of these devices, however one plugs into the router and phone line, and the other the phone line and computer in the office.

---

### Post by tribble222 on 2008-10-14
Thanks. I'm going to go with the WRT310N and flash it with dd-wrt.

---

