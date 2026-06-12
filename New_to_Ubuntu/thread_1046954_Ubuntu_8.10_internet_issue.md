---
title: "Ubuntu 8.10 internet issue"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by bharath-v on 2009-01-21
Hello everyone,
       I received a copy of Ubuntu 8.10 which i requested in the ubuntu site.i have 2 hard disks and both have separate xp's installed. i installed ubuntu 8.10 on the secondary hard disk. installation went fine but its not detecting the internet at all.
when clicked on the 2comp icons it said some restricted drivers needed to be installed.it was some ATI one and its was not able to install either from cd or the net(coz net is not detected).but my internet works fine in Xp.

one more thing when i shutdown and start Xp the time will be changed.

Please help and thank u

---

### Post by Iowan on 2009-01-21
How do you connect - wired/wireless? 
Do you have static IP Address or DHCP server?

The time may be a function of which timezone you have selected.

---

### Post by emarkd on 2009-01-21
Also, what brand and model network interface card do you have?

---

### Post by bharath-v on 2009-04-01
thanks for the reply
i m connection is wired.
And Ip is DHCP not static

---

### Post by alphacrucis2 on 2009-04-01
> **bharath-v said:**
> thanks for the reply
i m connection is wired.
And Ip is DHCP not static

8.10 has an applet called network manager. An icon for it should be on the status bar at the top right. You can right click on it and first check that the networking is enabled. Click edit Connections and you should see eth0 under the wired tab. The default setting under IPV4 should be Automatic (DHCP). 

Also Under Applications/Accessories/Terminal type:

```
ifconfig
```

Can you see if an ip address has been assigned to eth0?

If not there may be an issue with Ubuntu recognising your ethernet card.

---

### Post by bharath-v on 2009-04-02
I think the ethernet card is not accepted.but previously it had no problems.
how to install  ethernet driver.

---

