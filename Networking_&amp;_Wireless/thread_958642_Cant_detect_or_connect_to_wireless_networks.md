---
title: "Cant detect or connect to wireless networks"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by ecko19 on 2008-10-25
I have just installed ubuntu server edition and install i believe gnome.  I am trying to connect to my wireless network but keep failing.  I have the broadcom BCM4306 card.  I detects the card and all, although in network settings once I set the settings for my wireless network it wont connect.  Even if I put the roaming setting it wont detect and networks around me and I know that there are many.  

After that I tried to install the windows wireless driver thinking that something was wrong.  I successfully installed it but its still acting the same way.

Can someone help me or give me some ideas?

---

### Post by melojo on 2008-10-25
double posted

---

### Post by melojo on 2008-10-25
lets do this first and post the output

open a terminal and type
```
 iwlist <network interface> scan
```

type ```
ifconfig
```

to get your wireles interface

this will list all wireless networks in range.

---

### Post by ecko19 on 2008-10-25
When I type ifconfig it doesnt show the wireless:  It shows the ethernet and the local loopback. 

When I do iwlist wlan0 scanning it doesnt have any results

---

### Post by melojo on 2008-10-25
It sounds like the card is not recognized correctly.
Goto
System -> Administration -> Hardware Drivers

does it show any if so check the box and see if it enables your card.

---

### Post by melojo on 2008-10-25
If no drivers listed type this in a terminal.
```
sudo apt-get install b43-fwcutter
```

Look here
[http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/](http://www.foogazi.com/2008/04/28/how-to-enable-bcm43xx-in-ubuntu-804/)

---

### Post by ecko19 on 2008-10-25
I installed the firmware and was able to connect to my network....Thanks!!!

---

### Post by ecko19 on 2008-10-25
When I restarted the computer it reverted back to the same thing?  Did I miss something?

---

### Post by ecko19 on 2008-10-25
I was able to figure that out but now it seems like I lose the connection multiple times.  It continues to ask for my password and it loses all bars.

---

