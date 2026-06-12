---
title: "Dropped wireless connection leads to system hang"
date: 2005-10-03
forum: Networking &amp; Wireless
---

### Post by bs_ on 2005-10-03
With the help and information that I've found on these forums, specifically ([https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)](https://wiki.ubuntu.com//Rt2500WirelessCardsHowTo)), I've got my Linksys WUSB54Gv4 wireless USB adapter working with Ubuntu 5.04. I'm currently using the driver provided by RaLink ([http://www.ralinktech.com/supp-1.htm](http://www.ralinktech.com/supp-1.htm)) and I'm successful at connecting to my home networking using WEP.

My problem lies in managing the interface.  Whenever I do a "ifconfig rausb0 down" the system chugs along a little and then eventually hangs.  Also related to this is that when I use the GUI interface to configure my wireless network, I cannot commit the changes. Attempting to close the UI to commit the changes results in a system hang.

My wireless signal goes up and down and when I lose my connection, the only way I've been able to re-establish it (on Windows at least) is by recycling the interface. Since I can't bring down the wireless interface reliabliy, I'm not making the most of my wireless network.

Any ideas on how I can debug this issue? What logs can I investigate or what tracing steps should I take? 

Also, I witness the same behavior when I use the serialmonkey drivers ([http://rt2x00.serialmonkey.com/wiki/index.php)](http://rt2x00.serialmonkey.com/wiki/index.php)).

Thanks for the help!
-b

---

### Post by Zotova on 2005-10-03
Have you tried using the raconfig utility to connect? I find that a lot more reliable than the built in gnome/ubuntu one.

---

### Post by bs_ on 2005-10-03
I haven't used the Raconfig utility but I assume that it's just making calls to the underlying wireless tools package? So I thought I'd cut out the middle man and use the wireless tools directly. Right now, the only commands that I've needed are:

```
iwconfig essid
iwconfig enc
```

I'm not on my linux box right now so I'll have to give Raconfig a try when I get home later.

---

### Post by bs_ on 2005-10-03
No luck with Raconfig, I get a hang using this config utility as well.

Any ideas on where I can look on my system for some debugging information? A system log somewhere? A debug flag somewhere that I'm missing?

---

