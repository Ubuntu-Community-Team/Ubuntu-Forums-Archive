---
title: "Can't configure wireless the way I want"
date: 2008-08-23
forum: Networking &amp; Wireless
---

### Post by IFailAtLinux on 2008-08-23
Well, I wasn't sure how to name this topic. I have WL-5480USB-50 thingy connected to my PC and it has eth2 interface(I have another wireless card in, and 2 wired ones).

First thing I want to do is to configure my USB card to work as access point. I figure it's station mode, right? Or Managed mode. Anyway, I wasn't able to make it visible by any of my wireless devices and whenever I try to google out anything about configuring access point on Linux I get a lot of info on how to connect to access point.

So, how do I do it? Anyone can show me some tutorial, doc, gui application or be nice enough to tell me how to do it in console?

Second thing I want to do is to make my wireless devices that will connect to WL-5480 to be able to use internet. I'm already doing that with device connected to eth1 but I used Firestarter and it made all configuration for me. But I think it can forward only 1 connection at a time... Ah, the outgoing connection is eth0.

I'm really bad at this stuff, and even though I read tons of tutorials on routing I never managed to do it by hand :( Even if I had exactly the same set up as the one who wrote tutorial in the end all I tried ended in vain.

---

### Post by IFailAtLinux on 2008-08-24
I'm in right section, right? Last time I asked about configuring AP I met dead silence for a week... Why? Is it impossible to make AP of Linux? Or I'm asking something wrong?

---

### Post by Neo_M on 2009-02-22
I am having the same problem..I have a wireless access point connected to a switch. The switch is connected to the linux machine. The LAN works fine and I can connect to anything connected to the switch. Question is how do I "see" other wireless devices through the Wireless access point on the switch with the linux machine.

I know this can be done in windows, because Netgear has an illustration of it on the box. How do I get started.

---

### Post by pdtpatrick on 2009-02-23
It's not impossible to make AP in linux -- as you can see many distros can be used as a wireless router. However, you have to make sure your card can be put into monitoring mode. 

Check the driver of your card and the model and verify whether it is capable of being put into monitor mode to observe the network.

---

### Post by Neo_M on 2009-02-23
I am not looking to make the linux machine an AP I just want it to access the IP and everything else the AP can see. My laptops can see the AP, now how do I get the Linux machine to see the AP on the switch?

---

### Post by Reiger on 2009-02-24
To see devices 'ask' your router. You could do this by logging into the router/AP web control panel if it supports such a thing and you are administrator of it (both are typical for home use networks).
To do so, merely navigate to [http://192.168.1.1](http://192.168.1.1) or [http://192.168.2.1](http://192.168.2.1) (actually: [http://ip-address-of-router](http://ip-address-of-router) but the above two are the most common for wireless routers).

---

