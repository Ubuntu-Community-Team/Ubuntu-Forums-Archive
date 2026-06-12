---
title: "Bridging with Atheros cards"
date: 2008-07-06
forum: Networking &amp; Wireless
---

### Post by Omnutia on 2008-07-06
I want to bridge a network between wired and wireless on a home server I am making and I've tried everything but still, I'm not getting anywhere.
I have tried using a /etc/network/interfaces file I found [here]("https://help.ubuntu.com/community/BridgingNetworkInterfaces") and modified, but it doesn't work and, when I use it and restart the computer, *iwconfig* says ath0 doesn't exist.
When I try rewriting the interfaces file while running and then restarting using "/etc/init.d/networking restart" I am told it couldn't create the device.

The most success I have had was when I entered the commands into the terminal manually. I was able to destroy the device and then create the new one, in accordance with [this guide]("http://www.linux.com/articles/55617"), and I was able to see the created access point with my laptop but when I tried using firefox on the server I couldn't connect to anything, leading me to think this something to do with the IP configuration.

Ok, questions:
1) Why would the "pre-up <command>" not work from the interfaces file but the same commands work from the terminal once logged in?
2) When you create a bridge, does it override the IP configuration of it's components?
3) As I could see the access point created by the wireless card and "brctl show" showed both eth0 and ath0 can I assume the two devices were bridged?
3b) How would I then set the IP options to make the bridged device connect to the network?

---

### Post by kevdog on 2008-07-06
What's the purpose of your bridge?? -- To do internet connection sharing?

---

### Post by Omnutia on 2008-07-06
Yes, eth0 is currently connected to the wired router and I want to share that connection with the wireless card in AP mode so I can connect with my laptop and use my it around the house.

---

### Post by kevdog on 2008-07-07
Possibly this will help -- hopefully the atheros card is on the wired computer.
[https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)

Key words
internet connection sharing
ad-hoc
madwifi monitor mode

also take a look at this:
[http://madwifi.org/wiki/UserDocs/SimpleAccessPoint](http://madwifi.org/wiki/UserDocs/SimpleAccessPoint)
That tutorial suggests bridging, however it would seem to me routing of ICS would be a better choice.  What I would suggest is to get the AP up and running and make sure you can connect to the AP from the client.  If this is successful then we will work on the bridging/routing solution later.

---

