---
title: "Problems with the wireless connection. Message: disconnected - you are now offline"
date: 2016-03-23
forum: Networking &amp; Wireless
---

### Post by diki_saki on 2016-03-23
Hey friends

Firstly,  I'm active here in the Forum so i will answer your replies after only a short moment. 
I've searched up this problem for a long time now, and  I'm becoming nervous. I don't know quite what happened and why it  happened. When I start the computer, I get the message "disconnected -  you are now offline" and no signal about wireless connections come up on  the top right bar. When I touch the wireless spot, it says "Ethernet  Network disconnected".

I would gladly provide you with extra information, and offcourse if anyone suggest any script, I would post the outcome here.

Recently it worked, but I thought of sparing  some batterytime and shut off the bluetooth. The wifi stopped working. I  rebooted and turned the bluetooth on again, but still no signal. I've  even tried to reinstall the whole Ubuntu-distro for a third time now with  no luck. Still no internet connection.
If the internet is going to  work with the cable inserted, this is not my case. No internetconnection  even with the cable inserted...

I would be extremely happy if you could help me. I've seen some of your answers on the Forum, but nothing has helped me.

---

### Post by praseodym on 2016-03-25
Please open a terminal and show the outputs of these commands:
```

uname -a
lspci -nnk
lsusb
ifconfig -a
iwconfig
rfkill list
```

---

### Post by diki_saki on 2016-03-25
I recently solved the problem. The problem was in the bios-settings. I don't know how the wlan button was not checked in the bios-settings.

thnx for the fast answer. appreciate it.

---

### Post by Bucky Ball on 2016-03-25
Please see the first link in my signature at the bottom of my post and mark thread solved. Thanks.

---

