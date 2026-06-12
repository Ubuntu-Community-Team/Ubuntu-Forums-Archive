---
title: "Strange error Wifi Ubuntu 8.10"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by Tralapo on 2008-11-01
Hello,

I've got an Dell XPS M1530 with a *"Intel Corporation PRO/Wireless 4965 AG or AGN"* network card.

Today I installed my first Linux, and I took Ubuntu 8.10.
But there is something strange happening. I can connect to unsecured wireless networks, but not to secured, both are coming from the same router ([www.fon.com](www.fon.com)).
When I try to connect to our secured wireless network, I've to fill in our Network key, so I do.

Then he starts to connect, but there is nothing happening, en than, he askes again for the network key (which is already filled in in that window), so I type it again, and he does the same.

He connects to unsecured wireless networks with no problems, but secured doesn't work. 

Does anyone knows what's the problem and how I can solve it?


[SIZE="2"]*I'm sorry for my bad English*[/SIZE]

---

### Post by Roci on 2008-11-05
I have the same WiFi card, and I've never had any problems with connecting to secured networks. Can you describe the problem in more detail? For example, is the network secured with WEP or WPA?

Also, congrats for your first Linux. :)

---

### Post by devauda on 2008-11-05
I upgraded from hardy to ibex and my intel 3945 card can't connect to a wep protected network. I can only connect to open wifi networks.

---

### Post by devauda on 2008-11-06
I installed wicd this morning and i can use all my network connections (wired and wifi) with and without wep.

Add the repos for intrepid:

    deb [http://apt.wicd.net](http://apt.wicd.net) intrepid extras 

You'll also need to add the key used for signing Wicd by running the following command in a terminal:

    wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add - 

Hope it help

---

