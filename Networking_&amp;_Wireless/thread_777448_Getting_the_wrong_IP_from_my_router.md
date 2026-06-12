---
title: "Getting the wrong IP from my router"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Pipette Monkey on 2008-05-01
Hello,
    I have my computer hooked up to a D-link router.  The router always assigns the computer the IP 192.168.1.2, however, whenever I restart my computer, the computer thinks its IP is 192.168.1.3.  I noticed that this was going on in Gutsy, but it didn't effect anything so I didn't care, but since updating to Hardy, this makes it so that I can't connect to the internet without first running "sudo ifconfig eth0 192.168.1.2"  How can I get DHCP to give me the right address on startup, or should I just add ifconfig eth0 192.168.1.2 to my rc.local?

Thanks

---

### Post by superprash2003 on 2008-05-01
you can set it right in network manager(system->administration->network).. if you prefer DHCP then just select DHCP

---

### Post by Iowan on 2008-05-02
I'm curious why 192.168.1.2 is "right" (or why 192.168.1.3 is wrong - especially if that's what the DHCP server (router) issued.

---

### Post by Pipette Monkey on 2008-05-02
Well,  if I go to my router's control page and look at the attached devices screen, it will show the computer's hostname listed as 192.168.1.2, and at the same time ifconfig eth0 says 192.168.1.3.  I can ping the computer from another on the network at either 2 or 3.  For some reason this causes the computer to only be able to access the local network since the Hardy update, whereas it didn't effect internet access before.
I've since changed the network settings to a static IP of 192.168.1.2 and everything's fine now.

---

