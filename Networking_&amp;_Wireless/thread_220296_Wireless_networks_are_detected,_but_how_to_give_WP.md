---
title: "Wireless networks are detected, but how to give WPA2 key"
date: 2006-07-21
forum: Networking &amp; Wireless
---

### Post by GoldWing on 2006-07-21
I have a very large wpa2 key to enter from my acer laptop to enter the network via a 3com wireless router.
I can see 2 networks on eth1, but I can't access any.
How do I do that ? I think I have to install something additional, but what ? This ndiswrapper ?

---

### Post by wieman01 on 2006-07-21
You could try this. Perhaps it even works without ndiswrapper:

[http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn]("http://www.ubuntuforums.org/showthread.php?t=202834&highlight=wpa2+rsn")

Good luck! Let me know if you need more help.

---

### Post by GoldWing on 2006-07-21
found this howto, I will try this first:

[http://ubuntuforums.org/showthread.php?t=125150&page=2&highlight=wpa](http://ubuntuforums.org/showthread.php?t=125150&page=2&highlight=wpa)

---

### Post by wieman01 on 2006-07-21
Absolutely. NetworkManager is a good tool if you don't need static IP. It works well for DHCP.

---

### Post by it.henrik on 2006-07-21
NetworkManager is cool as long as you do not use hidden essid... :/

---

### Post by wieman01 on 2006-07-21
> **it.henrik said:**
> NetworkManager is cool as long as you do not use hidden essid... :/

Also, yes. Actually it has quite a couple of restrictions, but within these constraints it's the perfect tool. I hope they are going to enhance it in future for one day this tool (and the GUI) may do away with all our problems relating to wireless networking.

---

### Post by GoldWing on 2006-07-24
Just an update to say the the network manager solved the issue. I am now secure wifi connected !
Now let's confgiure my network printer.

---

### Post by wieman01 on 2006-07-24
> **GoldWing said:**
> Just an update to say the the network manager solved the issue. I am now secure wifi connected !
Now let's confgiure my network printer.

Use CUPS for the network printing. It's fairly straight-forward and I am using it for my own network back home. Give it a try and let us know if you face problems.

---

