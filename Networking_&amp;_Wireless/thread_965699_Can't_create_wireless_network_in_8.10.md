---
title: "Can't create wireless network in 8.10"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by wildman4god on 2008-10-31
I have ubuntu 8.10 installed on a dell Latitude D600 and I can't create a wireless network, I can connect to other networks fine, but when I try to make my own network so others can come and connect (For an open arena lan party) It tries to connect but it just gives me a disconnected message, I was able to make a network fine in previous versions. I noticed that the network manager is a lot different in 8.10 so for the sake of "ease of use for the normal user" did they do away with this feature or is this indeed a bug?

---

### Post by river2884 on 2008-10-31
network is horrible, horrible in this distribution.
do not upgrade if you use internet!

---

### Post by wildman4god on 2008-10-31
Actually not being able to create networks is my only problem, everything else works fine, I have used the internet, installed programs via repositories, downloaded large video file and more and I never new there was a problem untill I tried to make my own wlan network.

---

### Post by wildman4god on 2008-10-31
Also would it help if I posted the syslog from when it tries to create a network.

---

### Post by wildman4god on 2008-11-01
Hellooooooooooooo.....
Anybody there?
echo...echo...

---

### Post by prematurebaby on 2008-11-01
I'm having troubles with connecting to a network wirelessly since the upgrade all that works is to hard wire it. To create a network however you would do that from your router.

---

### Post by wildman4god on 2008-11-02
Then what is the create network option for? and in previous versions of ubuntu I was able to have my laptop act as an access point so we could have a lan party with out a router, I have done it before so why can't I do it now?

---

### Post by Alex Merveille on 2009-01-23
I have the exact same problem (can't create network, everything else works great) with an eeepc 901 using easypeasy (ubuntu eee 8.10). Any help greatly appreciated, since this defeats the purpose of having the new NetworkManager for me.

---

### Post by Alex Merveille on 2009-01-25
Fixed it.

Installed dnsmasq-base package and repaced minipci card from azurewave to intel. It's not perfect (get 0% reception on the applet all the time), but it works.

Hope this helps someone.

---

