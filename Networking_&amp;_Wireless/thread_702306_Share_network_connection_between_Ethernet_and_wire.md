---
title: "Share network connection between Ethernet and wireless adapter"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by 13warrior on 2008-02-20
Hi,

I have a laptop that has a ethernet port and wirelss adapter. I want to share the network connection with the wireless adapter so that I can create a adhoc network to connect my iphone . 

I have done this in Windows using something called device-device sharing or sort. Is this possible in ubuntu ?

---

### Post by SpaceTeddy on 2008-02-20
yes, it is... BUT it is a bit... complicated :(

there are two ways of doing this...
1.) create a bridge between the two network card, make them work as one and thereby forward anything through your laptop.
**Pro:** a little easier setup, less to understand about network archtiecture.
**Con:** this will render network manager useless, you will have to confgure your network card  manually with iwconfig

2.) make your laptop a router which provides a subnet on it's wifi for other devices...
**Pro:**you don't need to change anything in your system itself, just enable a few things
**Con:**understanding of networks is required, you will also need a dhcp-server in your machine to supply the iphone with an ip address.

i personally always prefer the second option, since it messes less with the system. 
If you still want to do this, then tell me which of the options you prefer and i will try to tell you the basic setup or point you in the right direction with a few tutorials. :)

---

