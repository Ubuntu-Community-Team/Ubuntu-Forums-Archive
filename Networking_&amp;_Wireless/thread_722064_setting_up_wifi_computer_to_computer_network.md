---
title: "setting up wifi computer to computer network"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by drunkmatador on 2008-03-12
I'm on a network where I can only have a limited number of MAC addresses configured to work with the wifi. It's at an apartment building so I share this connection with 20-30 other people.

Since I can't have my laptop set up to connect to the network, I'd like to configure it to connect to my desktop computer, which is connected to the wireless connection. It seems like this would be possible but I don't have any idea how it would be done. Any suggestions?

---

### Post by Whiffle on 2008-03-12
You'll need a network card of some sort in both computers and a howto:

[https://help.ubuntu.com/community/InternetConnectionSharing](https://help.ubuntu.com/community/InternetConnectionSharing)

Any questions feel free to ask.

---

### Post by drunkmatador on 2008-03-12
I've got working wireless cards and drivers in both. Just can't connect to this particular network with one computer so I've got to go through the desktop.

Thanks for the link to the howto. I'll let you know if there's any problems.

---

### Post by Whiffle on 2008-03-12
Yeah actually you'll need a second network card of some type in the desktop, since it has to have one to get on the wireless and one to talk to your laptop.

---

### Post by drunkmatador on 2008-03-12
The howto he linked me to says you can just configure wlan0 for internet and wlan0:0 for internal network. Would this not work?

Also I'm connecting these through wireless. Would that be a problem and should I follow any different steps in the howto?

---

### Post by Whiffle on 2008-03-12
Oh, actually yeah I think the wlan0:0 would work.  totally didn't know that was possible actually :D

---

### Post by drunkmatador on 2008-03-12
So would I be able to connect the two computers through wireless? At closer look I don't think this howto would work because the client wouldn't know which ESSID to connect to. How could I go about telling it which one?

---

