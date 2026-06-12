---
title: "Help needed with 2nd WEP key in Network Manager"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by meglamaniac on 2007-05-02
Hi guys - thanks in advance for any help.
I'm running 7.04 with an Atheros wi-fi card.

Ok, my situation is that the wireless network I need to connect to requires me to use the ***second*** key index. Here is how I've got it running on the command line:

```

sudo ifconfig ath0 down
sudo iwconfig ath0 essid <my network name>
sudo iwconfig ath0 ap <my access point's mac address>
sudo iwconfig ath0 key [2] <my WEP key>
sudo iwconfig ath0 key [2]
sudo iwconfig ath0 key open
sudo iwconfig ath0 key on
sudo ifconfig ath0 up
sudo dhclient ath0
ping www.google.com (pings are returned)

```

The problems with this are:
 - it took me 3 hours to figure out
 - i don't know how to connect without first knowing the mac address of the AP i'm trying to connect to
 - probably the biggest problem, the connection drops after about 10 seconds unless I keep it alive by pinging somewhere

What I need to be able to do:
 - Get network manager to accept a key for index 2 **and then use it!**

I'm stuck on this part.
Both the Microsoft wi-fi manager and the custom Win32  wi-fi manager supplied with my Proxim (atheros) PCMCIA card have an option for keys 1 - 4.
Network manager doesn't, that I can see.

**I cannot connect to the network without being able to use the second key index.**

Is this impossible to do?


Sorry for all the bolding but I've asked in a few places so far and people keep ignoring the all important second index bit.

---

### Post by meglamaniac on 2007-05-03
*bump*

Please guys, I couuld really use some advice on this!

---

### Post by hfdragon on 2007-08-09
I have this exact same problem... did anyone manage to connect with the 2nd wep key with networkmanager ?

---

### Post by meglamaniac on 2007-08-09
In the end the only way I found to make it work was to remove network-manager using synaptic and just configure it manually as I described in the first post.

I think NM simply doesn't support any WEP key other than 1 at the moment.

---

### Post by hfdragon on 2007-08-09
Thanks for your reply.

Anyway, I managed to configure this manually without removing network manager  (I still need it for the other places I go).

Maybe I will fill this as a bug in network manager bug tracker and keep you advised here if there is any developpements.

---

### Post by hfdragon on 2007-08-10
I filled a bug on gnome bugzilla to add this feature request :

[http://bugzilla.gnome.org/show_bug.cgi?id=465543](http://bugzilla.gnome.org/show_bug.cgi?id=465543)

---

