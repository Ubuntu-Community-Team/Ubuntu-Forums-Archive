---
title: "wired network question"
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by O-pos on 2007-07-11
Hello,

I have wired network at my office and the guys there configured my lap's networking as fixed wired connection. they entered the ip address and subnet masks and etc.. and it works ok. 

But friend of mine has a DSL cable at home and his PC doesn't work. I would like to connect my lap to this dsl cable, but the autodetect system doesn't work and I also tried dhclient and it also can't help. it thinks lot and then gives negative output. I don't know the IP and other parameters to enter. what can be done in this regard to connect to internet?

---

### Post by checho on 2007-07-11
Try in console "dig www.google.com". It is a command that traces the packages through internet. It will gives you valuable information like at which point you are having problems. For example, if the DNS server is miss configured it might give you the DNS correct configuration. Also remember that when working with fixed ip connections is recommendable (or necessarily) to have a network configuration per network because it may save the configuration( ip address, DNS server, etc.) in cache. For example even if you  did dhclient and asked for a new ip address, you still have other information might that miss match. To make a new account use the wizard in "Start">System>Administration>Configure network
Make a new profile and save it. Remember to select the correspondent configuration when connecting to the proper network. If still having problems post what you got with dig and with ifconfig.

---

