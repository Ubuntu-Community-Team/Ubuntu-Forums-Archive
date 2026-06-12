---
title: "How to set my IP address?"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by Agent ME on 2008-09-29
My laptop with Ubuntu 8.04 always uses the IP of 192.168.1.111 on whatever wireless network I'm on. (Haven't tried a wired network.) This is ok, but I'm curious as to where I can set this for if I need to change it in the future, or how to change it to DHCP.

Under System > Administration > Network, Connections tab, under properties of Wireless and Wired Connections, the "Roaming" checkbox is checked, and all the other settings under that are blank+greyed out, so I assume this isn't what's setting my IP and network.

---

### Post by pytheas22 on 2008-09-30
If you're always being assigned the same IP address, it's probably your router that's doing it.  Unless you're using static IP (which you're most likely not), Ubuntu doesn't have any say in which IP address you get assigned; it just asks the router for an IP and the router responds with whichever address it decides to give.  You can configure most routers to always assign the same IP to certain computers on the network, so I'd suspect that that's what's going on.  To see your router's configuration, open up Firefox, type '192.168.1.1' in the address bar, and you should see the configuration page (if you're asked for a password and username, the defaults should be printed on the outside of your router).  If you get a page-not-found error, try going to 192.168.0.1 instead, or if that fails, 10.0.0.1.

If you do use static IP, you can set it by going to System>Administration>Network, unlocking the utility by entering your password, clicking the "Propreties" button, unchecking "Roaming mode," selecting "Static IP" in the "Configuration" field, and then entering your IP, subnet and gateway as appropriate.  If you don't use static IP, leave roaming mode enabled, or you might break your Internet connection.  If you don't know what static IP is, then you most likely don't use it (very few people use it at home anyway).

---

### Post by Agent ME on 2008-09-30
Doubt its the router as I've gotten the same IP on two different networks I've tried. Plus the DHCP on both started at ...1.100.
I'm curious as to what the "roaming mode" is exactly.

---

### Post by pytheas22 on 2008-10-01
As far as I know, there's really no way that Ubuntu can have any control over which IP you get, if you're using dynamic IP.

Roaming mode just means, I think, that your computer is configured to connect to whichever wireless network happens to be available, and can move from network to network as the computer moves around.  With roaming mode disabled, you have your computer configured to connect to only one particular network; if you change locations and need to connect to a different one, you'd need to enter the settings explicitly for that network.

---

### Post by Iowan on 2008-10-01
**/etc/dhcp3/dhclient.conf** has a **fixed address** under "alias", and **might** be able to request a specific address (though I don't see option in **man dhclient.conf).** Seems unlikely, though...

---

