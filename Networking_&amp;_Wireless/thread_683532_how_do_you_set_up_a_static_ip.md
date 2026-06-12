---
title: "how do you set up a static ip?"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by the12cook on 2008-01-31
how do you set up a static ip whenever i try i end up with no connection! please could someone either walk me through it or direct me to a tutorial thanx very much in advance!

---

### Post by lungdart on 2008-01-31
Simplest way I can think of is to use gnomes network tool under System->Administration->Network

Choose the interface your using (wireless card, wired card, modem, etc.) and click properties. This will bring up a new window. In this window, make sure the enable this connection is checked (It already should be). In the drop down list labeled configuration, choose Static IP.

Under this it will ask for some basic information you want to use.

IP address: The IP you want your interface set to. Try to choose something out of your routers DHCP range, for instance, if your router gives 192.168.0.10-192.168.0.50 pick something like 192.168.0.120.

Subnet mask: This will most likely auto fill with 255.255.255.0, this is fine for 99% of home networks.

Gateway: This is your routers IP address. Also make sure your IP address has the same first three values (If your routers address is 10.0.1.50 your ip address must be 10.0.1.X, where X is any number outside that routers DHCP range to avoid any conflicts that may arise.)

Click OK, a scrolling bar should come up indicating its changing your netowrk configuration and tada, your set to static. Enjoy!

---

### Post by jan quark on 2008-01-31
here my static ip configuration
screenshot one

you have to change the addresses accordingly to your router settings
I have a fritz.box router. there I had to assign a static Ip for my pc and laptop
see second screenshot

---

