---
title: "Network Monitor Panel add-on question."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by adventure man on 2009-05-05
Hey guys I added "Network Monitor" to the top panel in my Xubuntu 9.  I just have one problem, what do I need to put in the "Network Device" space in edit properties?

Here is a screen:
[IMG]http://i242.photobucket.com/albums/ff89/quasimodo69/Screenshot3.png[/IMG]


Thanks:):KS

---

### Post by Kobalt on 2009-05-05
You need to put in the device label to display, for instance *eth0* if you want to monitor your ethernet connection, etc. Which way do you connect to the internet? I see a wifi graph in your screenshot from NetworkManager : you'll find the device label with which you connect to the internet from there.

---

### Post by kanikilu on 2009-05-05
For my wired ethernet adapter, it's "eth0", yours might be different, though, depending on what you want to monitor.

The easiest way to get the device names is to open a terminal and type **ifconfig**. The device names will be on the left, for example, eth0, lo, and so on.

// Edit - Too slow ;)

---

### Post by Hospadar on 2009-05-05
it's probably something like "eth0"

It depends on what hardware you are using, if you open up a terminal and type "ifconfig" it will spit out a bunch of info about your connection.  On the left you'll see the connection names.

you might see names like "lo" (the loopback interface used to communicate between processes), eth0, eth0, wlan0, ath1, ra1, etc, etc.  lo is not the one you're looking for, its probably eth0 or wlan0.  The interface that's actually connected will have a "inet addr" followed by a typical ip address, that's the one you want.  and if you arn't sure, there arn't that many, you can always try them all.

---

### Post by adventure man on 2009-05-05
thanks so much for the help guys.  I right clicked the wireless graph and under "connection information", like kobalt mentioned and it showed "802.11 wifi (ath0)" as interface.  Plugged that ath0 into network device and it works now.  Thanks!!:KS

---

