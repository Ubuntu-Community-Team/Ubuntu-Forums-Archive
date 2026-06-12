---
title: "Free beer for anyone who can answer my ethernet question!"
date: 2006-08-29
forum: Networking &amp; Wireless
---

### Post by drews_blunted on 2006-08-29
i have a hp pavillion labtop it has a built in ethernet card. It was working fine at my friends home. He has DSL internet and the labtop was connected to that service and worked great! i now have the labtop at my house and hoooked up to my cable modem. For somereason i cannot use the internet now. it says its connected, im assuming only to a LAN. But the internet will not work at all. my question is i do not think ubuntu specificly has a problem, but i could be wrong. But i think my labtops bios or onboard ethernet is still configured for the last internet connection. when the computer is booting is say something about mac address. and it seems to be trying to find out the dHCP info. but it fails and then ubuntu boots. I think because of this the internet will not work. and i cannot find a way to erase the mac address from the labtops bios.

Any help or ideas would be VERY helpfull :cool:

---

### Post by NetworkGuy on 2006-08-29
Did you reboot your modem?  You should reboot your cable modem everytime you change what it is connected to.

---

### Post by drews_blunted on 2006-08-29
I did some more research into what the DHCP / Mac address booting thing was at boot.  It said it was something called:

Argon PXE Boot Agent

Argon Technology's Client-based firmware streamlines networked desktop management. It enables client PCs, notebooks, servers and network devices to access and boot from server-based boot image files. And used with our Management Software or your favourite third party management application, Argon's Client Boot Agent technology allows you to:

    * ensure consistent client management standards are maintained
    * improve overall efficiency, and
    * create an easily maintained computing environment for users. 

i kept looking and i found something called:

Etherboot Boot Roms

Im not sure if this is something i need or not.

[http://www.argontechnology.com/products.aspx?id=65](http://www.argontechnology.com/products.aspx?id=65)

[http://www.argontechnology.com/](http://www.argontechnology.com/)

Anyone sudgestions or ideas? :)

---

### Post by tturrisi on 2006-08-29
Your bios has NOTHING at all tgo do with dhcp or whether or not you can connect to the Internet.  The ONLY this a biso can affect network-wise is ability to boot from the network, usually a "yes or no" choise in bios section called Boot Order or Boot Priority, which means which devices the bios should look to boot from in a particular order.

That's what your second post above refers to, network boot.

Power your modem off & back on.

---

