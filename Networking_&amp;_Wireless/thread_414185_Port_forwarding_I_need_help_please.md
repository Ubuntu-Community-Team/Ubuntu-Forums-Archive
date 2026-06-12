---
title: "Port forwarding?? I need help please"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by all4spl on 2007-04-19
OK i'm a complete noob when it comes to linux.. i just installed it a couple of days ago and i need some how... My internet goes like this... comes from a router, goes to my linux eth0 with cat5.. comes out of my linux eth1 with a crossover.. and then into my vista computer... How would my make my vista computer dmz?? like so i wont have any port issues??? please be very specific with commands because im not quite grasping the concept of command based os's yet.... Thanks a bunch and have a great day.

---

### Post by GTvulse on 2007-04-20
The short answer: buy a swtich, program the DMZ in the router and let your Vista machine be 0wn3d in 1 sec flat.

Or, install bridge-utils, read the [Linux Advanced Routing and Traffic Control How-To]("http://lartc.org/"), set up the DMZ in the router and let your Vista machine be 0wn3d in 1 sec flat.

Or buy a switch (always a good idea) and learn [how to open ports in your router]("http://portforward.com/").

---

### Post by Mb0742 on 2007-04-20
You shouldn't need to touch linux go into Vista use ipconfig to get your computer ip on the server. Then use ipconfig /all to find your defult gateway then type that into IE / FF etc. and then you can play directly with your router's settings, in the router. 

Guessing you are using a d1-524, then you can just type 192.168.0.1 in Ie etc. ;)

---

