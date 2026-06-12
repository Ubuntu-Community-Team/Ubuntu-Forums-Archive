---
title: "[SOLVED] wireless usb dongle"
date: 2008-04-01
forum: Networking &amp; Wireless
---

### Post by lilalmond on 2008-04-01
Hi

My connection is going on and off all the time...
I have a wireless modem with a wireless USB dongle (level one)
I tried many things to get a better connection but it just doesnt work.(from the thread slow wireless and wired internet Ubuntu 7.10)
I have disabled IPv6 in firefox
I have disabled alias net-pf-10 ipv6 in /etc/modprobe.d/aliases
I edited (~prepend) in /etc/dhcp3/dhclient.conf
Im out of options...
Any help would be welcome

---

### Post by bluemarble on 2008-04-01
I am having similar problems!

I have a usb wireless dongle as well and cannot get internet. I have to use my windows partition to surf the internet, which i dont like :(

I dont know what to do either. There are many people looking for help with the same problem and there is not much help around :(

---

### Post by lilalmond on 2008-04-02
This is insane, my connection keeps on jumping in and out.
And the funny part is that the "network" icon shows im connected but im not hooked up to the internet.
This is really annoying to get disconnected like every 5 mins...
Is there anything to do???

---

### Post by lilalmond on 2008-04-02
Anyone? :confused:

---

### Post by dstew on 2008-04-02
Try disabling roaming in System --> Administration --> Networking. If that doesn't work, you might have to try a new driver.

---

### Post by lilalmond on 2008-04-02
Thank you so much dstew!!!
I disabled roaming and  so far i didnt get disconnected for the last 30 mins :)
I tested it out by playing a tourney on pokerstars, worked out perfectly!!!
Dont wanna jinx it tho  ;)
You rock  :guitar:

---

### Post by bluemarble on 2008-04-02
I have a virgin broadband dongle and have tried turn off roaming but the USB modem is not recognised by the computer at all. I asked Virgin tech support and they said 

''Unfortunately, there is no support for Linux. We have not developed a driver for the OS and there is currently no plan to do so in the immediate future.''

 but there must be something out there?!?!?!

any ideas?

---

### Post by dstew on 2008-04-02
Bluemarble, your problem is different than that of the original poster on this thread. Would you mind starting a new thread for your problem? This helps when people search for solutions that are specific for their hardware. When you start the new thread, include in your starting post the output of the command```
lsusb
```That will tell us more exactly what your hardware is. Thanks.

---

