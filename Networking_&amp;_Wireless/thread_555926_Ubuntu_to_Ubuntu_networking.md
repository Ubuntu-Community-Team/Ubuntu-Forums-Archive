---
title: "Ubuntu to Ubuntu networking"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by edward4130 on 2007-09-20
I have two machines running Feisty, one of them I am intending to be a kind of household server but not running as a server it is Myth/ubuntu.  now setting up a PC with ubuntu/wine to play games and do the day to day stuff... I want to connect to the mediacenter one and it can see it but it will not share the stuff I ask it to..

What is up?

I searched everywhere and I can't find anything on this Local networking, sharing ubuntu to ubuntu.

Edward 4130

---

### Post by louieb on 2007-09-20
Linux to Linux is pretty easy. 
1st set up both machines to have a static IP. I do mine through my router setup. And just let the PC's use DHCP.
2nd install openssh-server on both pcs
3rd places > coneect to server > service type **ssh**  in the server box put the other machines ip address. And give the connection a name. Your done. 
Now the other pc will be just another place on the places menu.

---

