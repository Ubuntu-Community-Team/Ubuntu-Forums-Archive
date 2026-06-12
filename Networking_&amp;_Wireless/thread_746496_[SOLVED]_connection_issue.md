---
title: "[SOLVED] connection issue"
date: 2008-04-05
forum: Networking &amp; Wireless
---

### Post by upthelum on 2008-04-05
I use a bt home hub wireless router and can connect no problem now, after a driver workaround. The thing is, when i try to access my uni network i have to manually re-configure the network interface and reboot. These used access points are in my network manager. Can anyone suggest a fix to allow automatic connection to various access points on different networks seamlessly?

Thanks.

---

### Post by spd106 on 2008-04-06
I don't fully understand what you're asking, but you might want to look into editing the essid settings of Network Manager in gconf.

See this web page [http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ](http://live.gnome.org/DarrenAlbers/NetworkManagerFAQ)

Hardy Heron has a separate utility for making this kind of thing much easier.

---

### Post by upthelum on 2008-04-06
What i meant is how do i get my adapter to automatically pick up the available wireless access point without having to change my network interface manually. I installed that network manager with apt-get but as yet cannot find how to start it, it's not in any menu and i don't know the command to run it in terminal.

---

### Post by spd106 on 2008-04-06
Sorry, I just spotted you're KDE user, so my advice about gconf is kinda useless.

I think you want to install the knetworkmanager package.

---

### Post by upthelum on 2008-04-06
Yes thats what i did but how do i run it?

---

### Post by upthelum on 2008-04-08
Got a Wireless Lan Assistant in Synaptic which starts at bootup and lets you choose which network to use. A very simple tool but quite adequate. I'm quite pleased to say i can use Linux for all my day to day needs now and the transition from winblows is getting easier by the day.

= happy bunny

---

