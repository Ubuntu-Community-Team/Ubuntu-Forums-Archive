---
title: "ip"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by trav9595 on 2014-02-16
xubu  with xfce
how can you change your ip address if you are running thru a small router...are there `any easy to use apps for that???

---

### Post by ian-weisser on 2014-02-17
Easy-to-use-apps? The terminal and Network Manager are very easy already. 
Why do you want to do that?

You can change your IP address using the router configuration webpage, if you have the router's password. That requires no changes to your system beyond releasing and requiring the address from the router.

You can change your IP address on your system by setting a static IP address using either Network Manager or the terminal. That works with many routers, but not all.

---

### Post by Bucky Ball on 2014-02-17
You don't need an app (as suggested by ian-w). Right click the network icon>Edit Connections>Wireless (or Wifi)>choose your router>Edit>IPv4 settings>Method = Manual.

Then you simply fill in the details you want and set the static IP address you want. You need to check on the router that it is not serving DHCP addresses in the same range as you set your static IP address in Network Manager. 

Very important your router is not serving addresses in the range of the static IP. If you have, for instance, 192.618.0.12 set as the static IP on your machine you do not want the router serving in the range 192.168.0.0-999. With me?

---

